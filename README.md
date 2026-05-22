# Jellexiglass

A dark Jellyfin theme with Plex-style layout, amber accents, and light glass effects.

Built around Jellyfin 10.11.9.

## Install

Add this in **Dashboard > Branding > Custom CSS**:

```css
@import url("https://landmine-1252.github.io/jellexiglass/theme.css");
```

Save, then hard refresh Jellyfin.

If the browser keeps an old copy, bump the query string:

```css
@import url("https://landmine-1252.github.io/jellexiglass/theme.css?v=20260521");
```

## Local Testing

From this folder:

```bash
python3 -m http.server 8080
```

Use this in Jellyfin:

```css
@import url("http://127.0.0.1:8080/theme.css?v=1");
```

If you are testing from another device, replace `127.0.0.1` with your computer's LAN IP.

## Optional

Use Jellyfin's normal collapsible drawer instead of the static sidebar:

```css
@import url("https://landmine-1252.github.io/jellexiglass/theme.css");
@import url("https://landmine-1252.github.io/jellexiglass/disable-static-drawer.css");
```

## Notes

- Use Jellyfin's dark theme.
- The web app works best.
- GitHub raw URLs are not recommended for imports because they are served as plain text.
- GitHub Pages may take a minute or two to update after pushing changes.
