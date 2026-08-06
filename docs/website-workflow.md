# Step 3: Normal website workflow

Once the project is installed locally, use this process for every website change.

## Before editing

Ask the AI assistant to read these files in the private website repository:

1. `README.md`
2. `CONTRIBUTING.md`
3. `AGENTS.md`
4. `CLAUDE.md` when using Claude Code
5. `docs/ai-change-guide.md`
6. `docs/website-map.md`

The assistant must run the repository's Git preflight before editing:

```bash
git status --short --branch
git pull --ff-only origin main
```

If the worktree contains uncommitted or untracked files, or the pull fails, stop and ask what should be preserved. Do not automatically stash, reset, clean, overwrite, or resolve conflicts.

## Make and validate the change

The assistant should:

1. Explain the requested change and identify the affected files.
2. Create a focused branch from the current `main` branch.
3. Make the smallest useful change.
4. Run the local development server and inspect the affected page on desktop and mobile sizes.
5. Run `npm run build` and `git diff --check`.
6. Review the complete diff and explain every changed file.

## Review and deployment

Open a pull request for human review. Do not push directly to `main` unless the project owner explicitly approves that exception.

After a reviewed pull request is merged into `main`, GitHub Actions builds the website and deploys the approved production path. Contributors should not build or restart the production website directly on the VPS.

## Content changes need extra review

Ask a human to confirm before changing donation language, financial claims, team names or biographies, participant stories or photos, partner names, safety or legal statements, privacy language, forms, or external integrations.
