# Teen Health computer setup: instructions for the AI assistant

This page is written for the AI assistant. The team member who sent it to you wants you to follow these steps on their computer. Work through them in order, run the commands yourself when you can, and stop at the human checkpoints marked **USER**.

The person you are helping is usually not technical. Use short, plain sentences. Tell them what you are about to do before each step, and tell them exactly what to click when a step needs them.

Starting point: the person already has a GitHub account and has been added to the `Teen-Health-Inc` GitHub organization. Their computer may have none of the tools installed yet.

## Before you start

- **You must be able to run commands on this computer.** If you cannot (for example, you are a chat-only assistant or the Claude Desktop **Chat** or **Cowork** tab), stop and say so. Claude Desktop users must open the **Code** tab, choose **Local**, and select a folder. If you cannot run commands at all, go to [If you cannot run commands](#if-you-cannot-run-commands).
- Never ask for, or accept, a password, GitHub token, SSH key, or private key in the chat. The person enters passwords only in their operating system's own dialog or on github.com.
- Do not install GitHub Desktop. The supported GitHub tool is GitHub CLI (`gh`).
- Do not edit project files, create branches, commit, push, or deploy during this setup.

## Step 1: Find the operating system

Run `uname -s` (macOS prints `Darwin`, Linux prints `Linux`). On Windows, use PowerShell. Tell the person which system you found.

## Step 2: Install Git

Check with `git --version`. If it prints a version, go to Step 3.

- **macOS:** run `xcode-select --install`. **USER:** a macOS window appears; click **Install** and wait for it to finish (5–15 minutes). Then run `git --version` again.
- **Windows:** run `winget install --id Git.Git -e --source winget`. **USER:** approve the Windows permission prompt if one appears. Close and reopen the terminal (or start a new assistant session) so the new command is found.
- **Linux (Debian/Ubuntu):** the command needs an administrator password, so ask the person to run it in their own terminal window: `sudo apt update && sudo apt install -y git`.

## Step 3: Install GitHub CLI (`gh`)

Check with `gh --version`. If it prints a version, go to Step 4.

- **macOS with Homebrew** (`brew --version` works): run `brew install gh`.
- **macOS without Homebrew:** do not install Homebrew just for this. Download the macOS `.pkg` installer from the official release page <https://github.com/cli/cli/releases/latest> (the file named `gh_<version>_macOS_universal.pkg`) and open it with `open <file>.pkg`. **USER:** click through the installer and enter your Mac password in the macOS dialog. Then run `gh --version` again.
- **Windows:** run `winget install --id GitHub.cli -e --source winget`, then reopen the terminal.
- **Linux:** follow the official instructions at <https://github.com/cli/cli/blob/trunk/docs/install_linux.md>. Ask the person to run any `sudo` commands in their own terminal.

## Step 4: Sign in to GitHub

Run `gh auth status`. If it says the person is logged in to `github.com`, go to Step 5.

Otherwise, start the sign-in yourself:

```bash
gh auth login --hostname github.com --git-protocol https --web
```

**Important: this command does not finish right away.** It prints a one-time code and the link `https://github.com/login/device`, then waits (up to about 15 minutes) until the person approves in the browser. If your tools wait for a command to finish before showing you its output, run it as a background task (or with its output written to a file) so you can read the code while it is still waiting. Do not run it in a way that times out after one or two minutes. When it runs without a terminal attached, it does not ask any questions; within a few seconds it prints lines like these, then keeps waiting:

```text
! One-time code (ABCD-1234) copied to clipboard
Open this URL to continue in your web browser: https://github.com/login/device
```

As soon as you see the code:

1. Show the person the code and the link `https://github.com/login/device`.
2. **USER:** open the link, sign in to GitHub if asked, type the code, and click **Authorize**. The person does not need to send the code back to you.
3. Wait for the command to finish, then run `gh auth status` to confirm the sign-in.

Then connect Git to that sign-in so `git clone` and `git push` work without extra passwords:

```bash
gh auth setup-git
```

If the person has a terminal of their own and prefers it, they can run the `gh auth login` command there instead; continue when they say it is done.

## Step 5: Choose the project

If the person already gave you a project URL or repository name, use it. Otherwise, list the projects they can access and ask which one they want:

```bash
gh repo list Teen-Health-Inc --limit 100
```

Do not guess. If the project they want is not in the list, their GitHub account does not have access yet: tell them to ask the Teen Health organization administrator, and stop.

## Step 6: Download (clone) the project

Clone into the folder the person selected, or into a normal development folder if they have no preference. Never overwrite an existing folder; if a folder with the project's name already exists, ask what to do. If the current folder is already inside a Git repository (`git rev-parse --show-toplevel` succeeds), do not clone there; ask the person which folder to use instead.

```bash
gh repo clone Teen-Health-Inc/<project-name>
```

## Step 7: Install the project's own tools

Each project lists its own requirements. Read these files in the cloned project if they exist: `README.md`, `CONTRIBUTING.md`, `AGENTS.md`, `CLAUDE.md`, and setup guides under `docs/` (for example `docs/first-time-setup.md`). Follow them to install what the project needs (for example a specific Node.js version) and its dependencies.

Do not assume every project uses Node.js, npm, or a web server. The project's documents are the source of truth. Do not create `.env` files with real secrets; if a project needs secrets, tell the person to ask the project owner.

## Step 8: Check that it works

Run the project's documented development or test command once and confirm it starts without errors. If it serves a web page, give the person the local address to open.

## Step 9: Hand off

Tell the person, in plain words:

- What you installed, and where the project is on their computer (the full folder path).
- That setup is done, and that **for real work they should start a new assistant session with the project folder selected** (in Claude Desktop: Code tab → Local → select the project folder). That way the assistant reads the project's own instructions automatically.
- To describe the change they want in plain language; the project's instructions handle branches, checks, and pull requests.

## If something goes wrong

Stop and tell the person the exact error in plain words. Common causes:

- `gh repo clone` or `gh repo list` says the repository is not found: the account has no access yet. Ask the organization administrator.
- `command not found` right after installing: reopen the terminal or start a new session.
- A password prompt you cannot answer: ask the person to run that command in their own terminal.

Do not work around access errors with another person's account or token.

## If you cannot run commands

Say so clearly. Then give the person one command at a time to paste into their own Terminal (macOS/Linux) or PowerShell (Windows), wait for them to report the result, and continue. They should never paste passwords, tokens, or codes back to you.
