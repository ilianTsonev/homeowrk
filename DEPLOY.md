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
