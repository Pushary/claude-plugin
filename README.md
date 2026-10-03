# Pushary for Claude

[![Plugin checks](https://github.com/Pushary/claude-plugin/actions/workflows/plugin-check.yml/badge.svg)](https://github.com/Pushary/claude-plugin/actions/workflows/plugin-check.yml)

Get Claude task updates and answer its questions from your phone or Mac. This plugin connects Claude Chat and Claude Code to your Pushary account.

## Before you install

The plugin source is MIT-licensed. Phone and Mac delivery use the hosted Pushary service, which requires a [Pushary plan](https://pushary.com/pricing) and a connected device. Install [Pushary on your phone or Mac](https://pushary.com/download) and use the same account when connecting Claude. The hosted backend is not included in this repo.

Chat and Cowork plugins require a paid Claude plan. See [Claude’s supported plans and apps](https://support.claude.com/en/articles/13837440-use-plugins-in-claude).

## Install and connect

In Claude Chat, open **Customize > Plugins > Add > Add marketplace**, add `https://github.com/Pushary/claude-plugin`, and install **Pushary for Claude**.

In Claude Code:

```text
/plugin marketplace add Pushary/claude-plugin
/plugin install pushary@pushary-claude-plugin
```

In Chat, connect Pushary from the plugin's **Connectors** tab and enable it in the conversation. In Claude Code, open `/mcp` and follow the OAuth sign-in prompt.

If your Claude version does not add the connector, add `https://pushary.com/api/mcp/mcp` under **Customize > Connectors > Add custom connector**. Leave OAuth Client ID and Secret empty. No Pushary CLI or API key is needed for this setup. See [SETUP.md](SETUP.md) for verification and recovery.

## Try it

Ask Claude:

```text
Use Pushary to ask which summary format I want: bullets or a paragraph.
Wait for my answer and use that format.
```

Answer from your phone or Mac and check that Claude receives the answer. Then try:

```text
When you finish this task, send me a Pushary notification with the result.
```

## What it can do

The shared skill guides when Claude asks questions and sends updates. Claude chooses when to call these tools. The plugin can receive an answer to a question it asked; it does not intercept native permission prompts, start new tasks, or resume an ended turn. It installs no native hooks.

For Cowork, the existing [Pushary for Cowork plugin](https://github.com/Pushary/cowork-plugin) remains available. The shared Claude plugin format also works in Cowork. Choose one Pushary installation per app to avoid duplicate tools. For native Claude Code approval hooks, use the separate [Claude Code integration](https://github.com/Pushary/pushary-skill).

## Verification

[CI](https://github.com/Pushary/claude-plugin/actions/workflows/plugin-check.yml) validates both manifests with pinned Claude Code, installs the checked-out package in an isolated profile, and checks its version, loaded skill, lack of native hooks, and OAuth connector configuration. Changes run on Linux; releases and manual checks also run on macOS and Windows. No account credentials are used.

CI does not test account OAuth or device delivery. Verify those with the [setup checks](SETUP.md#4-verify-both-directions). Directory review is separate; this GitHub release is not an approved Claude directory listing.

## Privacy and contributing

Claude sends the arguments of Pushary tool calls to the hosted connector: questions, answer options, updates, optional context, and agent or session identifiers. Keep secrets, file contents, and private conversation history out of these messages. The plugin does not upload a transcript automatically. Read the [privacy policy](https://pushary.com/privacy) for retention details.

[Report a bug](https://github.com/Pushary/claude-plugin/issues/new/choose) · [Contribute](CONTRIBUTING.md) · [Security reports](https://github.com/Pushary/.github/blob/main/SECURITY.md) · [Support](https://pushary.com/support) · [Full guide](https://pushary.com/docs/agents/guides/claude-desktop)
