# Step 2: Ask an AI assistant to set up the computer for a project

The shortest first request is the most reliable one:

```text
Help me set up my computer for this Teen Health project. Use this onboarding guide first:
https://teen-health-inc.github.io/team-onboarding/
```

After reading the guide, the AI should ask which Teen Health project you need if you have not provided a project URL or repository name. Give it the target project's GitHub URL when it asks. It must not guess.

## Claude Desktop

Use the **Code** tab, not Chat or Cowork. Choose the **Local** environment and select an empty working folder or the folder where you want the project cloned. If Claude is not in Code mode, it should stop and ask you to switch before attempting setup.

Do not install or use GitHub Desktop for this workflow. The supported GitHub path is GitHub CLI (`gh`).

## What the AI should do after reading this guide

The AI should:

1. Detect whether the computer uses macOS, Windows, or Linux.
2. Check whether Git and GitHub CLI (`gh`) are installed.
3. Install missing tools using official platform instructions. Do not assume Homebrew is installed.
4. Check whether GitHub CLI is already authenticated:

   ```bash
   gh auth status
   ```

5. If GitHub CLI is not authenticated, run this command itself:

   ```bash
   gh auth login --hostname github.com --git-protocol https --web
   ```

   The AI must not merely tell the user to run the command. It must start the command, wait for GitHub to open or display the browser link and one-time verification code, and tell the user to complete that step on GitHub's page. The code must never be pasted into the AI chat.

6. Run `gh auth status` again after the browser flow completes.
7. Confirm that the user's account can access the target project.
8. Clone the target project into a normal development folder without overwriting an existing folder.
9. Read the target project's `README.md`, `CONTRIBUTING.md`, `AGENTS.md`, `CLAUDE.md`, and any relevant setup, development, architecture, or testing documentation that exists.
10. Install dependencies and run the local development command documented by that project.

Do not assume the target project uses Node.js, npm, Next.js, or a browser-based development server. The target project's documentation is the source of truth for its tools and commands.

## Security boundaries

- Never ask for a computer password, GitHub token, SSH key, private key, or one-time login code in the AI chat.
- Tell the user to enter computer passwords into the operating system's own prompt or their own Terminal/PowerShell window.
- Use the user's own GitHub account. Never use another person's account or credentials.
- Do not access production, deployment secrets, DNS, SSH keys, server configuration, or the VPS during setup.
- Do not edit project files, create branches, commit, push, merge, or deploy during first-time setup.

## If the AI cannot use the computer

Some AI applications can read this page but cannot operate the user's local terminal. In that case, the AI must say so clearly and show one command at a time. The user runs the commands in their own Terminal, PowerShell, or Linux terminal and reports only non-sensitive results back to the AI.
