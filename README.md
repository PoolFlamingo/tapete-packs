# Proxy Builder frame packs

Downloadable content for the card editor of
[Proxy Builder](https://github.com/PoolFlamingo/proxy-builder). The app
downloads each pack from a fixed commit of this repository and checks the
SHA-256 of every file (the manifest lives in the app:
`src-tauri/assets/packs-descargables.json`).

## `balatro/`

Pixel-art frames themed after Balatro: seven templates (Joker, Land,
Planeswalker, Planet, Spectral, Tarot and Voucher) with their variants, mana in
poker chips, rarity as a label, coloured words and scanlines. It also includes
two card backs, tokens, the basic lands and the ready-made cards of the sample
deck. The original templates and sample cards are by **u/Poke_Hybrids**
([original post](https://www.reddit.com/r/mtg/comments/1fglapq/balatrothemed_mtg_proxy_deck/));
PoolFlamingo integrated them into Tapete but did not create them, and express
permission to redistribute them within Tapete is pending confirmation. Credits
in `balatro/CREDITS.md`.

### Rebuilding it from the templates

In `balatro/source/`, with a venv that has `psd-tools`, `pillow` and `numpy`:

1. `python -I convert.py <folder with the PSDs> ..` — layers and inventory.
2. `python -I build.py .. <Drive folder> <m6x11plus.ttf>` — symbols, labels,
   extras and `pack.json` (leaves only the layers it uses).
3. `python -I manifest.py .. <commit>` — the app's manifest entry.

`build.py` deletes the layers it does not use: if you run it again, run
`convert.py` first.

## License

The licence depends on what each file is:

- **The scripts** (`*/source/*.py`) are free software under the
  [GNU General Public License v3.0 or later](LICENSE), like the app.
- **The pack contents** (templates, layers, fonts, symbols, sample cards) are
  **not** covered by that licence: each pack keeps the terms of its authors,
  listed in its `CREDITS.md` (for Balatro, `balatro/CREDITS.md`, where
  permission to redistribute is still pending confirmation). Do not reuse
  them outside what those terms allow.
- *Magic: The Gathering* names, card text and symbols belong to Wizards of the
  Coast.
