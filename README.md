# nexa-assets

Public CDN assets for **Nexa Roleplay** — server list banners, logos, and inventory icons served via **GitHub Pages**.

Base URL: `https://nexa-roleplay-official.github.io/nexa-assets/`

## Contents

| Path | Use |
|------|-----|
| `REV_NEXA_BANNER_FM.gif` | FiveM server list banner |
| `REV_NEXA_BANNER_FM_source.gif` | Source banner asset |
| `REV_NEXA_LOGO.png` | Nexa logo |
| `inventory/*.png` | ox_inventory item / weapon icons |

## ox_inventory

In `ox.cfg`:

```cfg
setr inventory:imagepath "https://nexa-roleplay-official.github.io/nexa-assets/inventory"
```

Icons resolve as `{imagepath}/{itemName}.png` (example: `.../inventory/WEAPON_BAT.png`).

Prefer **GitHub Pages** URLs (correct `Content-Type`, CORS `*`). Avoid `raw.githubusercontent.com` for in-game / NUI images.

## Related

- [nexa-resources](https://github.com/Nexa-Roleplay-Official/nexa-resources) — main server scripts
