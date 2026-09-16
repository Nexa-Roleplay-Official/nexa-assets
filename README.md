# nexa-assets

Public **CDN** for Nexa Roleplay — served by **GitHub Pages** (no separate CDN host).

**Base URL:** https://nexa-roleplay-official.github.io/nexa-assets/

## How CI/CD works (simple)

```
drop PNG into repo  →  git push main  →  GitHub Pages rebuild  →  live CDN URL
```

There is no extra upload step. **This repo IS the CDN source.** Pages is set to publish from `main` `/`.

| Path | Use |
|------|-----|
| `inv/*.png` | **ox_inventory icons** (current — see `ox.cfg`) |
| `inventory/` | legacy (empty after wipe; do not use) |
| `REV_NEXA_*.gif/png` | server list banner / logo |

### ox_inventory (`nexa-resources/ox.cfg`)

```cfg
setr inventory:imagepath "https://nexa-roleplay-official.github.io/nexa-assets/inv"
```

Resolves as `{imagepath}/{itemName}.png`  
Example: `https://nexa-roleplay-official.github.io/nexa-assets/inv/WEAPON_BAT.png`

### Add / update icons

1. Put files in `inv/` named exactly like the item key (`bandage.png`, `WEAPON_PISTOL.png`).
2. Commit + push to `main` on [Nexa-Roleplay-Official/nexa-assets](https://github.com/Nexa-Roleplay-Official/nexa-assets).
3. Wait ~1–2 minutes for Pages, then hard-reconnect / clear FiveM cache if an old URL was cached.

Prefer **GitHub Pages** URLs (CORS + correct `Content-Type`). Avoid `raw.githubusercontent.com` for NUI.

## vs mk_phone images

| | mk_phone | ox_inventory |
|--|----------|--------------|
| Where files live | Inside resource: `mk_phone/images/` | This CDN repo: `inv/` |
| How game loads them | `nui://mk_phone/images/...` (bundled) | HTTPS Pages URL from `inventory:imagepath` |
| “CI/CD” | Ship with resource update | Push to this repo → Pages |

Phone **item** icons used by ox (`phone_black.png`, etc.) should also exist under `inv/` so inventory slots match.

## Related

- [nexa-resources](https://github.com/Nexa-Roleplay-Official/nexa-resources) — `ox.cfg` imagepath
