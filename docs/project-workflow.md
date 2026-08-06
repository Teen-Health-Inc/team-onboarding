# Step 3: Normal project workflow

Once the target project is installed locally, use its own documentation together with this general process.

## Before editing

Ask the AI assistant to read the target repository's available instructions, especially:

1. `README.md`
2. `CONTRIBUTING.md`
3. `AGENTS.md`
4. `CLAUDE.md` when using Claude Code
5. Any `docs/` setup, development, architecture, or testing guides

The assistant must run the target repository's documented Git preflight before editing. At minimum:

```bash
git status --short --branch
git pull --ff-only
```

If the worktree contains uncommitted or untracked files, or the pull fails, stop and ask what should be preserved. Do not automatically stash, reset, clean, overwrite, or resolve conflicts.

## Make and validate the change

The assistant should:

1. Explain the requested change and identify the affected files.
2. Identify the target project's default branch and create a focused working branch according to its instructions.
3. Make the smallest useful change.
4. Run the target project's documented local development command and inspect the result when applicable.
5. Run the target project's documented build, test, lint, format, or validation commands.
6. Run `git diff --check`, review the complete diff, and explain every changed file.

Do not assume that every project uses Node.js, npm, Next.js, or a browser-based development server. Follow the target project's source-of-truth documentation.

## Review and deployment

Open a pull request for human review. Do not push directly to the default branch unless the project owner explicitly approves that exception.

After a reviewed pull request is merged, follow that project's documented release or deployment process. Contributors should not access production systems or deploy directly unless the project owner has explicitly authorized it.

## Content and sensitive changes need extra review

Ask a human to confirm before changing organizational claims, financial language, participant or client information, personal data, legal or safety statements, external integrations, infrastructure, deployment configuration, or secrets.
