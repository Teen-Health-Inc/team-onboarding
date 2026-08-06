# Teen Health website team onboarding

This public repository helps Teen Health, Inc. team members prepare a computer to work on the private Outside the City website repository with an AI coding assistant.

The website source code is not in this repository. The private project is:

<https://github.com/Teen-Health-Inc/outside-the-city>

You can read this guide without a GitHub account. To access the private website repository, you must use your own GitHub account and receive an invitation to the Teen Health organization.

## Start here

1. [Create or verify your GitHub account and organization access](docs/account-access.md).
2. [Ask your AI assistant to set up your computer](docs/ai-setup.md).
3. [Follow the normal website change workflow](docs/website-workflow.md).

## What the AI can and cannot do

After you have a GitHub account and repository access, an AI assistant can usually detect your operating system, install or verify development tools, clone the project, install dependencies, and start the local site.

The AI cannot safely replace your identity and security decisions. You must personally complete email verification, organization invitations, two-factor authentication, browser authorization, and operating-system password prompts. Never send a password, GitHub token, private key, or one-time login code to an AI chat.

## For AI assistants

Read `AGENTS.md` first. It explains how to use this onboarding repository and where the detailed instructions are. Then follow the relevant document instead of inventing a new setup process.

## Important boundaries

- This repository contains onboarding documentation only.
- Do not put website source code, production credentials, VPS details, SSH keys, API keys, `.env` files, or sensitive organizational information here.
- Do not ask a new team member to share another person's GitHub account or token.
- Do not deploy from a contributor computer. Website changes go through the private repository's pull-request and review process.

## If something does not work

Stop and report the exact error. Common causes are a missing GitHub organization invitation, an unverified email address, a missing local permission, an unsupported operating system, or a Node.js version other than 22.x.
