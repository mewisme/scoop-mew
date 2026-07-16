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
| [initrule](https://github.com/mewisme/initrule) | CLI to install Cursor rule files (`.cursor/rules/*.mdc`) into a project |
| [wrec](https://github.com/mewisme/wrec) | Record one or more Windows windows into a single MP4 |

```powershell
scoop install mew/initrule
scoop install mew/wrec
```

Manifests sync hourly from each package's GitHub release asset (`*.json`).
