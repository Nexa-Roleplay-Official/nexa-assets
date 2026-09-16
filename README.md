# nexa-assets

Source repo for **static** Nexa assets (inventory icons, banners). Live inventory CDN is **`media.maheskanoko.com`**.

## Inventory icons (ox_inventory)

| | |
|--|--|
| **Live CDN** | `https://media.maheskanoko.com/item-icons/{item}.png` |
| **Repo folder** | `inv/*.png` (this repo) |
| **VPS path** | `/var/www/nexa-media/inv/` on CDN host `210.247.250.102` |
| **ox.cfg** | `setr inventory:imagepath "https://media.maheskanoko.com/item-icons"` |

### Deploy / update icons

```bash
rsync -avz --include='*/' --include='*.png' --exclude='*' \
  inv/ root@210.247.250.102:/var/www/nexa-media/inv/
```

Phone camera uploads stay under `https://media.maheskanoko.com/phone/...`.

## Related

- [nexa-resources](https://github.com/Nexa-Roleplay-Official/nexa-resources) — `ox.cfg`
