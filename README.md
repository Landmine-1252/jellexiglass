# Jellexiglass

Jellexiglass is a Jellyfin custom CSS theme inspired by Plex's dark cinema UI and Apple's Liquid Glass visual style. It uses amber accents, translucent panels, saturated blur, rounded media cards, and a Plex-like desktop side rail.

Built for Jellyfin 10.11.9.

## Install

1. Sign in to Jellyfin with an admin account.
2. Open **Dashboard**.
3. Go to **Settings** and find **Custom Style** / **Custom CSS**. In some Jellyfin builds this may appear under **Branding**.
4. Paste this import:

```css
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/theme.css");
```

5. Save, then hard-refresh Jellyfin.

The desktop side rail is static by default. To use Jellyfin's normal collapsible drawer instead, import this override after the main theme:

```css
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/theme.css");
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/disable-static-drawer.css");
```

The source file is here:

```text
https://raw.githubusercontent.com/Landmine-1252/jellexiglass/refs/heads/main/theme.css
```

Use the jsDelivr URL for the Jellyfin import. The raw GitHub URL is useful for viewing the file, but it is served as plain text and may be rejected by browsers as a stylesheet.

## Recommended Jellyfin Settings

For the intended look:

- Use Jellyfin's dark theme.
- Enable backdrops in your Jellyfin display settings.
- Use a modern browser or Jellyfin client with `backdrop-filter` support for the glass effects.

Custom CSS support varies by Jellyfin client. The web app and desktop-style browser clients usually work best.

## Update

If you use the `@main` import, updates are pulled from the main branch:

```css
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/theme.css");
```

CDN and browser caches may take a little time to refresh. If you need a stable install that does not change automatically, pin the import to a specific commit:

```css
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@COMMIT_HASH/theme.css");
```

## Local Testing

You do not need to publish changes to test them.

Option 1: paste the CSS directly into Jellyfin's Custom CSS box. This is the simplest way to test one file.

Option 2: serve this folder locally and import the local files.

From the theme folder, run:

```bash
python3 -m http.server 8080
```

Then use this in Jellyfin Custom CSS:

```css
@import url("http://127.0.0.1:8080/theme.css");
```

To test the collapsible-drawer override too:

```css
@import url("http://127.0.0.1:8080/theme.css");
@import url("http://127.0.0.1:8080/disable-static-drawer.css");
```

Notes:

- If you open Jellyfin from another device, `127.0.0.1` points to that device, not your development machine. Use your development machine's LAN IP instead, for example `http://192.168.1.50:8080/theme.css`.
- If your Jellyfin page is loaded over HTTPS, the browser may block an HTTP stylesheet as mixed content. For local theme work, use Jellyfin over local HTTP or serve the test CSS over HTTPS.
- Hard-refresh after edits. Browser caching can make CSS changes look like they did not apply.

## Customize

You can override theme variables below the import in Jellyfin's Custom CSS box.

Example: change the Plex-style amber accent:

```css
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/theme.css");

:root {
    --plg-accent-rgb: 0, 164, 220;
    --plg-accent: rgb(var(--plg-accent-rgb));
    --plg-accent-strong: #28c7ff;
}
```

Example: change the desktop side rail width:

```css
@import url("https://cdn.jsdelivr.net/gh/Landmine-1252/jellexiglass@main/theme.css");

:root {
    --plg-drawer-width: 220px;
}
```

## Troubleshooting

If the theme does not appear:

- Confirm the Custom CSS field contains the jsDelivr `@import` line.
- Hard-refresh the Jellyfin page.
- Clear your browser cache.
- Make sure the Jellyfin user is using the dark theme.
- Try the Jellyfin web app in a modern Chromium, Firefox, or Safari browser.

If the glass effect looks flat, the browser or client may not support `backdrop-filter`. The theme includes fallbacks, but the full Liquid Glass effect needs blur support.
