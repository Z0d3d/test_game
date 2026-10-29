# Drop-in assets

Everything in this folder is served as-is by the dev server and copied
verbatim into `dist/` by the build. No code changes are needed to swap a file.

## Sounds — `public/audio/`

| File | Plays when |
|---|---|
| `plop.ogg` | a sand block lifts |
| `throw.ogg` | a chunk lands in the truck bed |
| `truck-depart.ogg` / `truck-arrive.ogg` | the truck cycle turns over |
| `coin.ogg` | payout |
| `tier-up.ogg` | combo tier gained |
| `ui-click.ogg` | shop buttons |
| `combo/x2.ogg` … `combo/x12.ogg` | combo loops, one per tier |

- Use the exact names above and the game picks the file up on reload.
- No file → the synthesized fallback plays (the game is always playable).
- Format: OGG preferred; WAV/MP3 also work. Mono, 44.1–48 kHz, under ~150 KB.
- Loops must start and end on a zero crossing.
- Renamed files: point at them in `src/data/sounds.ts` (`file: '/audio/…'`).

## Shovel skins — `public/skins/`

Six skin ids: `steel`, `copper`, `silver`, `gold`, `ember`, `prismatic`.
Each has up to three independent layers:

| Layer | File (for `<id>`) | Size | Notes |
|---|---|---|---|
| Blade | `<id>-blade.png` (legacy `<id>.png` also works) | 1024 × 512, 2:1 | u = around the scoop, v = lip (bottom) → heel (top); 8 px safe border |
| Shaft | `<id>-shaft.png` | 256 × 1024, 1:4 | plain vertical strip |
| Grip | `<id>-grip.png` | 512 × 512 | wraps the T-grip; keep the motif centred |

- Missing files are normal: that layer shows its placeholder (tier tint on the
  blade, wood on the handle/grip).
- A corrupt file logs one warning and falls back alone; the rest of the skin
  still loads.
- Alpha is ignored; the shovel is opaque.
- Preview any skin in-game with `?skin=ember`; browse states with `?assets=1`.
- Manual art replaces files only; see `docs/03-assets-and-structure.md` §3.

## Tuning

Not here — numbers live in `src/config/`, content tables in `src/data/`.
See `docs/03-assets-and-structure.md`.
