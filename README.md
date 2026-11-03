# BeatStars Trap & Drill Beats Player (Free & Paid)

Streaming player & random-download API for BeatStars tracks matching:
- **Genres:** `TRAP`, `DRILL`
- **Track Type:** `Beat` (`category:BEAT`)
- **Moods:** `DARK`, `POWERFUL`, `ANGRY`, `ENERGETIC`, `EPIC`
- **Vocal Presence:** `NONE`
- **Pricing:** Includes **both Free and Paid** beats for streaming; **MP3 downloads are restricted strictly to beats with Free Downloads enabled on BeatStars (`f: 1`)**.

## Build Pipeline
1. Enumerate tracks into `free_trap_streams.db`:
   ```bash
   python scraper.py
   ```
2. Resolve any missing stream URLs (if needed):
   ```bash
   python resolve_fast.py
   ```
3. Export static site (`site/`):
   ```bash
   python finish_export.py --skip-resolve
   ```
4. Self-host single-threaded `ffmpeg.wasm` (optional):
   ```bash
   python fetch_ffmpeg.py
   ```
5. Upload to GitHub Pages in resumable batches:
   ```bash
   python upload_site.py https://github.com/<user>/<repo>.git
   ```
