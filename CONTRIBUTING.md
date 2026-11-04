# Contributing

Thanks for hacking on `video-renderer`! This guide covers both the command-line and the GitHub web UI workflows. Pick whichever suits you.

## Working an issue

Issues are **not exclusive** — multiple teams may work on the same one at the same time. The first PR that meets the acceptance criteria gets merged; other PRs for the same issue will be closed as superseded. Keep your branch up to date with `main` so late PRs still merge cleanly.

## Option A: Command line

### 1. Fork and clone

Fork the repo on GitHub (button top-right), then:

```bash
git clone https://github.com/<your-username>/video-renderer.git
cd video-renderer
git remote add upstream https://github.com/iamjonjackson/video-renderer.git
```

### 2. Add your own secret for CI

In your fork: **Settings → Secrets and variables → Actions → New repository secret** — add `MISTRAL_API_KEY` with your own key. Forks don't inherit secrets from the upstream repo, so renders in your fork's CI need your key.

### 3. Branch

```bash
git fetch upstream
git checkout -b my-feature upstream/main
```

### 4. Work, commit, push

```bash
git commit -m "Describe your change"
git push -u origin my-feature
```

Team members get commit credit via co-author trailers (the email must match their GitHub account email):

```bash
git commit --amend -m "Describe your change" \
  -m "Co-authored-by: Teammate <teammate@example.com>"
```

### 5. Open the PR

```bash
gh pr create --repo iamjonjackson/video-renderer --head my-feature \
  --title "Short description" --body-file pr-body.md
```

In the PR body, reference the issue with a closing line (e.g. `Closes #5`) and include the required screenshot/video evidence.

## Option B: GitHub web UI only

1. **Fork** the repo via the Fork button.
2. In your fork, use the **pencil (edit) icon** on any file to make changes — GitHub creates a branch for you and offers a commit form. Add co-author trailers in the commit description box ("Add co-authors by name" is built into the web commit UI).
3. For CI secrets: your fork → **Settings → Secrets and variables → Actions** → add `MISTRAL_API_KEY`.
4. Upload evidence (screenshots/video) by dragging files into a PR body comment — GitHub hosts them for you.
5. Open the PR: your fork → **Contribute** button (above the file list) → **Open pull request**, targeting `iamjonjackson/video-renderer:main`.
6. Fill in the PR template (Summary, Verification, Evidence, Team credit) and add `Closes #<issue>`.

## After you open the PR

- A maintainer must click **"Approve and run"** before the repo's workflows run on a first-time contributor's PR.
- The upstream repo's secrets are not shared with fork PRs — that's why evidence goes in the PR body.
- If `main` moves during the hackathon, sync with **Sync fork** (web UI) or `git fetch upstream && git merge upstream/main` (CLI) and push; the PR updates automatically.
- Expect review comments; push fixes to the same branch.

## Merge credit

Co-author trailers carry through squash merges, so every listed teammate appears on the merged commit. Ensure each teammate's trailer email matches their GitHub account.
