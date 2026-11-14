# Setup instructions for Harsh99-ops GitHub profile

## 1. Upload to the correct repository

Create (or use) a **public** GitHub repository whose exact name is `Harsh99-ops` under the `Harsh99-ops` account. Upload the contents of this folder into the repository root (not inside a second nested folder). Your GitHub profile will then display README.md automatically.

If you already have a `Harsh99-ops` repository, back it up first, then replace/update the relevant files.

## 2. Enable the animated contribution meadow

1. In that repository open **Settings → Actions → General**, and enable GitHub Actions as appropriate for the repository. The workflow's `permissions: contents: write` grants the publishing step write access, subject to your organization/account rules.
2. Visit **Actions → Generate Contribution Meadow → Run workflow**, selecting `main`.
3. Wait for the run to finish and check that an `output` branch has been created and contains `contribution-meadow.svg`.
4. Your README already points to `https://raw.githubusercontent.com/Harsh99-ops/Harsh99-ops/output/contribution-meadow.svg`.
5. GitHub will subsequently refresh the meadow every 12 hours according to the workflow schedule (scheduled runs can be delayed or occasionally skipped). Github Actions may require approval for a workflow from a new fork.

**Important:** The calendar generator reads contributions for username `Harsh99-ops` via the GitHub GraphQL API and uses the workflow's built-in `GITHUB_TOKEN`. It does not use someone else's contribution statistics. Private contributions are subject to GitHub API visibility and token permissions. GitHub's `GITHUB_TOKEN` usually cannot read private details of a user's private contributions, so the scene may represent only activities visible to the token.

## 3. SVG banner and animation

- `assets/title.svg` is **already regenerated** with the text `Hi, I'm Harsh`.
- `assets/rocket-retro.svg` is the original pixel-art animated rocket and has been kept as requested. No video creation is necessary.
- To regenerate either image later: `python scripts/generate-header.py`.
- To change the title wording, edit the `title_svg` default argument in `scripts/meadow/header.py` and re-run that command.

## 4. Text you may wish to personalize

- `README.md`: Edit university, role, experience, and listed skills if needed. The current copy uses the background you previously shared.
- `README.md`: Add your TaskFlow repository link when published.
- `README.md`: Add email, LinkedIn, portfolio, or other social links **only once you verify the exact URLs**.
- `scripts/generate-meadow.py`: Username is already set to `Harsh99-ops`.

## 5. Test locally (optional)

Python 3.12+ recommended. Generate the title/rocket SVGs without extra packages:

```bash
python scripts/generate-header.py
```

Generate live contribution meadow (requires a GitHub token with permission to query your GitHub contributions):

```bash
export GITHUB_TOKEN=your_token_here
python scripts/generate-meadow.py
```

Don't commit tokens into any file or share them publicly. GitHub Actions uses a generated token automatically, so manual token setup isn't needed in the repo workflow.
