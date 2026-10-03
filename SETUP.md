# Set up Pushary for Claude

## 1. Add the connector

Install **Pushary for Claude** as described in [README.md](README.md). In Chat or Cowork, open the plugin's **Connectors** tab and connect Pushary. You can also add this public URL under **Customize > Connectors > Add custom connector**:

```text
https://pushary.com/api/mcp/mcp
```

Leave OAuth Client ID and Secret empty. Sign in with the same Pushary account used by your phone and Mac app. The link contains no key. On versions where installing the plugin does not add its connector, add the URL manually.

In Claude Code, open `/mcp` to check the bundled server and follow its OAuth sign-in prompt.

No local CLI, API key, or package installation is required. Setup is complete only after Claude receives your answer to the test in step 4.

## 2. Enable tools in the task

In a Chat or Cowork conversation, enable Pushary under **Customize > Connectors**. In Claude Code, confirm Pushary is connected in `/mcp`. Claude may ask you to allow its tool calls. If it repeatedly asks permission, check the controls available for that version and your organization’s policy; this setup cannot bypass them.

## 3. Guide proactive use

Use the bundled skill in each app. In Cowork, you can also add standing instructions in **Settings > Cowork** to ask for missing decisions and send task updates while you are away. Chat and Cowork do not rely on a repository’s CLAUDE.md or AGENTS.md for this connector setup.

## 4. Verify both directions

Ask Claude to use Pushary `ask_user` with type `confirm` for a harmless setup question. Use agentName `Claude Chat - Setup check`, `Claude Cowork - Setup check`, or `Claude Code - Setup check` for the app you are testing. Answer from Pushary and verify Claude reports the answer it received. Test the notch and phone separately, including phone delivery while away from your Mac.

If nothing arrives, check the signed-in account, task-level connector enablement, tool permission, and Pushary delivery mode. CLI `doctor` checks your local CLI installation, not this account-level connector. Remove a connector from Claude to disconnect it; CLI clean does not remove account connectors.

## Supported boundary

The connector can notify and ask; it does not intercept native permission prompts or restart an ended turn. This package installs no native hooks. Claude Code approval hooks are provided by the separate [Claude Code integration](https://github.com/Pushary/pushary-skill). A task being open on your Mac does not prove this connector can stop or message it.
