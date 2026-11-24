# iftk-versions

The newest version of each team After Effects tool, per platform. Our plugins read this file from
inside After Effects to show "update in IFTK" when the copy that's loaded is out of date.

- File: `versions.json`, read at
  `https://raw.githubusercontent.com/noahwitchell/iftk-versions/main/versions.json` (no token).
- Written only by the catalog's `publish.py`, after each release is uploaded. Don't edit it by hand.
- Holds names, versions and one-line notes only. Downloads live elsewhere.

```json
{
 "schema": 1,
 "generated": "2026-11-23T22:00:00+00:00",
 "tools": {
  "noahglowah": {"name": "NoahGlowah", "mac": "1.4.0", "win": "1.4.0", "notes": "..."}
 }
}
```

- `mac` / `win`: that platform's current version, or `null` if there is no build for it.
- Versions compare like `1.2.0-b5 < 1.2.0 < 1.2.1`.
- New keys may be added; readers must ignore keys they don't know. `schema` changes only if an
  existing key changes meaning.

Offline, plugins read the same format from the copy IFTK writes on each refresh:
`~/Library/Application Support/NoSchmo/Manager/versions.json` (Mac) or
`%APPDATA%\NoSchmo\Manager\versions.json` (Windows). That copy can also carry
`"held": {"<id>": "<version>"}` for tools someone rolled back on purpose in IFTK.
