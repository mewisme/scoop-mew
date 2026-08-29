# scoop-mew

Scoop bucket for [mewisme](https://github.com/mewisme) packages.

## Install

```powershell
scoop bucket add mew https://github.com/mewisme/scoop-mew
scoop install mew/<package>
```

## Packages

| Package | Description |
|---|---|
| [agentrule](https://github.com/mewisme/agentrule) | CLI to install agent instruction rules across Cursor, Claude, Codex, and more |
| [discloud-cli](https://github.com/mewisme/discloud-go) | CLI client for DisCloud (Discord-backed file storage) |
| [vutils](https://github.com/mewisme/vutils) | Standalone Windows minimap guide overlay (no Valorant process access) |
| [wrec](https://github.com/mewisme/wrec) | Record one or more Windows windows into a single MP4 |
| [chatgpt-mcp](https://github.com/mewisme/chatgpt-mcp) | Self-hosted MCP runtime with local tools, upstream MCP aggregation, and OpenAI Secure MCP Tunnel |

```powershell
scoop install mew/agentrule
scoop install mew/discloud-cli
scoop install mew/vutils
scoop install mew/wrec
scoop install mew/chatgpt-mcp
```

Manifests sync daily from each package's GitHub release asset (`*.json`).
