# Contributing

Bug reports, clearer instructions, and patches are welcome. Open an issue or pull request in the repository you installed from. Include your Claude version, operating system, plugin version, and the steps that reproduce the problem. Leave out keys, tokens, account details, and private transcripts.

## Check a change

These packages contain Markdown and JSON, not an npm application. Install Node.js 22 or newer and Claude Code, then run from the repository root:

```sh
npm install --global @anthropic-ai/claude-code@2.1.288
claude plugin validate . --strict
claude plugin validate .claude-plugin/plugin.json --strict
```

Test installation in a separate profile. On Windows, use Git Bash:

```sh
export CLAUDE_CONFIG_DIR="$(mktemp -d)"
claude plugin marketplace add ./
claude plugin install pushary@pushary-claude-plugin --json
claude plugin list --json
claude plugin details pushary@pushary-claude-plugin
```

The installed version must match `.claude-plugin/plugin.json`, and the MCP server must be `https://pushary.com/api/mcp/mcp`. The inventory must show one skill, `pushary-cowork`, and zero hooks. CI runs these checks on Linux for changes, and on Linux, macOS, and Windows for releases and manual runs. The checks do not sign in to a Pushary account or prove device delivery. State any live checks you ran separately.

## How a patch ships

This repo is a public mirror. Maintainers apply accepted changes to the source monorepo, run the checks, and publish a new snapshot here. A direct mirror-only change can be overwritten by the next sync. You do not need access to the private repo to contribute.

The shared skill is generated from one source. Report a skill change in your public PR; maintainers update the source and both plugin copies together. Your public PR records the contribution, and the maintainer credits it when the public snapshot ships.

## Security

Report vulnerabilities privately to **aadil@pushary.com**, or follow the [organization security policy](https://github.com/Pushary/.github/blob/main/SECURITY.md). Do not open a public issue with an exploit or credentials.
