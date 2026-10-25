# Thyrsus: commit with your assistant

!!! note "For the assistant"
    1. Run `sudo /usr/local/sbin/agathodaimon/cli.py thyrsus propose <repo path> -m "<what changed>"`.
    2. If `ok` is not true, stop with `firstMissingSignal`.
    3. Show the human `pr_url` when `ok` is true.
    4. Wait for the human to review the proposal in Forgejo.
    5. Use `admit` below only if the human explicitly says this turn to merge this proposal.

## For you

Thyrsus lets your assistant commit changes and open a proposal through Caduceus.
You decide what gets merged. The proposal includes all changes in the repository.

Your starter repository lives on your HomeServer's Forgejo at
[git.home.arpa](https://git.home.arpa). HomeSI uses that same Forgejo, never its own.
Replace `<repo path>` with the repository's local path on the device where the
assistant runs. Replace `<what changed>` with a short description of your changes.

On HomeSI, make a token in your HomeServer's Forgejo under **Settings → Applications**.
Paste it into the HomeSI website field **Your HomeServer's Forgejo token**, not into
chat. To check the connection, run:

```bash
sudo /usr/local/sbin/agathodaimon/cli.py thyrsus forge
```

Read `forge`, `token_present`, and `reachable`. The forge is always `git.home.arpa`.

Open the `pr_url` your assistant shows you. Review the changes, read diffs, add
comments, or close the proposal on that Forgejo web page. You can merge it there.

Only when you explicitly tell the assistant this turn to merge this proposal may
it run the following command. Replace `<pr number>` with that proposal's number.

```bash
sudo /usr/local/sbin/agathodaimon/cli.py thyrsus admit <repo path> <pr number>
```

Read `ok` and `merged_sha`. A successful proposal is not permission to merge.

For Caduceus HTTP calls, `POST /api/v1/thyrsus/propose` takes `repo` and `message`.
Read `ok`, `pr_url`, and `firstMissingSignal`, just as above.
Only with the same explicit instruction to merge this proposal this turn may the
assistant use `POST /api/v1/thyrsus/admit`, with `repo` and `pr`.
Read `ok` and `merged_sha`.
