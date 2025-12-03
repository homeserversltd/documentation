# Contributing to HOMESERVER Documentation

Welcome to the HOMESERVER documentation project! We're thrilled you're interested in helping make our documentation better. Whether you're fixing a typo, clarifying instructions, or adding entirely new guides, your contributions help users worldwide understand and get the most from their HOMESERVER platform.

## Why Documentation Matters

Great documentation is the bridge between powerful technology and empowered users. Every improvement you make helps someone:
- Set up their HOMESERVER successfully
- Troubleshoot an issue independently
- Discover a feature they didn't know existed
- Feel confident managing their digital sovereignty

## How Easy Is It to Contribute?

**Very easy!** If you can edit a text file, you can contribute to this documentation.

- **No complex setup**: Just edit Markdown files
- **No CLA required**: Your contributions are covered under GPL-3.0
- **Quick turnaround**: Documentation improvements are typically reviewed within days
- **All skill levels welcome**: From fixing typos to writing comprehensive guides

## Ways to Contribute

### Quick Fixes (5-10 minutes)

- **Fix typos and grammar**: Spotted a misspelling? Fix it!
- **Update outdated information**: Version numbers, URLs, deprecated features
- **Clarify confusing sections**: If something was unclear to you, improve it for others
- **Add missing links**: Connect related documentation pages

### Medium Contributions (30-60 minutes)

- **Expand existing guides**: Add missing steps, screenshots, or troubleshooting tips
- **Improve organization**: Restructure sections for better flow
- **Add examples**: Real-world scenarios help users understand concepts
- **Create "Common Pitfalls" sections**: Help users avoid mistakes

### Major Contributions (2+ hours)

- **Write new guides**: Document features, services, or workflows
- **Create tutorial series**: Step-by-step learning paths for new users
- **Add troubleshooting sections**: Comprehensive problem-solving guides
- **Translate content**: Help non-English speakers (future feature)

## Getting Started

### The Simple Way (Edit on GitHub)

1. **Find the page** you want to edit on GitHub
2. **Click the pencil icon** (Edit this file)
3. **Make your changes** in the browser editor
4. **Scroll down** and describe what you changed
5. **Click "Propose changes"** to create a pull request

That's it! No git commands, no local setup needed.

### The Developer Way (Local Editing)

If you're making larger changes or want to preview locally:

1. **Fork this repository** on GitHub

2. **Clone your fork**:
   ```bash
   git clone git@github.com:YOUR_USERNAME/documentation.git
   cd documentation
   ```

3. **Install MkDocs** (for local preview):
   ```bash
   pip install mkdocs mkdocs-material
   ```

4. **Start the preview server**:
   ```bash
   mkdocs serve
   ```
   Visit http://localhost:8000 to see your changes live

5. **Make your edits** in the `docs/` directory

6. **Commit and push**:
   ```bash
   git add .
   git commit -m "Brief description of changes"
   git push origin main
   ```

7. **Create a pull request** on GitHub

## Documentation Structure

### Directory Layout

```
docs/
├── index.md                    # Home page
├── setup/                      # Setup guides
│   ├── setup-physical.md      # Hardware setup
│   ├── setup-network.md       # Network configuration
│   ├── setup-admin.md         # Admin access
│   ├── setup-security.md      # Security setup
│   ├── setup-verification.md  # Verification steps
│   └── setup-management.md    # Ongoing management
├── services/                   # Service documentation
│   ├── jellyfin.md
│   ├── vaultwarden.md
│   └── ...
├── developers/                 # Developer docs
├── certificates/               # Certificate management
├── admin/                     # System administration
└── troubleshooting/           # Problem solving
```

### Adding a New Page

1. **Create your Markdown file** in the appropriate `docs/` subdirectory
2. **Write your content** (see Writing Guidelines below)
3. **Add to navigation** by editing `mkdocs.yml`:
   ```yaml
   nav:
     - Section Name:
       - Page Title: path/to/your-file.md
   ```

### Writing Guidelines

#### Content Quality

- **Accuracy first**: Verify all technical information
- **User-centric**: Write for the person trying to accomplish something
- **Clear and concise**: Simple language, short paragraphs
- **Actionable**: Focus on what users can do
- **Complete**: Include prerequisites, steps, and verification

#### Formatting Standards

**Headings:**
```markdown
# Page Title (H1 - one per page)
## Major Section (H2)
### Subsection (H3)
#### Details (H4)
```

**Code blocks:**
```markdown
```bash
command --with-arguments
```
```

**Links:**
```markdown
[Link text](../other-page.md)  # Relative links to other docs
[External](https://example.com)  # External links
```

**Notes and warnings:**
```markdown
!!! note
    This is important information.

!!! warning
    This could cause problems if ignored.

!!! tip
    Here's a helpful suggestion.
```

**Images:**
- Place images in appropriate subdirectories
- Use descriptive filenames: `jellyfin-dashboard-overview.png`
- Include alt text: `![Jellyfin dashboard](images/jellyfin-dashboard.png)`

#### Voice and Tone

- **Direct address**: Use "you" and "your" (not "the user")
- **Active voice**: "Click the button" not "The button should be clicked"
- **Encouraging**: "You can now..." not "The system allows..."
- **Honest about complexity**: Don't oversimplify if something is genuinely complex
- **Respectful**: Assume users are intelligent but may lack specific knowledge

#### Examples

**Good:**
```markdown
## Accessing Jellyfin

1. Open your web browser
2. Navigate to `https://homeserver.local:8096`
3. Log in with the credentials you created during setup
4. You'll see the Jellyfin dashboard

If you see a certificate warning, this is normal for self-signed certificates.
Click "Advanced" and proceed to the site.
```

**Not as good:**
```markdown
## Jellyfin Access

The user must use a web browser to access Jellyfin at the URL. Authentication
is required. Certificate warnings may appear.
```

## Testing Your Documentation

Before submitting, verify:

- [ ] **Accuracy**: All commands, URLs, and instructions are correct
- [ ] **Completeness**: No missing steps that would confuse users
- [ ] **Links work**: Test all links to other pages
- [ ] **Code blocks**: Verify commands are copy-pasteable and work
- [ ] **Formatting**: Preview looks good, no broken Markdown
- [ ] **Spelling**: Run a spell checker

## Commit Message Guidelines

Keep it simple and descriptive:

**Good examples:**
- `Fix typo in Jellyfin setup instructions`
- `Add troubleshooting section for Vaultwarden connection issues`
- `Update certificate renewal guide with new process`
- `Expand setup-physical.md with network diagram`

**Less helpful:**
- `Update docs`
- `Fix stuff`
- `Changes`

If you're making multiple changes, list them:
```
Improve Jellyfin documentation

- Add section on hardware transcoding
- Fix incorrect port number
- Add screenshot of dashboard
- Clarify library setup steps
```

## Pull Request Process

### Submitting Your PR

1. **Fork and make changes** (see Getting Started above)
2. **Create a pull request** with a clear title
3. **Describe what you changed** and why
4. **Wait for review** (typically 1-3 days)

### PR Description Template

Feel free to use this template:

```markdown
## What I Changed
Brief summary of your changes.

## Why
Why are these changes needed? What problem do they solve?

## Testing
- [ ] Previewed locally with mkdocs serve
- [ ] Verified all links work
- [ ] Checked spelling and grammar
- [ ] Tested any commands or procedures
```

### Review Process

1. **Automated checks**: None! Documentation PRs are simple
2. **Maintainer review**: A HOMESERVER maintainer reviews your changes
3. **Feedback**: We may suggest minor improvements
4. **Merge**: Once approved, we'll merge your contribution
5. **Deployment**: Changes are automatically built and distributed to all HOMESERVER devices

### Response Time

We aim to review documentation PRs within **3 days**. Simple fixes (typos, broken links) are often merged within 24 hours.

## Documentation Philosophy

Our documentation follows these principles:

### 1. User-First Always

Every page should answer:
- What is this?
- Why do I care?
- How do I use it?
- What if it doesn't work?

### 2. Assume Intelligence, Not Knowledge

Users are smart but may not know HOMESERVER-specific details. Don't oversimplify, but do explain.

### 3. Show, Don't Just Tell

Examples, screenshots, and step-by-step instructions beat abstract descriptions.

### 4. Keep It Current

Outdated documentation is worse than no documentation. Update as the platform evolves.

### 5. Progressive Disclosure

Start with the essentials, then provide details for those who need them.

## Topics We Need Help With

Looking for ideas? These areas could use attention:

### High Priority
- Troubleshooting guides for common setup issues
- More screenshots and visual guides
- Service-specific optimization tips
- Real-world usage examples

### Medium Priority
- Advanced administration guides
- Performance tuning documentation
- Integration guides for third-party tools
- FAQ sections for each service

### Nice to Have
- Video tutorial scripts (we can record them)
- Comparison guides (HOMESERVER vs. other solutions)
- Use case documentation (home media server, small business, etc.)
- Best practices guides

## Getting Help

### Questions About Contributing?

- **Check existing docs**: Browse the repository for examples
- **Open an issue**: Ask questions using GitHub issues
- **Draft PR**: Start a draft PR and ask for feedback early

### Questions About Content?

- **Test it yourself**: Set up HOMESERVER and verify the process
- **Ask maintainers**: We're happy to help you get details right
- **Flag uncertainty**: If you're not sure about something, mention it in your PR

## Recognition

Documentation contributors are valued members of the HOMESERVER community:

- **Listed in contributors**: Your name in the project contributors list
- **Mentioned in updates**: Significant contributions noted in release announcements
- **Building expertise**: You're helping define best practices
- **Helping thousands**: Your work benefits every HOMESERVER user

## Common Questions

**Q: I found an error but I'm not sure how to fix it. Should I still report it?**  
A: Absolutely! Open an issue describing what's wrong. Someone else may have the knowledge to fix it.

**Q: English isn't my first language. Can I still contribute?**  
A: Yes! We'll help with any language polish needed. Your technical knowledge and user perspective are valuable.

**Q: Can I copy documentation from other projects?**  
A: Only if it's clearly licensed for reuse (like CC-BY or public domain). Always attribute sources.

**Q: I disagree with how something is explained. Should I change it?**  
A: Open an issue first to discuss your concerns. If it's a genuine improvement, we'll support the change.

**Q: How technical should documentation be?**  
A: Match the audience. Setup guides should be accessible, developer docs can be more technical.

## License

All documentation contributions are licensed under **GPL-3.0**. By contributing, you agree that your work can be freely used, modified, and distributed under this license.

No CLA is required for documentation contributions.

---

**Thank you for helping make HOMESERVER documentation better for everyone!**

Every improvement you make helps someone accomplish their goals and take control of their digital life. That's powerful.

*HOMESERVER LLC - Professional Digital Sovereignty Solutions*

