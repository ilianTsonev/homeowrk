# Deploy to GitHub Pages

This repository is prepared to deploy a static site to GitHub Pages using GitHub Actions. The workflow `/.github/workflows/deploy.yml` will run on pushes to the `main` branch and publish the repository contents to Pages.

Suggested steps to create the public repository named `homeowrk` and push your site:

1. (Optional) Install and authenticate the GitHub CLI: https://cli.github.com/

Using `gh` (recommended):

```bash
# from repository root
git init
git add .
git commit -m "Initial commit"
gh repo create homeowrk --public --source=. --remote=origin --push
```

Or using plain `git` (create an empty repo on GitHub first at https://github.com/new):

```bash
# replace USERNAME with your GitHub username
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/USERNAME/homeowrk.git
git push -u origin main
```

After pushing, the Actions workflow will run and publish the site. Your Pages URL will be `https://USERNAME.github.io/homeowrk/` once deployment completes.

Notes:
- The workflow deploys the repository root. If you later add build steps (e.g., a static site generator), update the workflow to publish the build output directory.
- If you want the repository named differently, replace `homeowrk` with your preferred repo name in the commands above.

Workflow note:
- This workflow now deploys by committing the site files to a `gh-pages` branch (via `peaceiris/actions-gh-pages`). After the workflow runs, verify your repository's Pages settings at https://github.com/USERNAME/homeowrk/settings/pages and ensure the source is set to the `gh-pages` branch (or choose the automatic option GitHub suggests).

If you'd like, I can instead revert to an artifact-based Pages workflow and attempt to update any deprecated action versions, but the `gh-pages` push method avoids the deprecated `upload-artifact` action and works without additional fixes.
