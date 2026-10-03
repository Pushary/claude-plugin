# Pushary for Claude

Get Claude task updates and answer its questions from your phone or Mac notch. The plugin bundles a skill and Pushary's hosted OAuth connector for Claude Chat, Cowork, and Claude Code.

The older [Pushary for Cowork plugin](https://github.com/Pushary/cowork-plugin) remains available for Cowork. Choose one Pushary plugin per app to avoid duplicate connectors. Both plugins use the same shared skill; its `pushary-cowork` identifier is retained for compatibility.

## Install

In Claude Chat or Cowork, open **Customize > Plugins > Add > Add marketplace** and add `https://github.com/Pushary/claude-plugin`. Install **Pushary for Claude** from that marketplace. This GitHub installation does not require a directory listing.

In Claude Code:

```text
/plugin marketplace add Pushary/claude-plugin
/plugin install pushary@pushary-claude-plugin
```

## Setup

In Chat or Cowork, open the plugin's **Connectors** tab, connect Pushary, and sign in with the same Pushary account used by your phone and Mac app. Enable Pushary in the conversation. If the connector is missing, add `https://pushary.com/api/mcp/mcp` under **Customize > Connectors > Add custom connector** and leave OAuth Client ID and Secret empty. In Claude Code, use `/mcp` to check the connection and follow the OAuth sign-in prompt.

Follow [SETUP.md](SETUP.md) for account setup and verification. The connector uses OAuth; no local CLI, API key, or package installation is required.

Use the bundled skill to guide when Claude asks questions and sends updates. In Cowork, standing instructions in **Settings > Cowork** are also supported. Ask Claude a harmless Pushary test question, answer from your phone or notch, and verify Claude receives the answer. A successful notification alone does not verify answers.

## Included

- `.mcp.json`: the public OAuth connector, with no embedded key.
- `skills/pushary-cowork/SKILL.md`: when to ask, notify, and hand off unanswered questions.
- `SETUP.md`: account setup, verification, and recovery.

## Capabilities

| Surface | Questions and task updates | Native permission interception in this bundle |
| --- | --- | --- |
| Claude Chat: web, desktop, and mobile | Through the remote connector | None |
| Cowork | Through the remote connector | None |
| Claude Code | Through the remote connector | None |

Claude chooses when to call the tools. This bundle can wait for a question it asked and receive your answer on that request. It cannot intercept native permission prompts, send new work into an ended turn, or launch tasks.

For Claude Code approval hooks, use the separate [Pushary Claude Code integration](https://github.com/Pushary/pushary-skill). Choose one setup path rather than installing duplicate Pushary connectors. Chat ignores hooks; this bundle installs none. [Anthropic's platform support table](https://claude.com/docs/plugins/platform-support) describes what each app loads.

## Data sent to Pushary

Claude sends the arguments of Pushary tool calls to `https://pushary.com/api/mcp/mcp`. These can include question text, answer options, notification titles and summaries, optional context, and agent and session identifiers. Pushary returns your answers to Claude and delivers updates according to your account settings. Keep these messages brief and leave out passwords, API keys, file contents, and private conversation history. The plugin does not install a local process or upload a transcript automatically. See the [privacy policy](https://pushary.com/privacy) for storage and retention details.

[Full guide](https://pushary.com/docs/agents/guides/claude-desktop) · [Plugin support](https://support.claude.com/en/articles/13837440-use-plugins-in-claude) · [Pushary support](https://pushary.com/support)
