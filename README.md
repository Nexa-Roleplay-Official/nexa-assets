# nexa-assets

Source repo for **static** Nexa assets (inventory icons, banners). Live inventory CDN is **`media.maheskanoko.com`** (same host as mk_phone photos).

## Inventory icons (ox_inventory)

| | |
|--|--|
| **Live CDN** | `https://media.maheskanoko.com/inv/{item}.png` |
| **Repo folder** | `inv/*.png` (this repo) |
| **VPS path** | `/var/www/nexa-media/inv/` on `cdn-server-nexa` (`210.247.250.102`) |
| **ox.cfg** | `setr inventory:imagepath "https://media.maheskanoko.com/inv"` |

### Deploy / update icons

```bash
# from 34. Nexa V2/nexa-assets
rsync -avz --include='*/' --include='*.png' --exclude='*' \
  inv/ root@210.247.250.102:/var/www/nexa-media/inv/
```

Then push this repo so Git stays the backup/source of truth.

Phone **camera uploads** stay under `https://media.maheskanoko.com/phone/...` (API upload). Inventory icons are static files under `/inv/`.

## Other files

| Path | Use |
|------|-----|
| `REV_NEXA_*.gif/png` | server list banner / logo (still via GitHub Pages OK) |

## Related

- [nexa-resources](https://github.com/Nexa-Roleplay-Official/nexa-resources) — `ox.cfg`
