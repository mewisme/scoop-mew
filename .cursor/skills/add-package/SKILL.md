---
name: add-package
description: Add or register a package in the scoop-mew Scoop bucket. Normal packages are auto-registered by sync-package repository_dispatch; registry overrides remain available when repository and package names differ.
---

# Add package to scoop-mew

Prefer the automatic release flow.

## Automatic flow

A package repository sends:

```json
{
  "event_type": "sync-package",
  "client_payload": {
    "name": "<name>",
    "tag": "vX.Y.Z"
  }
}
```

The workflow then:

1. Validates `name` and `tag`.
2. If `name` is absent from `registry.json`, adds it enabled with asset `<name>.json`.
3. Downloads `<name>.json` from that tagged release and validates it as JSON.
4. Rebuilds all generated README package rows and install commands from enabled registry entries.
5. Commits `registry.json`, `README.md`, and `bucket/` together only after successful sync.

README package rows contain Package, Version, and Description. Version and description come from `<name>.json`.

## Registry overrides

By default repository name equals package name. Only edit `registry.json` manually when an override is required, for example:

```json
{
  "name": "discloud-cli",
  "repo": "discloud-go",
  "asset": "discloud-cli.json",
  "enabled": true
}
```

Do not manually edit README for normal package registration; the workflow regenerates it.
