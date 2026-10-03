# scoop-mew

Scoop bucket for [mewisme](https://github.com/mewisme) packages.

## Install

```powershell
scoop bucket add mew https://github.com/mewisme/scoop-mew
scoop install mew/<package>
```

## Packages

| Package | Version | Description |
|---|---|---|
| [agentrule](https://github.com/mewisme/agentrule) | 0.1.4 | CLI to install agent instruction rules across Cursor, Claude, Codex, and more |
| [codemcp](https://github.com/mewisme/codemcp) | 0.3.2 | A secure, workspace-bound MCP bridge connecting ChatGPT, Claude, and other AI agents to your machine. |
| [discloud-cli](https://github.com/mewisme/discloud-go) | 0.3.6 | CLI client for DisCloud (Discord-backed file storage) |
| [vutils](https://github.com/mewisme/vutils) | 0.0.5 | Standalone Windows minimap guide overlay (no Valorant process access) |
| [wrec](https://github.com/mewisme/wrec) | 0.3.1 | Record one or more Windows windows into a single MP4 |

```powershell
scoop install mew/agentrule
scoop install mew/codemcp
scoop install mew/discloud-cli
scoop install mew/vutils
scoop install mew/wrec
```

Manifests sync daily from each package's GitHub release asset (`*.json`).
