# Jellexiglass

A dark Jellyfin theme with Plex-style layout, amber accents, and light glass effects.

Built around Jellyfin 10.11.9.

## Install

Add this in **Dashboard > Branding > Custom CSS**:

```css
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/theme.css");
```

Save, then hard refresh Jellyfin.

If jsDelivr serves an old copy, purge the CDN cache:

```text
https://purge.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/theme.css
```

Then bump the query string:

```css
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/theme.css?v=2");
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
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/theme.css");
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/disable-static-drawer.css");
```

## Notes

- Use Jellyfin's dark theme.
- The web app works best.
- GitHub raw URLs are not recommended for imports because they are served as plain text.
- For a stable install, pin the import to a commit hash instead of `@main`.
