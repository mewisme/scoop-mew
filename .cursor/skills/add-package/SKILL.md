---
name: add-package
description: Add a new package to the scoop-mew Scoop bucket. Updates registry.json, README.md, and seeds bucket/<name>.json from the package GitHub release. Use when adding a package, registering a new app, or wiring a new mewisme tool into scoop-mew.
---

# Add package to scoop-mew

Wire a new package into this bucket. By default the GitHub repo name under the same owner **is** the package name. Override with optional `repo` when they differ.

## Prerequisites

User must give (or confirm):

| Input | Default |
|---|---|
| `name` | required — Scoop package / local manifest stem (`mew/<name>`) |
| `repo` | optional — GitHub repo slug if different from `name` |
| `description` | from release manifest `.description` if present |
| `asset` | `<name>.json` |
| `enabled` | `true` |

Package must already publish a Scoop manifest as a release asset (e.g. `discloud-cli.json` on `mewisme/discloud-go` releases). Autoupdate fetches from `https://github.com/<owner>/<repo\|name>/releases`.

## Checklist

Do every step. Fewest files: only these three touch points.

### 1. `registry.json`

Append under `packages` (keep existing order style; new entry at end is fine):

```json
{
  "name": "<name>",
  "asset": "<name>.json",
  "enabled": true
}
```

When GitHub repo ≠ package name:

```json
{
  "name": "discloud-cli",
  "repo": "discloud-go",
  "asset": "discloud-cli.json",
  "enabled": true
}
```

Valid JSON only — trailing commas break CI `jq`.

### 2. Seed `bucket/<name>.json`

Fetch latest release asset into `bucket/<name>.json` (local path uses `name`, not necessarily the asset filename) so install works before the next scheduled sync:

```powershell
$owner = (gh repo view --json owner -q .owner.login)  # this bucket's owner
$name = "<name>"
$repo = "<repo>"   # defaults to $name
$asset = "<asset>" # e.g. discloud-cli.json
$url = gh api "repos/$owner/$repo/releases/latest" --jq ".assets[] | select(.name == `"$asset`") | .browser_download_url"
if (-not $url) { throw "Asset $asset missing on $owner/$repo latest release" }
curl.exe -fsSL $url -o "bucket/$name.json"
```

If fetch fails or asset missing: stop and tell the user the package must ship `<name>.json` on its latest GitHub release. Do **not** hand-write a fake manifest.

Optional: trigger CI sync after registry is pushed:

```powershell
gh workflow run "Auto-update manifests"
# package repos can also fire repository_dispatch type sync-package
# with client_payload: { "name": "<name>", "tag": "vX.Y.Z" }
```

### 3. `README.md`

Under **Packages**:

1. Add a table row (alphabetical by package name):

   `| [<name>](https://github.com/<owner>/<name>) | <description> |`

2. Add an install line in the powershell block (same alphabetical order):

   `scoop install mew/<name>`

Description: use manifest `description`, else a one-line summary from the package README/repo.

### 4. Done check

- [ ] `registry.json` has the package, `enabled: true`
- [ ] `bucket/<name>.json` exists and is valid JSON
- [ ] README table + install example updated
- [ ] No other files changed (workflow already reads `registry.json`)

Do **not** edit `.github/workflows/autoupdate.yml` for a normal add.

## Out of scope

- Homebrew tap (`homebrew-mew`) — separate repo
- Changing sync schedule or CI
- Committing unless the user asks
