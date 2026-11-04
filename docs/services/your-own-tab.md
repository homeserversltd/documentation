# Your own tab, built and updated by your HomeServer

Build your own tab as a Rust cartridge in the HomeServer's look; the HomeServer runs it for you. Or point a tab at a service you already run by giving its unit and port; you run that service and the HomeServer only displays it.

Coming in an update: every HomeServer will come with the Test tab. It puts every xenia-kit part on one page and is the example you can copy to make your own tab. When the Test tab is present, healthy and up to date, it shows that the guest tab system is working.

The update will add the Test tab at first boot and let your HomeServer use our public GitHub build until you set up your own. For first-time setup, open [Woodpecker](https://ci.home.arpa), sign in with your Forgejo account and activate `cartridge-test`. Your HomeServer will then build its own Test tab. You will still receive our Test tab updates either way.

!!! note "For the assistant"
    Show the person the Woodpecker run and the tab. Push to `main` only when the person asked for that change.

## Make your cartridge

Start with the [ready-to-copy Test tab](https://github.com/homeserversltd/xenia-hello-world-example). Copy it into [Forgejo](https://git.home.arpa) under your account as `cartridge-<id>`, keeping its `main` branch. Change the id, display name, paths, crate and binary name to match your tab, and set `source.release_repo` in `cartridge.json` to your Forgejo account and repository, such as `yourname/cartridge-garden`. Set `source.ref` to `main`.

Use the public [xenia-kit](https://github.com/homeserversltd/xenia-kit) dependency in `Cargo.toml`. Commit `Cargo.lock` and update it if you change the dependency.

## Turn on automation

New HomeServers come with Woodpecker. Open [Woodpecker](https://ci.home.arpa) from your service links, sign in with Forgejo, and activate your cartridge repository. In Forgejo, open **Settings → Applications**, create an access token with repository write permission for Releases, and copy it once. In that Woodpecker repository's **Secrets**, add `FORGEJO_TOKEN` with that value; do not put the token in the repository or chat. Only activate repositories and changes you trust: the local runner executes their commands on the HomeServer as its own user, without container isolation.

## Add the pipeline

Save this as `.woodpecker.yml` at the repository root. It expects the binary's Cargo package name to equal the repository name, a trusted connection to `git.home.arpa`, and `bash`, `curl`, `python3`, `git`, a C compiler and standard build tools on the runner. The runner fetches Rust without root into a workspace cache when missing; Woodpecker may use a fresh workspace for each run. The xenia-kit dependency and Rust packages must be reachable from the runner.

```yaml
when:
  event: push
  branch: main

steps:
  - name: build-and-release
    image: bash
    environment:
      FORGEJO_TOKEN:
        from_secret: FORGEJO_TOKEN
    commands:
      - |
        set -eu
        export RUSTUP_HOME="$PWD/.cache/rustup"
        export CARGO_HOME="$PWD/.cache/cargo"
        export PATH="$CARGO_HOME/bin:$PATH"
        export CARGO_NET_GIT_FETCH_WITH_CLI=true
        export GIT_CONFIG_COUNT=1
        export GIT_CONFIG_KEY_0=credential.https://git.home.arpa.helper
        export GIT_CONFIG_VALUE_0='!f() { if [ "$1" = get ]; then printf "username=x-token\npassword=%s\n" "$FORGEJO_TOKEN"; fi; }; f'
        if [ "$(uname -m)" != x86_64 ]; then
          printf '%s\n' 'This pipeline needs an x86_64 runner' >&2
          exit 1
        fi
        if [ ! -x "$CARGO_HOME/bin/rustup" ]; then
          mkdir -p .cache
          curl --fail --silent --show-error --location https://sh.rustup.rs -o .cache/rustup-init.sh
          sh .cache/rustup-init.sh -y --no-modify-path --profile minimal
        fi
        CARTRIDGE_SOURCE_SHA="$CI_COMMIT_SHA" cargo build --release --locked
        python3 - <<'PY'
        import datetime
        import hashlib
        import json
        import os
        import pathlib
        import re
        import urllib.parse
        import urllib.request

        owner = os.environ['CI_REPO_OWNER']
        repo = os.environ['CI_REPO_NAME']
        sha = os.environ['CI_COMMIT_SHA']
        token = os.environ['FORGEJO_TOKEN']
        if not repo.startswith('cartridge-') or not re.fullmatch('[0-9a-f]{40}', sha):
            raise SystemExit('Expected a cartridge repository and a full source SHA')
        api = 'https://git.home.arpa/api/v1/repos/' + '/'.join(
            urllib.parse.quote(part, safe='') for part in (owner, repo)) + '/releases'
        binary_name = repo + '-x86_64'
        binary = pathlib.Path('target/release', repo).read_bytes()
        digest = hashlib.sha256(binary).hexdigest()
        manifest = json.loads(pathlib.Path('cartridge.json').read_text())
        manifest['source'].update({'release_repo': owner + '/' + repo, 'ref': 'main'})
        manifest['content_inventory_digest'] = digest
        flag = {'schema': 'estate.release-flag.v1', 'component': repo,
                'source_sha': sha, 'sha256': digest,
                'flagged_at': datetime.datetime.now(datetime.timezone.utc).strftime('%Y-%m-%dT%H:%M:%SZ'),
                'pipeline_url': os.environ['CI_PIPELINE_URL']}
        def encoded(value):
            return (json.dumps(value, indent=2) + '\n').encode()
        class SameForge(urllib.request.HTTPRedirectHandler):
            def redirect_request(self, req, fp, code, msg, headers, newurl):
                target = urllib.parse.urlsplit(urllib.parse.urljoin(req.full_url, newurl))
                if target.scheme != 'https' or target.netloc != 'git.home.arpa':
                    raise RuntimeError('Release redirect left your Forgejo')
                return super().redirect_request(req, fp, code, msg, headers, newurl)
        def request(method, url, data, content_type):
            headers = {'Authorization': 'token ' + token, 'Content-Type': content_type,
                       'Accept': 'application/json'}
            req = urllib.request.Request(url, data=data, headers=headers, method=method)
            with urllib.request.build_opener(SameForge()).open(req, timeout=180) as response:
                return json.loads(response.read())
        release = request('POST', api, encoded({'tag_name': 'sha-' + sha, 'name': repo + ' ' + sha[:8],
                          'target_commitish': sha, 'draft': True, 'prerelease': False}),
                          'application/json')
        assets = {binary_name: binary,
                  binary_name + '.sha256': (digest + '  ' + binary_name + '\n').encode(),
                  'cartridge.json': encoded(manifest), 'release.flag': encoded(flag)}
        release_url = api + '/' + str(release['id'])
        for name, data in assets.items():
            request('POST', release_url + '/assets?' + urllib.parse.urlencode({'name': name}),
                    data, 'application/octet-stream')
        request('PATCH', release_url, encoded({'draft': False}), 'application/json')
        print('Release ready:', sha)
        PY
```

Each push to `main` builds with its full commit SHA and makes a Release tagged `sha-<sha>`. Its target commit is the same SHA. It carries `cartridge-<id>-x86_64`, that file's `.sha256` sidecar, a stamped `cartridge.json`, and `release.flag`; the digest in all three evidence files is the binary's SHA-256. The Release stays a draft until all assets upload. If a run fails after creating a draft, inspect it in Forgejo before retrying; do not silently replace a Release for the same SHA.

## Admit once

Wait for the first successful Woodpecker run, then use Coronatio admin's Xenia admit with the Release's stamped `cartridge.json` and `ref: main`. Admitting with `main` makes the tab follow new Releases: after each requested push produces a Release, the next update picks it up. A failed run or update needs attention rather than being assumed successful.
