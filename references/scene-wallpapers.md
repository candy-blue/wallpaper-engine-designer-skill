# Scene Wallpapers

Use this file when the task is being solved inside the Wallpaper Engine editor.

## Mental Model

A scene wallpaper is usually assembled from imported layers and editor-side systems:

- image layers
- text layers
- sound layers
- video textures
- built-in effects
- timeline animation
- user properties
- SceneScript
- particles
- parallax
- puppet warp
- lighting and reflections
- 3D models

The best solution is usually the least programmable one that still works.

## Choose The Right Tool

### Built-in effects

Use when:

- the user wants visual motion or distortion
- the effect already exists in Wallpaper Engine
- the result can be authored by tweaking parameters

Examples:

- shake
- blur
- bloom
- chromatic aberration
- water ripple
- pulse
- transform

Use effects before shaders.

### Timeline animation

Use when:

- the user wants a looped motion
- the motion is keyframe-driven
- the behavior is predictable and not data-driven

Good fits:

- idle movement
- breathing
- periodic transforms
- opacity fades
- repeating animation clips

Prefer timeline before SceneScript for authored loops.

### User properties

Use when:

- the wallpaper should be configurable from the Installed tab
- the user needs toggles, sliders, colors, dropdowns, text, or texture replacement

Scene wallpaper property types:

- `color`
- `slider`
- `bool`
- `combo`
- `textinput`
- `texture`

Use display conditions to hide secondary options until a parent option is enabled.

Typical condition examples:

```js
show_clock.value == true
```

```js
mode.value == "advanced"
```

### SceneScript

Use when:

- behavior depends on cursor, time, audio, media, or user properties
- the value must be recomputed continuously
- multiple scene objects need shared logic

SceneScript is the right tool for:

- clocks
- cursor reactions
- property-driven color or motion
- media-driven text or album art logic
- lightweight procedural animation

### Parallax

Use when:

- the user wants mouse-following depth
- the wallpaper is primarily layered 2D art

Important rules:

- enable camera parallax at the scene level
- keep mouse influence non-zero
- tune per-layer parallax depth
- scale or oversize background layers so borders never show
- set one axis to `0` if the motion should be only horizontal or vertical

### Puppet warp

Use when:

- the subject is a character or articulated object
- there is a clean transparent cutout
- the user can spend time on mesh, bones, weights, and animation

Puppet warp is usually not the first choice for simple motion. If shake, sway, or timeline can solve it, prefer those first.

### Shaders

Use when:

- built-in effects cannot produce the requested look
- the user explicitly wants a custom effect shader
- the user already has shader knowledge

Important rule:

- effect shaders are the supported path
- do not replace system shaders such as the particle shader

## High-Value Patterns

### Character wallpaper

Typical stack:

1. clean cutout
2. background cleanup
3. parallax or subtle effects
4. optional puppet warp for body motion
5. user properties for toggles and strength

### Music reactive scene wallpaper

Typical stack:

1. scene audio/media features
2. user properties for sensitivity or mode
3. SceneScript only if built-in behavior is not enough

### Polished static illustration

Typical stack:

1. slight parallax
2. a few small effects
3. timeline-based idle movement
4. optional color or visibility properties

## Common Mistakes

- using SceneScript for motion that should be timeline animation
- using puppet warp on artwork that is not properly cut out
- forgetting to oversize parallax backgrounds
- exposing too many user properties at once
- reaching for shaders when built-in effects already solve the problem
