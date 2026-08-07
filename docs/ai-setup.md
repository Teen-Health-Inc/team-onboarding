# Step 2: Ask an AI assistant to set up the computer for a project

Give this prompt to Codex, Claude Code, or another AI coding assistant that can use the local terminal or computer. Replace the project placeholder with the actual Teen Health project URL or repository name.

If you are using Claude Desktop, start in the **Code** tab, choose the **Local** environment, and select an empty working folder. Do not use the Chat or Cowork tabs for this setup. Do not install or suggest GitHub Desktop.

```text
Set up this computer for the Teen Health, Inc. project at [paste the project's GitHub URL or repository name here].

Use this public onboarding guide as your first source of instructions:
https://github.com/Teen-Health-Inc/team-onboarding

First, detect whether this is macOS, Windows, or Linux. Check which required tools are already installed before making changes.

Required tools:
- Git
- GitHub CLI (`gh`)

Use official installation methods only. Install GitHub CLI (`gh`) using the platform's official package instructions. Do not assume Homebrew is installed. Do not install or suggest GitHub Desktop.

Do not assume this is a JavaScript or website project. After cloning the target project, read its README and project instructions to determine the required runtime, package manager, dependencies, development command, and validation commands. Install only what that project requires.

Security rules:
- Never ask me to paste a computer password, GitHub token, SSH key, private key, or one-time login code into this chat.
- If the operating system displays an administrator or password prompt, tell me to enter the password directly into that operating system prompt or my own Terminal/PowerShell window.
- Use the official GitHub browser login flow. Do not create or request a personal access token just to avoid browser authentication.
- Do not use another person's GitHub account or credentials.
- Do not access production, the VPS, deployment secrets, DNS, SSH keys, or server configuration.

After the tools are ready:
1. Verify Git and `gh`.
2. Check `gh auth status`. If it is not authenticated to GitHub.com, run this command yourself:

   `gh auth login --hostname github.com --git-protocol https --web`

   Do not merely tell me to run it. Wait for the command to open or display GitHub's browser link and one-time verification code. Tell me to open the link and enter the code on GitHub's page. Do not ask me to paste the code into this chat. Wait until I finish, then run `gh auth status` again.
3. Confirm that my own GitHub account can access the target project.
4. Clone the target repository into a normal development folder, without overwriting an existing folder.
5. Read its `README.md`, `CONTRIBUTING.md`, `AGENTS.md`, `CLAUDE.md`, and any project-specific setup or development documentation that exists.
6. Install the dependencies using the project's documented package manager and command.
7. Run the project's documented local development command and tell me how to open or use it.

Do not edit project files, create a branch, commit, push, merge, or deploy anything during this setup. If I am not using a local Code/terminal-capable session, stop and tell me to switch to one. If the project URL is missing, access, permissions, network, or an existing folder prevents progress, stop and explain the exact next action instead of guessing.
```

## If the AI cannot use the computer

Some AI chat or desktop applications can explain commands but cannot operate the user's Terminal or install software. In that case:

1. Ask the AI to show one command at a time.
2. Run the command yourself in Terminal, PowerShell, or the appropriate Linux terminal.
3. Enter passwords only into the native operating-system prompt.
4. Return the command's non-sensitive result to the AI.

Never copy a password, token, private key, or one-time browser code into the AI chat.
