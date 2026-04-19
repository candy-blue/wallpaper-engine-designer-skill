# Web Wallpapers

Use this file when the wallpaper is built with HTML, CSS, and JavaScript.

## Mental Model

A web wallpaper is a browser-based app running inside Wallpaper Engine. Generic web knowledge still applies, but Wallpaper Engine adds its own APIs for:

- user properties
- general app settings such as FPS limit
- audio visualization
- RGB integrations
- directory and file imports

## When Web Is The Right Choice

Use a web wallpaper when the user wants:

- DOM-based UI or layout
- canvas rendering
- HTML/CSS animation
- custom JavaScript architecture
- browser-style asset handling
- richer procedural interfaces than the editor offers

Do not use SceneScript for a web wallpaper. Use JavaScript plus Wallpaper Engine web APIs.

## Core Rules

- Initialize `window.wallpaperPropertyListener` as a global object.
- Do not define it inside `window.onload`.
- Register `window.wallpaperRegisterAudioListener(...)` directly, not inside `window.onload`.
- Use `requestAnimationFrame` for animation work.
- Apply the user's Wallpaper Engine FPS limit instead of inventing your own separate setting unless necessary.

## Property Types

Web wallpapers can expose these property types:

- `color`
- `slider`
- `bool`
- `combo`
- `textinput`
- `file`
- `directory`

Use them for user-facing customization in the Installed tab.

## Practical Guidance

### Color properties

Wallpaper Engine color values arrive as normalized floats like:

```text
1.0 0.1 0.25
```

Convert them to `0-255` values before using them in CSS or canvas APIs.

### File properties

File values need a `file:///` prefix before the embedded browser can read them.

Use cases:

- custom background image
- user-selected video
- optional avatar or album art source

Always plan a fallback state if the user clears the file.

### Directory properties

Use `directory` only if the wallpaper truly needs many files.

Modes:

- `ondemand`: request one random file at a time
- `fetchall`: listen for add/remove events and manage a file list yourself

Do not eagerly load an unlimited number of user files.

## Audio Visualizers

Wallpaper Engine sends 128 audio values:

- `0-63`: left channel
- `64-127`: right channel

Low indices are bass-heavy; higher indices are treble-heavy.

Volume values are usually between `0.0` and `1.0`, but can spike higher, so clamp with `Math.min(value, 1)`.

If you use audio, make sure the wallpaper actually registers the listener so Wallpaper Engine knows audio processing is required.

## Architecture Advice

For most web wallpapers, keep three layers of state:

1. user settings
2. runtime signals such as audio or pause state
3. render loop state

This keeps `applyUserProperties`, `applyGeneralProperties`, audio callbacks, and rendering logic from getting tangled together.

## Common Mistakes

- putting Wallpaper Engine API setup inside `window.onload`
- forgetting to check whether a property exists in `applyUserProperties`
- using file paths without the `file:///` prefix
- ignoring the FPS limit for heavy canvas animations
- assuming directory properties behave like normal scalar properties
