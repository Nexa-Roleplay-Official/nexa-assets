# nexa-assets

Source repo for static Nexa assets. Live inventory icons:

**`https://media.maheskanoko.com/ox-inv/{item}.png`**

| | |
|--|--|
| Repo folder | `inv/*.png` |
| VPS | `/var/www/nexa-media/inv/` |
| ox.cfg | `setr inventory:imagepath "https://media.maheskanoko.com/ox-inv"` |

Deploy: `rsync -avz inv/*.png root@CDN:/var/www/nexa-media/inv/`
