# nexa-assets

Source repo for Nexa static files.

## Inventory icons (ox_inventory)

**Do not hardcode full CDN / GitHub URLs in `items.lua`.**  
Items only store a **filename**; ox resolves it via convar.

```
items.lua          client.image = 'glue_stick.png'     (filename only)
       ↓
ox.cfg             setr inventory:imagepath "https://media.maheskanoko.com/inv"
       ↓
ox_inventory       imagepath + "/" + filename
       ↓
browser            https://media.maheskanoko.com/inv/glue_stick.png
```

| Step | Where | What |
|------|--------|------|
| 1. Source | this repo `inv/*.png` | commit + push icon |
| 2. Live host | VPS `/var/www/nexa-media/inv/` | rsync / deploy PNG |
| 3. Public URL | `https://media.maheskanoko.com/inv/{file}.png` | Cloudflare → VPS |
| 4. Game config | `nexa-resources/ox.cfg` | `inventory:imagepath` = that base |

**Use `/inv` only.** Paths `/ox-inv` and `/item-icons` are legacy; Cloudflare can still 404-cache newer files there.

### Deploy

```bash
cd nexa-assets
rsync -avz inv/*.png root@CDN:/var/www/nexa-media/inv/
```

### Verify (no game client needed)

```bash
# Must match ox.cfg inventory:imagepath
BASE="https://media.maheskanoko.com/inv"
for f in weed_seed.png jerry_can.png rolling_paper.png weedscissors.png \
         weedleaf_1.png glue_stick.png joint.png; do
  code=$(curl -s -o /dev/null -w "%{http_code}" -L "$BASE/$f")
  echo "$code  $BASE/$f"
done
```

Or open https://media.maheskanoko.com/monitor → Inspect / icon name check.

## Banner (GitHub Pages — separate from inv CDN)

| File | URL |
|------|-----|
| `REV_NEXA_BANNER_FM.gif` | `https://nexa-roleplay-official.github.io/nexa-assets/REV_NEXA_BANNER_FM.gif` |

Used by `server.cfg` `banner_detail` / `banner_connecting`. Not the inventory imagepath.
