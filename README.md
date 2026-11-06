# Lavender Theme for Standard Notes

[![License: MIT](https://img.shields.io/badge/License-MIT-a79ef4.svg)](LICENSE)
[![Standard Notes](https://img.shields.io/badge/Standard%20Notes-Theme-6366f1.svg)](https://standardnotes.com)

A soft, dark theme for [Standard Notes](https://standardnotes.com) with a lavender accent, set in [Inter](https://rsms.me/inter/).

A pastel like lavender glows against near-black, so since v2.6.0 Lavender sits on its own **charcoal base** (`#1e1e1e`, with a `#252525` sidebar) instead of the native Dark theme's `#0f1011`, uses a soft white for text, and marks the selected tag and note with a **lavender wash** rather than a black bar — the way Todoist's dark mode wears the same colour. See [What Changed vs Native Dark](#what-changed-vs-native-dark).

Lavender is a fork of [Dark Blue](https://github.com/beshoysabri/sn-dark-blue-theme): same stylesheet structure, same Inter setup, same GitHub Pages hosting. Through v2.5.1 it was Dark Blue's palette with the accent swapped; v2.6.0 gave it its own base. It keeps Dark Blue's version line, so the version history below is shared — v2.5.0 is the first Lavender release.

## Installation

1. Open the Standard Notes **desktop** app
2. Go to **Preferences** > **Plugins** > **Install Custom Plugin** (at the bottom of the page — older versions had it under **General** > **Advanced Settings**)
3. Paste the following URL:

```
https://beshoysabri.github.io/sn-lavender-theme/ext.json
```

4. Click **Install**
5. Select **Lavender** from the Appearance menu

There's a preview and a copy button at **[beshoysabri.github.io/sn-lavender-theme](https://beshoysabri.github.io/sn-lavender-theme)**.

Lavender has its own identifier, so it installs alongside Dark Blue rather than replacing it — switch between the two from the Appearance menu.

**Install from the desktop app, not the web app.** The web app's Content-Security-Policy only lets it fetch plugin links from Standard Notes' own servers and `raw.githubusercontent.com`, and even that one fails, because the request is sent with credentials and GitHub answers `Access-Control-Allow-Origin: *`. Pasting the link there gives *"Error downloading package details"* — for every self-hosted theme, Dark Blue included. Installed themes sync with your account, though, and the web app loads the stylesheet and fonts from Pages without complaint, so once it's installed on the desktop it shows up on the web too. Verified against app.standardnotes.com v3.203.0.

| Client | Colours | Inter |
|---|---|---|
| Web | yes | yes, downloaded automatically |
| Desktop | yes | install Inter on the machine — see below |
| Mobile | yes | install Inter on the device — works on iOS and Android |

### Everywhere except the web app, install Inter on the device

The desktop app sends `Content-Security-Policy: default-src 'self' blob:` with no `font-src`, so it refuses to download **any** webfont — from this repo, from a CDN, or inlined as a `data:` URI. No theme can ship a font file into it. Verified against the running app, not assumed.

What does work is a font already installed on the device. There's no download, so CSP has nothing to block — it's just a family-name lookup, and the stack is written so an installed copy is found automatically. The same trick works on mobile.

**Desktop**

1. Download Inter from [rsms.me/inter](https://rsms.me/inter/)
2. Install **both** `InterVariable.ttf` and `InterVariable-Italic.ttf` (inside `Desktop/` in the zip) — Font Book on macOS, right-click → Install on Windows. Skipping the italic leaves italics synthesised by slanting the roman rather than using Inter's real italic shapes.
3. Fully quit Standard Notes and reopen it; the system font list is read at launch

**Mobile** — install Inter as a system font (iOS needs a font-installer app that adds a configuration profile; Android varies by manufacturer), then restart Standard Notes. Confirmed working on both iOS and Android.

Skip this and the theme still works — you get the colours, and the text stays on the system font. That's a correct fallback, not a failure.

<details>
<summary>Alternative: jsDelivr</summary>

The theme is also reachable over jsDelivr:

```
https://cdn.jsdelivr.net/gh/beshoysabri/sn-lavender-theme@master/ext.json
```

Both origins serve the same files. GitHub Pages is the default because branch-pinned jsDelivr URLs are cached for roughly 12 hours, so a push doesn't show up until the cache expires or you purge it. Pages republishes on every push to `master`.

</details>

## Hosting

Pushing to `master` triggers `.github/workflows/pages.yml`, which verifies the theme before publishing — that `ext.json` and `package.json` agree on a version, that both woff2 files exist, that both `@font-face` sources are the absolute Pages URLs, that all **90** colour declarations still hash to the lavender palette's digest, that some rule actually applies `--sn-inter-font`, that the section 6 opt-ins are still commented out, and that braces balance in the comment-stripped `dist.css`. A failed check blocks the deploy rather than shipping a broken stylesheet.

The digest originally covered only the 51 `--sn-stylekit-*` names, which left 39 real colours — navigation, items column, editor, titlebar, text selection, popover — unguarded. It now covers every custom property except the three `--sn-inter-*` typography knobs.

Enable it once under **Settings → Pages → Source → GitHub Actions**.

## Color Palette

| Role | Hex | Preview |
|------|-----|---------|
| Background | `#1e1e1e` | ![1e1e1e](https://img.shields.io/badge/-1e1e1e-1e1e1e?style=flat-square) |
| Sidebar & surfaces | `#252525` | ![252525](https://img.shields.io/badge/-252525-252525?style=flat-square) |
| Border | `#2a2a2a` | ![2a2a2a](https://img.shields.io/badge/-2a2a2a-2a2a2a?style=flat-square) |
| Separator | `#333333` | ![333333](https://img.shields.io/badge/-333333-333333?style=flat-square) |
| Foreground | `#eeeeee` | ![eeeeee](https://img.shields.io/badge/-eeeeee-eeeeee?style=flat-square) |
| Accent (Lavender) | `#a79ef4` | ![a79ef4](https://img.shields.io/badge/-a79ef4-a79ef4?style=flat-square) |
| Accent, darkened | `#8a7ff0` | ![8a7ff0](https://img.shields.io/badge/-8a7ff0-8a7ff0?style=flat-square) |
| Selection wash | `#a79ef4` at 18% | ![373545](https://img.shields.io/badge/-373545-373545?style=flat-square) |
| Text selection | `#a79ef4` at 35% | ![4e4b69](https://img.shields.io/badge/-4e4b69-4e4b69?style=flat-square) |
| Text on accent | `#1e1e1e` | ![1e1e1e](https://img.shields.io/badge/-1e1e1e-1e1e1e?style=flat-square) |
| Success | `#2b9612` | ![2b9612](https://img.shields.io/badge/-2b9612-2b9612?style=flat-square) |
| Warning | `#cc8800` | ![cc8800](https://img.shields.io/badge/-cc8800-cc8800?style=flat-square) |
| Danger | `#f80324` | ![f80324](https://img.shields.io/badge/-f80324-f80324?style=flat-square) |

The two translucent rows are previewed as they render on the background.

## Typography

Since v2.3.0 the whole app is set in Inter v4.1 — sidebar, note list, menus and note text. The variable font, roman and italic, is bundled in `dist/fonts/` under the SIL Open Font License.

v2.2.0 scoped Inter to Super notes only. That left the rest of the UI on the system font, and — because of the CSP above — never actually loaded on Desktop at all.

Two details make it work where v2.2.0 didn't:

- **The `@font-face` sources are absolute, not relative.** Standard Notes inlines theme CSS instead of linking it, so a relative `url('fonts/…')` resolves against the app's own origin and 404s. v2.2.0 shipped that bug; the fonts never loaded in any client.
- **The family is set on elements, not through a variable.** Standard Notes doesn't read `--sn-stylekit-sans-serif-font` for its own chrome, so setting that variable changes nothing. `html, body, body *` is what actually reaches the UI.

Code keeps a monospace face. That rule is listed after the app-wide one so it wins at equal specificity, and it disables contextual alternates so `->` stays two characters where that matters.

Three variables at the top of `dist/dist.css` control it:

| Variable | Purpose |
|---|---|
| `--sn-inter-font` | The family stack. Inter has no Arabic or CJK glyphs, so those scripts fall through to the next family rather than rendering as boxes. |
| `--sn-inter-mono` | Code face. Defaults to whatever Standard Notes already uses. |
| `--sn-inter-features` | OpenType features. `cv05` gives lowercase `l` a tail so it stops looking like a capital `I`. Set to `normal` to disable. |

Inter's contextual alternates fuse `->` into a single `→` glyph. If the caret feels off by one when you arrow across it, section 6 has a block that turns ligatures back off — along with tighter heading tracking, roomier leading, tabular figures in tables, and a block that confines Inter to the editor again the way v2.2.0 did.

## Daily View

Standard Notes' Daily notebook borrows the app's `danger` token for today's date, the selected day, the entry tiles and both create-note buttons — so on a lavender theme they came out red. Since v2.4.0, section 4 of the stylesheet repaints those specific elements with the accent instead.

It's scoped deliberately rather than recolouring `--sn-stylekit-danger-color` wholesale, for two reasons: destructive controls should stay red, and the rules only *reference* the accent variables rather than declaring new ones — so the colour digest is unaffected.

Because they reference `--sn-stylekit-info-color` and friends, retuning the accent moves the Daily view with it automatically — including the dark text on today's date and the entry tiles.

## Selection

Standard Notes uses one colour for both hover and selection, in the two places that matter: `--navigation-item-selected-background-color` in the sidebar, and `--item-cell-selected-background-color` in the note list, which the app defines as the contrast background. Under native Dark both are near-black (`#0f1011` and `#000000`), so the selected tag and the selected note each became a black bar.

Since v2.6.0, section 5 keeps hover a neutral grey and gives the selected sidebar item and the selected note an 18% lavender wash, with the sidebar label in lavender (4.6:1 on the wash). Like the Daily view rules, they only *reference* variables, so the colour digest is unaffected — and they match Standard Notes' own class names, so they may need revisiting if the app restyles its sidebar or note list.

## What Changed vs Native Dark

The accent, the base it sits on, and the font. Through v2.5.1 only the accent family moved; v2.6.0 softened the base too:

- **Charcoal, not near-black.** Background `#0f1011` → `#1e1e1e`; sidebar and surfaces `#1c1d1e` → `#252525`; borders `#181a1b` → `#2a2a2a`; separators `#28292b` → `#333333`; menus are solid charcoal instead of 65%-transparent black.
- **Soft white.** Sidebar labels, section titles and note text `#ffffff` → `#eeeeee`, matching the rest of the UI — 14.4:1 on the base instead of 19.1:1.
- **In-between lavenders.** The accent backdrop is 18% instead of 6%, which was invisible on dark; text selection is a 35% lavender wash under light text (7.1:1) instead of a solid block; the scrollbar thumb is lavender at 40%.
- **Selection is a lavender wash, not a black bar.** See [Selection](#selection).

The purple-to-lavender swap applies to:

- Selected items and navigation highlights
- Links, buttons, and focus rings
- Text selection background
- Scrollbar thumb
- Note preview progress bar
- Component highlight color
- Titlebar hover state
- Super, plain-text and rich-text note icons, the selected note's left edge, and the note's editing-status pill (accessory tint 1)

That last one isn't the accent in name, but Standard Notes designs it to match: it's `#086dd6` natively, the same blue as the default accent, and the app pairs it with accent-tinted fills. Dark Blue gets the match for free; Lavender sets tint 1 to `#a79ef4` so no blue is left over. The other five accessory tints stay native.

The darkened shade used for hover states (`#8a7ff0`) keeps lavender's hue and drops its lightness by the same amount Dark Blue's `#086DD6` → `#065cb5` did.

**Text on the accent is dark.** Lavender is much lighter than the native purple or Dark Blue's blue: the near-white `#eeeeee` that native Dark puts on accent fills manages only 2.0:1 against `#a79ef4`, under even the 3:1 floor for large text. So `--sn-stylekit-info-contrast-color` is the background colour `#1e1e1e` instead, at 7.0:1 — primary buttons, the new-note button, badges, and the Daily view's date tiles and create-note buttons.

## Customization

Want a different lavender? Replace `a79ef4` in `dist/dist.css` with your preferred shade — without the `#`, so the translucent variants (`#a79ef42e`, `#a79ef459`, `#a79ef466`) follow it:

| Name | Hex |
|------|-----|
| **Lavender** | `#a79ef4` (default) |
| Catppuccin Lavender | `#b4befe` |
| Dracula Purple | `#bd93f9` |
| Material Deep Purple 200 | `#b39ddb` |
| Tailwind Violet 400 | `#a78bfa` |

All of these are light enough for the dark text-on-accent (6:1 or better). A mid-tone accent such as Dark Blue's `#086DD6` reads better with light text — set `--sn-stylekit-info-contrast-color` back to `#eeeeee` — and `--sn-stylekit-info-color-darkened` should move with whatever accent you pick.

If you publish your own copy, the Pages workflow refuses any colour change until `EXPECTED` in `.github/workflows/pages.yml` is updated to match; the failed run prints the new digest.

## License

Theme: MIT — see `LICENSE`.
Inter: SIL Open Font License 1.1 — see `LICENSE-3RD-PARTY`.
