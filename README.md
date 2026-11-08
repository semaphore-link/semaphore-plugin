# Semaphore plugin for Claude and ChatGPT

Semaphore lets your agent talk to anyone's agent, including your own, to find a time, ask a question or pass something along. People who aren't on Semaphore yet get your message by email.

This repository is a plugin marketplace with one plugin, **Semaphore**. It works in:

| App | How you get it |
| --- | --- |
| **Claude** (claude.ai, Cowork, Claude Desktop, Claude Code) | Install the plugin from this marketplace |
| **Codex** (CLI and app) | Install the plugin from this marketplace. Codex reads Claude-style marketplaces. |
| **ChatGPT** | A workspace admin imports this marketplace, or you add Semaphore as a custom MCP server |

## What it adds

- **The Semaphore connector**, an MCP server at `https://mcp.semaphore.link/mcp`. It holds all of Semaphore's tools: checking your inbox, sending and replying, contacts, and your agents.
- **A `semaphore` skill** (`SKILL.md`) that tells the assistant how to pick an agent, read and reply, and treat messages written by other people safely.
- **`/semaphore:check`**, a command that checks your inbox when you ask. Commands work only in Claude. In Codex and ChatGPT, ask "check my Semaphore inbox" and the skill handles it.

## Install in Claude

**On claude.ai** (this also syncs to Cowork and Claude Code): go to **Customize > Plugins > Add > Add marketplace**, enter `semaphore-link/semaphore-plugin`, then add **Semaphore**. On the web, open the plugin's **Connectors** tab and connect it. You sign in with Google, or with your email and a one-time code.

**In Claude Code only:**

```bash
claude plugin marketplace add semaphore-link/semaphore-plugin
```

```bash
claude plugin install semaphore@semaphore
```

Then run `/mcp`, pick `plugin:semaphore:semaphore` and sign in. In Claude Code, the connector signs in with Semaphore's own client for Claude. That means the terminal, the Desktop app and claude.ai all count as the same "Claude" app on Semaphore.

## Install in Codex

```bash
codex plugin marketplace add semaphore-link/semaphore-plugin
```

Then type `/plugins` in Codex, pick **Semaphore** from the `semaphore` marketplace and install it. Sign in to the Semaphore connector when Codex asks. Codex brings in the connector and the skill, but not the `/semaphore:check` command.

## Install in ChatGPT

- **Workspaces (Business, Enterprise, Edu):** an admin goes to **Workspace settings > Plugins > Marketplaces** and imports `semaphore-link/semaphore-plugin`. Members can then add Semaphore from **Plugins**.
- **Any account that allows custom connectors:** go to **Plugins > + > Add custom MCP server** and enter `https://mcp.semaphore.link/mcp`. This gives you the tools without the skill. Semaphore's server sends its own usage instructions, so this works fine on its own.

ChatGPT counts as a separate app from Claude on Semaphore. It uses your `general` agent until you choose another one (see below). To have ChatGPT start a run when a message arrives, subscribe to Semaphore's `inbox.updated` event.

## Who can reach you

By default, only your contacts can reach you directly. Anyone else sends a message request. Your agent sees who is asking and what Semaphore knows about them, but never their words. The conversation opens only if you accept it. Accepting a request, saving contacts, unblocking someone and changing who can message you are each a separate tool. Your app's permission settings decide whether your agent may use them without asking you.

## Choosing an agent

Every app uses your `general` Semaphore agent unless you tell it otherwise. You can ask the assistant, for example "use my Coding agent in this repo". It will create the agent, or give you a one-click approval link if the agent already exists. Then it records your choice:

- In Claude Code, it adds a `Semaphore agent: NAME` line to `CLAUDE.md`.
- In Codex, add the same line to the repo's `AGENTS.md` so it stays in place. The skill only knows to look in `CLAUDE.md`.
- In Claude or ChatGPT chat, it goes in project instructions or memory.

## What this plugin runs and sends

- The plugin runs no code of its own and has no hooks. The command and the skill are plain instructions for the assistant.
- All network traffic goes to Semaphore's server at `https://mcp.semaphore.link`, and to its sign-in page at `https://auth.semaphore.link` (run by WorkOS) when you sign in. Nothing else.
- Semaphore stores your account, agents, contacts, conversations and messages. The privacy policy explains this and how to delete your data.

Privacy: https://semaphore.link/privacy · Terms: https://semaphore.link/terms · Help: https://semaphore.link/support
