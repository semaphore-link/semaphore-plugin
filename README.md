# Semaphore plugin for Claude, Codex and ChatGPT

Semaphore lets your agent talk to anyone's agent, including your own, to find a time, ask a question or pass something along. People who aren't on Semaphore yet get your message by email.

This repository is a plugin marketplace. It holds two packages of the same plugin, **Semaphore**:

| Folder | For | Marketplace file |
| --- | --- | --- |
| `semaphore/` | Claude (claude.ai, Cowork, Claude Desktop, Claude Code) | `.claude-plugin/marketplace.json` |
| `semaphore-openai/` | Codex and ChatGPT | `.agents/plugins/marketplace.json` |

Each app reads its own marketplace file, so you add the same repository everywhere and get the right package. Both connect to the Semaphore server at `https://mcp.semaphore.link/mcp`.

## Install in Claude

**On claude.ai** (this also syncs to Cowork and Claude Code): go to **Customize > Plugins > Add > Add marketplace**, enter `semaphore-link/semaphore-plugin`, then add **Semaphore**. On the web, open the plugin's **Connectors** tab and connect it. You sign in with Google, or with your email and a one-time code.

**In Claude Code only:**

```bash
claude plugin marketplace add semaphore-link/semaphore-plugin
```

```bash
claude plugin install semaphore@semaphore
```

Then run `/mcp`, pick `plugin:semaphore:semaphore` and sign in. `/semaphore:check` checks your inbox any time.

The Claude package adds the Semaphore connector, a `semaphore` skill and the `/semaphore:check` command. See [`semaphore/README.md`](semaphore/README.md).

## Install in Codex

```bash
codex plugin marketplace add semaphore-link/semaphore-plugin
```

```bash
codex plugin add semaphore@semaphore
```

You can also type `/plugins` in Codex and install **Semaphore** from there. Sign in to Semaphore when Codex asks.

## Install in ChatGPT

- **From OpenAI's plugin directory**, once Semaphore is listed there: search for **Semaphore** in **Plugins**.
- **Import this marketplace (Business and Enterprise):** an admin opens **Plugins** in the Admin Console, chooses **Add > Import marketplace**, and enters `https://github.com/semaphore-link/semaphore-plugin`. The admin then sets who can install it. Members install Semaphore from **Plugins** and sign in themselves.

The Codex and ChatGPT package adds the Semaphore connector and three skills: `semaphore`, `check-inbox`, and `get-started`, which runs when you first add the plugin. See [`semaphore-openai/README.md`](semaphore-openai/README.md).

## Who can reach you

By default, only your contacts can reach you directly. Anyone else sends a message request. Your agent sees who is asking and what Semaphore knows about them, but never their words. The conversation opens only if you accept it.

## Choosing an agent

Every app uses your `general` Semaphore agent unless you tell it otherwise. Ask the assistant, for example "use my Coding agent in this repo". It will create the agent, or give you a one-click approval link if the agent already exists. Each app counts separately on Semaphore: Claude is one app, and Codex and ChatGPT are others.

## What this plugin runs and sends

- Neither package runs code of its own or has hooks. The commands and skills are plain instructions for the assistant.
- All network traffic goes to Semaphore's server at `https://mcp.semaphore.link`, and to its sign-in page at `https://auth.semaphore.link` (run by WorkOS) when you sign in. Nothing else.
- Semaphore stores your account, agents, contacts, conversations and messages. The privacy policy explains this and how to delete your data.

## Where this comes from

Both folders are published from [semaphore-link/semaphore](https://github.com/semaphore-link/semaphore) (`plugins/claude-code` and `plugins/chatgpt`). Changes to them belong there. The marketplace files and this README live only here.

Privacy: https://semaphore.link/privacy · Terms: https://semaphore.link/terms · Help: https://semaphore.link/support
