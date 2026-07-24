# readings

Long-form thinking notes, published as a single-file site.

**Live:** https://vaibhavgit9210.github.io/readme/

| File | What it is |
|---|---|
| `index.html` | The site. Single file, no build step, no CDN, works offline. Dark/light, mobile-first. |
| `ant-analogy-interstellar.md` | Source: the ant analogy stress-tested against the literature. |
| `reading-track.md` | Source: 41-item reading curriculum in seven tiers. |

## Conventions

- One `index.html`, everything inline. Must work from `file://`.
- Reading ticks persist in `localStorage` only — nothing is uploaded.
- The site carries the standard `site-analytics` beacon (anonymous, no cookies, no raw IPs).
- Adding a new note: write the `.md`, add a section to `index.html`, add a TOC entry.
  If it has a checkbox list, the counter total in `#counter` is derived automatically.

## Deploy

    git push origin main
    git push origin main:gh-pages

Verify with headless Chrome, not by assumption:

    "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
      --headless=new --disable-gpu --use-angle=swiftshader \
      --window-size=500,5200 --virtual-time-budget=4000 \
      --screenshot=shot.png "file://$PWD/index.html"

Known quirk: screenshots taken *after* a programmatic scroll come out blank under
`--virtual-time-budget`. Use a tall `--window-size` instead of scrolling, and temporarily
`display:none` earlier sections to bring a lower section into frame.
