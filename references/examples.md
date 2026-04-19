# Examples

Use these examples as starting points. Adapt names and values to the wallpaper instead of copying blindly.

## SceneScript: Smooth Vertical Idle Motion

```js
'use strict';

/**
 * @param {Vec3} value
 * @return {Vec3}
 */
export function update(value) {
  value.y = 500 + Math.sin(engine.runtime) * 100;
  return value;
}
```

Use when a layer needs a soft looping motion.

## SceneScript: Property-Driven Toggle

```js
'use strict';

let enabled = false;

export function update(value) {
  if (!enabled) {
    return value;
  }

  value.y = 500 + Math.sin(engine.runtime) * 40;
  return value;
}

export function applyUserProperties(changedUserProperties) {
  if (changedUserProperties.hasOwnProperty('enabled')) {
    enabled = changedUserProperties.enabled;
  }
}
```

Use when a scene wallpaper should expose a simple on/off behavior in user settings.

## Web Wallpaper: Central Settings Object

```js
var wallpaperSettings = {
  fps: 0,
  accentColor: 'rgb(255,255,255)',
  showClock: true
};

window.wallpaperPropertyListener = {
  applyUserProperties: function(properties) {
    if (properties.accentcolor) {
      var rgb = properties.accentcolor.value.split(' ').map(function(c) {
        return Math.ceil(c * 255);
      });
      wallpaperSettings.accentColor = 'rgb(' + rgb + ')';
    }

    if (properties.showclock) {
      wallpaperSettings.showClock = properties.showclock.value;
    }
  },
  applyGeneralProperties: function(properties) {
    if (properties.fps) {
      wallpaperSettings.fps = properties.fps;
    }
  }
};
```

Use when property events and render code need a shared state container.

## Web Wallpaper: Basic Audio Listener

```js
function wallpaperAudioListener(audioArray) {
  var bassLeft = Math.min(audioArray[0], 1);
  var bassRight = Math.min(audioArray[64], 1);
  var combinedBass = (bassLeft + bassRight) * 0.5;

  // Use combinedBass to drive scale, opacity, particles, or bar height
}

window.wallpaperRegisterAudioListener(wallpaperAudioListener);
```

Use when the wallpaper should respond to beats rather than render a full spectrum.

## Web Wallpaper: FPS-Limited Render Loop

```js
var wallpaperSettings = { fps: 0 };
var last = performance.now() / 1000;
var fpsThreshold = 0;

function run() {
  window.requestAnimationFrame(run);

  var now = performance.now() / 1000;
  var dt = Math.min(now - last, 1);
  last = now;

  if (wallpaperSettings.fps > 0) {
    fpsThreshold += dt;
    if (fpsThreshold < 1.0 / wallpaperSettings.fps) {
      return;
    }
    fpsThreshold -= 1.0 / wallpaperSettings.fps;
  }

  // Draw the wallpaper here
}

window.onload = function() {
  window.requestAnimationFrame(run);
};
```

Use when a web wallpaper has ongoing animation or canvas drawing.

## Non-Code Checklists

### Parallax checklist

- enable camera parallax
- keep mouse influence above zero
- tune each layer's parallax depth
- enlarge or oversize background layers to hide borders

### Puppet warp checklist

- start from a clean transparent cutout
- generate geometry
- place a stable main bone
- paint weights carefully around holes and thin parts
- animate mostly bone angles, not aggressive scaling or translation

### Shader checklist

- verify a built-in effect cannot solve the request first
- implement an effect shader, not a system shader replacement
- inspect translated shader code through the error view if compilation fails
