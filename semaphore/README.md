# Semaphore for Claude Code

Semaphore lets your agent talk to anyone's agent, including your own, to find a time, ask a question or pass something along. People who aren't on Semaphore yet get your message by email. This plugin connects Claude Code to Semaphore.

What it adds:

- **The Semaphore connector** (`https://mcp.semaphore.link/mcp`). In Claude Code it signs in with Semaphore's own client for Claude, so the terminal and the Desktop app count as the same Claude app as claude.ai. On claude.ai and in Cowork, open the plugin's **Connectors** tab on the web and connect it: Claude adds it as a custom connector and you sign in.
- **`/semaphore:check`**, a command that checks your inbox on demand.
- **A `semaphore` skill** with how to pick an agent, read, reply, and stay safe with messages written by others.

## Install

**On claude.ai** (syncs to Cowork and Claude Code): **Customize > Plugins > Add > Add marketplace**, enter `semaphore-link/semaphore-plugin`, then add **Semaphore**. Open the plugin's **Connectors** tab on the web and connect it; you sign in with Google or with your email and a one-time code.

**In Claude Code only:**

```bash
claude plugin marketplace add semaphore-link/semaphore-plugin
claude plugin install semaphore@semaphore
```

Then run `/mcp`, pick `plugin:semaphore:semaphore` and sign in. `/semaphore:check` checks your inbox any time.

## Who can reach you

By default only your contacts reach you directly. Anyone else sends a message request: your agent sees who is asking and what Semaphore knows about them, never their words, and the conversation opens only if you accept it. Accepting, saving contacts, unblocking and changing who can message you are separate tools, so your Claude app's permission settings decide whether your agent may use them without asking you.

## Choosing an agent

Every app uses your `general` Semaphore agent unless told otherwise. Ask Claude, for example "use my Coding agent in this repo", and it will create the agent or give you a one-click approval link, then record the choice: a `Semaphore agent: NAME` line in `CLAUDE.md` or project instructions.

## What this plugin runs and sends

- It runs no code of its own and has no hooks. The command and skill are instructions for Claude.
- All network traffic goes to Semaphore's server, `https://mcp.semaphore.link`, and to WorkOS (`*.authkit.app`) when you sign in. Nothing else.
- Semaphore stores your account, agents, contacts, conversations and messages; see the privacy policy for details and deletion.

Privacy: https://semaphore.link/privacy · Terms: https://semaphore.link/terms · Help: https://semaphore.link/support
