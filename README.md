# Teen Health project onboarding

This public repository helps Teen Health, Inc. team members prepare a computer to work on any Teen Health project with an AI coding assistant.

This repository contains onboarding instructions, not project source code. The AI should use the project repository's own README, agent instructions, and development documentation as the source of truth for project-specific tools and commands.

## How to use this guide

Give your AI assistant this public repository link together with the Teen Health project you need to work on:

```text
Help me set up my computer for this Teen Health project. Use this onboarding guide first:
https://github.com/Teen-Health-Inc/team-onboarding

The project I need to work on is:
[paste the project's GitHub URL or repository name here]
```

If you do not know the project repository, tell the AI to stop and ask you for it. It must not guess which Teen Health project you mean.

You can read this guide without a GitHub account. To access a private project, you must use your own GitHub account and receive access to that repository or its organization.

## Claude Desktop users

If you are using Claude Desktop, open the **Code** tab before giving it the setup request. Choose the **Local** environment and select an empty working folder or the folder where you want the project cloned. Do not use the Chat or Cowork tabs for this setup; they do not provide the same local coding terminal. Do not install GitHub Desktop as a workaround.

## Start here

1. [Create or verify your GitHub account and project access](docs/account-access.md).
2. [Ask your AI assistant to set up your computer](docs/ai-setup.md).
3. [Follow the normal project change workflow](docs/project-workflow.md).

## What the AI can and cannot do

After you have a GitHub account and project access, an AI assistant can usually detect your operating system, install or verify Git tools, clone the project, install the project's dependencies, and run its documented development command.

The AI cannot safely replace your identity and security decisions. You must personally complete email verification, organization invitations, two-factor authentication, browser authorization, and operating-system password prompts. Never send a password, GitHub token, private key, or one-time login code to an AI chat.

## For AI assistants

Read `AGENTS.md` first. It explains how to use this onboarding repository and where the detailed instructions are. Then follow the relevant document instead of inventing a new setup process.

## Important boundaries

- This repository contains organization-wide onboarding documentation only.
- Do not put project source code, production credentials, VPS details, SSH keys, API keys, `.env` files, or sensitive organizational information here.
- Do not ask a new team member to share another person's GitHub account or token.
- Do not deploy from a contributor computer. Project changes go through the target repository's pull-request and review process.

## If something does not work

Stop and report the exact error. Common causes are a missing GitHub project invitation, an unverified email address, a missing local permission, an unsupported operating system, or a project-specific runtime or dependency problem.
