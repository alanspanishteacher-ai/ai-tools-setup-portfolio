# AI Tools Setup Portfolio

A personal portfolio project documenting my process of independently installing, configuring, and authenticating a set of AI-powered development tools from scratch on Windows 11. The goal is to demonstrate hands-on ability to set up a modern AI development environment without guided assistance - working through real errors, policy restrictions, and tooling quirks along the way.

---

## Tools Installed

| Tool | Purpose |
|------|---------|
| [Cursor IDE](https://www.cursor.com/) | AI-native code editor |
| [Claude Code (CLI)](https://docs.anthropic.com/en/docs/claude-code) | Anthropic's terminal-based AI coding assistant |
| [Codex (CLI)](https://github.com/openai/codex) | OpenAI's command-line coding agent |
| [Node.js](https://nodejs.org/) | JavaScript runtime required for npm-based CLI tools |
| [Git](https://git-scm.com/) | Version control and repository management |

---

## Steps Completed

1. **Installed Cursor IDE** - Downloaded and installed Cursor as the primary development environment.
2. **Installed Claude Code via native CLI** - Because this version of Cursor does not include a traditional Extensions panel like VS Code, I installed Claude Code directly through PowerShell as a standalone CLI tool rather than as an editor extension.
3. **Authenticated Claude Code with Claude Pro account** - Ran the authentication flow and linked the CLI to my existing Claude Pro subscription.
4. **Installed Node.js** - Downloaded and installed Node.js to get access to the `npm` package manager, which is required by several CLI tools.
5. **Installed Codex via npm** - Used `npm install -g @openai/codex` to install the Codex CLI globally.
6. **Authenticated Codex** - Codex automatically detected an existing OpenAI session and did not require explicit manual login.
7. **Created a GitHub repository** - Set up this repository on GitHub to track and showcase the setup process.
8. **Cloned the repository locally** - Used Git to clone the repo to my local machine and begin committing work.

---

## Issues Encountered and Solutions

### 1. Cursor had no classic Extensions panel

Cursor's interface in its current version does not expose the traditional Extensions sidebar that VS Code users are familiar with. Searching for Claude Code as an extension the usual way didn't work.

**Solution:** Installed Claude Code as a native CLI tool via PowerShell, bypassing the need for an editor extension entirely. This actually turned out to be the more capable setup - the CLI works across any editor or terminal session, not just inside Cursor.

---

### 2. npm failing with "running scripts is disabled"

When trying to run `npm` commands in PowerShell, I hit this error:

```
npm : File C:\...\npm.ps1 cannot be loaded because running scripts is disabled on this system.
```

This is caused by Windows PowerShell's default execution policy, which blocks unsigned scripts.

**Solution:** Updated the execution policy for the current user only (no admin rights needed):

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

This allows locally created scripts and signed remote scripts to run, without opening up the system globally.

---

### 3. Git not installed - repository couldn't be cloned

After creating the GitHub repository, I tried to clone it and discovered Git wasn't installed on the machine. The `git` command wasn't recognized in PowerShell at all.

**Solution:** Downloaded and installed Git from [git-scm.com](https://git-scm.com/), ran through the installer with default options, and restarted the terminal. After that, cloning worked without issues.

---

## Final Thoughts

This was more challenging and more fun than I expected. I went in without much familiarity with CLI tools, PowerShell policies, or how these AI tools fit together - every issue was something I had to figure out on my own, working through errors and situations I hadn't encountered before. The point of this project isn't complexity; it's that everything here is real. Real problems, real fixes, real learning. Troubleshooting each step and seeing it eventually come together was genuinely satisfying, and I'm glad I pushed through it.
