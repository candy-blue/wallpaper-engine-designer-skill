# Wallpaper Engine Web API

Use this file when a web wallpaper must integrate with Wallpaper Engine runtime events.

## wallpaperPropertyListener

Define it as a global object:

```js
window.wallpaperPropertyListener = {
  applyUserProperties: function(properties) {},
  applyGeneralProperties: function(properties) {},
  setPaused: function(isPaused) {}
};
```

Important:

- define it outside `window.onload`
- check whether each property exists before using it

## applyUserProperties

This fires:

- when the wallpaper loads
- whenever a user changes one of the wallpaper's properties

Only changed properties are included, so always guard each one:

```js
if (properties.customslider) {
  settings.speed = properties.customslider.value;
}
```

## applyGeneralProperties

Use this to read application-level settings, especially the FPS limit.

Typical use:

```js
if (properties.fps) {
  settings.fps = properties.fps;
}
```

## setPaused

Use when the wallpaper should explicitly react to pause and resume transitions.

This is optional, but useful for:

- pausing timers
- muting internal animation state
- skipping expensive work

## Directory Events

For `directory` properties in `fetchall` mode, use:

- `userDirectoryFilesAddedOrChanged`
- `userDirectoryFilesRemoved`

Do not expect `applyUserProperties` alone to manage the file list.

## Audio Listener

Register audio input directly:

```js
function wallpaperAudioListener(audioArray) {
  // Handle audio input here
}

window.wallpaperRegisterAudioListener(wallpaperAudioListener);
```

Rules:

- do not register it inside `window.onload`
- audio data arrives roughly 30 times per second
- clamp values because rare spikes above `1.0` can happen

## File And Directory Paths

When using file or directory-based assets, prepend file paths with `file:///`.

Example:

```js
imageElement.src = 'file:///' + properties.customimage.value;
```

## Color Conversion

Wallpaper Engine web color properties arrive as space-separated normalized components.

Convert them before using them in CSS:

```js
var rgb = properties.customcolor.value.split(' ').map(function(c) {
  return Math.ceil(c * 255);
});

var color = 'rgb(' + rgb + ')';
```

## FPS Integration

Use `requestAnimationFrame` for rendering and gate drawing with the user's configured FPS limit. This is the preferred pattern for canvas-heavy or animation-heavy wallpapers.
