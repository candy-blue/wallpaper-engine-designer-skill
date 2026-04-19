# SceneScript

Use this file when the wallpaper is a scene wallpaper and logic must be implemented with scripts.

## What SceneScript Is

SceneScript follows ECMAScript 2018 and behaves similarly to JavaScript, but it is focused on Wallpaper Engine scene objects instead of browser APIs.

## Core Globals

High-value globals:

- `engine`: runtime and general environment information
- `input`: mouse and input data
- `thisScene`: current scene
- `thisLayer`: current layer
- `thisObject`: current bound object
- `console`: logging for debugging
- `shared`: shared data between scripts

## Core Events

Most important events:

- `init`: run once when the object is created
- `update`: run every frame
- `destroy`: cleanup
- `resizeScreen`: respond to resolution changes
- `applyUserProperties`: react to user property changes and first load
- cursor events: `cursorEnter`, `cursorLeave`, `cursorMove`, `cursorDown`, `cursorUp`, `cursorClick`
- media events for playback, status, metadata, thumbnail, and timeline

## The Default Pattern

Most property-bound scripts revolve around `update(value)`.

Workflow:

1. `value` starts as the current property value
2. modify `value`
3. return `value`

The type of `value` depends on the property being scripted.

Examples:

- `String` for text
- `Vec3` for position-like properties

## Value Type Examples

### Text property

```js
'use strict';

/**
 * @param {String} value
 * @return {String}
 */
export function update(value) {
  return String(new Date().getSeconds());
}
```

### Position-like property

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

This sinusoidal pattern is usually better than an ever-increasing offset because it loops smoothly.

## User Properties In SceneScript

Use `applyUserProperties(changedUserProperties)` to react to property changes.

Important rule:

- the event only contains changed properties after the initial load
- always check whether a property exists before reading it

Recommended pattern:

```js
let enabled = false;

export function applyUserProperties(changedUserProperties) {
  if (changedUserProperties.hasOwnProperty('enabled')) {
    enabled = changedUserProperties.enabled;
  }
}
```

Then use that local variable inside `update()`.

## Debugging

Use `console.log()` when behavior is unclear.

Example:

```js
console.log(value.y);
```

But remove noisy logging before publishing because frequent logging can hurt performance.

## Good SceneScript Use Cases

- text clocks
- subtle procedural motion
- property-driven enable/disable logic
- cursor reactions
- media metadata display

## Bad SceneScript Use Cases

- simple authored looping transforms that belong in timeline animation
- effects that already exist as built-in editor effects

## Decision Tips

- If the user wants reusable logic across frames, use `update`.
- If the user wants to react to editor settings, use `applyUserProperties`.
- If multiple scripts need shared state, consider `shared`.
