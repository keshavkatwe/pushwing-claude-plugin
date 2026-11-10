# Pushwing for Claude

Publish and schedule content on your own connected YouTube and Instagram accounts, track upload jobs, and review available performance statistics. This repository contains the Claude plugin instructions and remote MCP configuration. The Pushwing backend is hosted separately.

## Install in Claude Code

```sh
claude plugin marketplace add keshavkatwe/pushwing-claude-plugin
claude plugin install pushwing@pushwing-plugins
```

Authenticate the Pushwing MCP server through Claude's normal authentication flow (use `/mcp` in Claude Code). Sign in to your own Pushwing account, then link YouTube or Instagram through [Connections](https://app.pushwing.com/connections). Registration may be waitlisted. Do not paste passwords, tokens, or provider credentials into chat.

## Skills

| Command | Purpose |
| --- | --- |
| `/pushwing:setup` | Check connected accounts, permissions, and publishing limits |
| `/pushwing:publish` | Upload or publish selected media now |
| `/pushwing:schedule` | Schedule publication or change an existing schedule |
| `/pushwing:status` | Inspect jobs and verify YouTube processing and visibility |
| `/pushwing:report` | Summarize available statistics for your own accounts |

Setup, status, and reports are read-only. Public/unlisted YouTube publication and Instagram publication use server previews and require approval of the resolved account, content, visibility, and schedule. A requested private YouTube upload can execute without a server preview. Installing this plugin does not authorize posting.

## What connects and what data moves

The plugin connects to `https://mcp.pushwing.com/mcp` over HTTP MCP with host-managed authentication. It contains no local server, hooks, background executable, or embedded credentials. Claude sends requested tool arguments to Pushwing; Pushwing communicates with the selected YouTube or Instagram account. Tool responses can include account names, media metadata, publication jobs, and available analytics.

Publishing transfers selected media and metadata to Pushwing and the destination provider. Remote media URLs are fetched through Pushwing's staging tools. Local media staging requires a host that can read the file and PUT its bytes to the exact temporary upload URL returned by Pushwing; if unavailable, use an accessible media URL or an already staged asset. Staging may create a temporary public-by-link copy. Staged assets expire after 24 hours and direct-upload URLs after one hour; returned expiry values are authoritative.

The plugin does not persist analytics locally. Service-side handling is governed by the [privacy policy](https://pushwing.com/privacy) and [terms](https://pushwing.com/terms). Do not commit media, tokens, signed upload URLs, or account exports here.

## Development and validation

```sh
claude plugin validate . --strict
claude --plugin-dir .
```

Run the [release checklist](docs/RELEASE.md) before submitting or publishing a version. Increment the manifest version for each release. The GitHub Actions workflow validates structure; it does not authenticate or publish media.

## Support and availability

Report integration issues in [GitHub Issues](https://github.com/keshavkatwe/pushwing-claude-plugin/issues), without credentials or private media. Account availability, optional analytics permissions, quotas, and provider restrictions are determined by the live service. YouTube quota pools are shared across the Pushwing project.

The package is prepared for Claude directory submission; listing approval and authenticated testing on Claude chat, Cowork, and Claude Code remain separate steps.

## License

MIT applies to the files in this repository. Hosted Pushwing services remain governed by their own terms.
