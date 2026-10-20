# Sand Timer

A free, ad-free sand timer for limiting spotlight time in online D&D sessions. Open it, screen-share the window over your voice call, and everyone watches the same sand drain.

**Live:** https://gishadev.github.io/spotlight-timer/

One static `index.html`: no build step, no tracking, no cookies. Google Fonts is the only external request; if it fails, system fonts are used. Works offline once loaded, and when opened as a local file.

## URL parameters

All optional. Example: `?t=45&name=Thorin&sound=gong&clean=1`

| Parameter   | Values                                        | Default              | Behaviour |
|-------------|-----------------------------------------------|----------------------|-----------|
| `t`         | Seconds (`45`) or a duration (`1m30s`, `2m`, `90s`) | `45`           | Timer length. Clamped to 5 s – 60 min. Invalid → default. |
| `name`      | Text, up to 20 characters                     | empty                | Fills "Spotlight on ___". Empty hides the label in clean mode. |
| `autostart` | `1` / `0`                                     | `0`                  | Starts running as soon as the page loads. |
| `sound`     | `bell`, `gong`, `drum`, `chime`, `off`        | `chime`              | End-of-time sound. |
| `clean`     | `1` / `0`                                     | `0`                  | Opens in clean mode (controls hidden). |
| `presets`   | Comma list of seconds (`15,30,45,60`)         | `15,30,45,60,90,120` | Preset buttons shown. Max 8. |
| `warn`      | Seconds                                       | `5`                  | When the low-time warning starts. `0` disables it. |

Changing settings on the page updates the address bar, so the current setup can be bookmarked at any time. **Copy link** copies it with all non-default parameters.

Handy bookmarks:

- https://gishadev.github.io/spotlight-timer/?t=30&clean=1
- https://gishadev.github.io/spotlight-timer/?t=45&clean=1
- https://gishadev.github.io/spotlight-timer/?t=60&clean=1&sound=gong

## Shortcuts

| Action                        | Button                         | Key |
|-------------------------------|--------------------------------|-----|
| Start / pause / resume        | Start · Pause · Resume · Again | `Space`, or click the hourglass |
| Flip (reset to full)          | Flip                           | `R` |
| Pick a preset                 | Preset chips                   | `1`–`8` |
| Adjust by 5 s                 | −5 / +5                        | `←` / `→` |
| Type a custom length          | Seconds field                  | — |
| Toggle clean mode             | Eye icon                       | `H` |
| Toggle full screen            | Full-screen icon               | `F` |
| Mute / unmute                 | Speaker icon                   | `M` |
| Copy link with current setup  | Copy link                      | — |

Shortcuts are ignored while typing in a field. Changing the duration while running flips the timer to the new length and stops it.

**Clean mode** shows only the name, hourglass and countdown, scaled to fill the window (a ~300×500 px window next to Miro works well). Move the mouse to show a small toolbar.

## Sound

All sounds are synthesized with the Web Audio API. Browsers only allow sound after a click or key press, so with `autostart=1` the page shows a "Click once to enable sound" button. The sound menu also has an optional tick during the last seconds.

When screen sharing, most voice apps only send audio if you turn on "share audio" as you start the share.

## Deploying your own copy

1. Fork or create a public repo and add `index.html`, `favicon.svg` and `README.md` to `main`.
2. **Settings → Pages**: Source "Deploy from a branch", branch `main`, folder `/ (root)`, save.
3. After about a minute it's live at `https://<user>.github.io/<repo>/`.
