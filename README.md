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
| [vutils](https://github.com/mewisme/vutils) | Standalone Windows minimap guide overlay (no Valorant process access) |
| [wrec](https://github.com/mewisme/wrec) | Record one or more Windows windows into a single MP4 |

```powershell
scoop install mew/agentrule
scoop install mew/vutils
scoop install mew/wrec
```

Manifests sync daily from each package's GitHub release asset (`*.json`).
