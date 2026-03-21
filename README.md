# 🪵 Schepki Extensions — Remote Config

This repository is the **central control panel** for all Schepki browser extensions.

## What is this?

All Schepki extensions fetch `config.json` from this repository at startup. This allows instant updates to donation links, affiliate links, and promotional banners — **without submitting updates to the Chrome Web Store**.

## How to update links

1. Open `config.json` in this repository.
2. Click the **pencil icon** (Edit) in the top right.
3. Change the value you need (e.g., update the donation link).
4. Click **"Commit changes"** (green button).

That's it! All extensions will pick up the new values within minutes.

## Files

| File | Purpose |
|---|---|
| `config.json` | Remote Config — all links and settings for all extensions |
| `index.html` | Landing page (hosted on GitHub Pages) |
| `privacy.html` | Privacy Policy page (required by Chrome Web Store) |

## Privacy Policy URL

```
https://nikol-dev-tools.github.io/schepki-config/privacy.html
```

Use this URL when submitting extensions to the Chrome Web Store.
