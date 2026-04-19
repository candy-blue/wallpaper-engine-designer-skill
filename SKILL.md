---
name: wallpaper-engine-designer
description: Use when the task involves Wallpaper Engine scene wallpapers, web wallpapers, SceneScript, shader programming, user properties, particles, puppet warp, parallax, audio visualization, or Wallpaper Engine-specific implementation guidance. Read the local docs mirror at D:\Project\wallpaper-engine-docs, choose scene or web first, then use the matching documentation path before coding.
---

# Wallpaper Engine Designer

Use this skill for Wallpaper Engine work that needs product-specific guidance rather than generic game-dev or web-dev advice.

## Docs Root

- Local mirror: `D:\Project\wallpaper-engine-docs`
- Prefer Chinese docs under `D:\Project\wallpaper-engine-docs\docs\zh`
- Fall back to English docs under `D:\Project\wallpaper-engine-docs\docs\en` when the Chinese page is missing or incomplete

## First Decision

Decide the wallpaper type before doing anything else.

- **Scene wallpaper**: built in the Wallpaper Engine editor from images, videos, models, effects, timeline, particles, puppet warp, parallax, SceneScript, lighting, and shaders.
- **Web wallpaper**: built with HTML, CSS, and JavaScript, then connected to Wallpaper Engine web APIs.

## Routing

### Scene wallpaper

Use the scene docs when the request mentions:

- scene wallpaper
- Wallpaper Engine editor
- SceneScript
- timeline
- effects
- particles
- puppet warp
- parallax
- user properties in the editor
- 3D models
- lighting
- shader programming

Start here:

- `D:\Project\wallpaper-engine-docs\docs\zh\scene\overview.md`
- `D:\Project\wallpaper-engine-docs\docs\zh\scene\first\gettingstarted.md`

### Web wallpaper

Use the web docs when the request mentions:

- web wallpaper
- HTML
- CSS
- JavaScript
- canvas
- DOM
- `window.wallpaperPropertyListener`
- `window.wallpaperRegisterAudioListener`
- Wallpaper Engine web APIs

Start here:

- `D:\Project\wallpaper-engine-docs\docs\zh\web\overview.md`
- `D:\Project\wallpaper-engine-docs\docs\zh\web\first\gettingstarted.md`

## Core Workflow

1. Identify whether the user needs a scene wallpaper or a web wallpaper.
2. Prefer built-in Wallpaper Engine mechanisms before custom code.
3. Read only the smallest relevant doc set.
4. Convert the docs into concrete steps, code, or debugging guidance.
5. Name the exact Wallpaper Engine subsystem being used in the answer.

## Preferred Order Of Solutions

When several approaches could work, prefer them in this order:

1. Built-in editor features
2. User properties
3. Timeline animation
4. SceneScript for scene-logic needs
5. Web JavaScript for web wallpapers
6. Custom shaders only when built-in effects are not enough

## Scene Doc Map

- First wallpaper:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\first\gettingstarted.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\first\effects.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\first\assets.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\first\properties.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\first\publishing.md`
- Effects:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\effects\introduction.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\effects\overview.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\effects\effect\*.md`
- User properties:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\userproperties\overview.md`
  `color.md`
  `slider.md`
  `checkbox.md`
  `combo.md`
  `text.md`
  `texture.md`
- Audio visualizer:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\audiovisualizer\overview.md`
- Timeline:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\timeline\introduction.md`
- Image preparation:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\image-preparation\foreground-separation.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\image-preparation\character-sheet.md`
- Particles:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\particles\introduction.md`
- Puppet warp:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\puppet-warp\introduction.md`
- Parallax:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\parallax\introduction.md`
- SceneScript:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\scenescript\introduction.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\scenescript\tutorials.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\scenescript\reference.md`
- Models:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\models\introduction.md`
- Shaders:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\shader\overview.md`
- Lighting:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\lighting\introduction.md`
- Performance:
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\performance\resolution.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\scene\performance\texture.md`

## Web Doc Map

- Overview:
  `D:\Project\wallpaper-engine-docs\docs\zh\web\overview.md`
- Getting started:
  `D:\Project\wallpaper-engine-docs\docs\zh\web\first\gettingstarted.md`
- Custom properties:
  `D:\Project\wallpaper-engine-docs\docs\zh\web\customization\properties.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\web\customization\displaycondition.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\web\customization\localization.md`
- Property listener API:
  `D:\Project\wallpaper-engine-docs\docs\zh\web\api\propertylistener.md`
- Audio APIs:
  `D:\Project\wallpaper-engine-docs\docs\zh\web\audio\visualizer.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\web\audio\media.md`
- RGB APIs:
  `D:\Project\wallpaper-engine-docs\docs\zh\web\api\rgb.md`
  `D:\Project\wallpaper-engine-docs\docs\zh\web\api\icue.md`
- Performance:
  `D:\Project\wallpaper-engine-docs\docs\zh\web\performance\fps.md`
- Debugging:
  `D:\Project\wallpaper-engine-docs\docs\zh\web\debug\debug.md`

## Decision Rules

- For simple looping motion in scene wallpapers, prefer timeline before SceneScript.
- For scene logic driven by cursor, audio, current time, media data, or user properties, use SceneScript.
- For web wallpapers, use JavaScript plus Wallpaper Engine web APIs.
- For “customizable wallpaper”, go to user properties first.
- For “music reactive wallpaper”, go to audio visualizer docs first.
- For “mouse depth movement”, go to parallax docs first.
- For “character deformation” or Live2D-like motion, go to puppet warp docs first.
- For custom visual effects, inspect built-in effects before shader programming.

## Product-Specific Caveats

- Do not mix SceneScript guidance into web wallpaper code unless the user is building both systems.
- For web wallpapers, initialize `window.wallpaperPropertyListener` as a global object outside `window.onload`.
- For web audio visualizers, register `window.wallpaperRegisterAudioListener(...)` directly and not inside `window.onload`.
- For scene wallpapers, timeline is usually simpler than code for authored loops.
- Use Wallpaper Engine performance docs instead of generic browser or engine optimization advice.

## What To Deliver

When responding, provide:

1. The chosen Wallpaper Engine subsystem
2. The minimum viable implementation path
3. Concrete steps or code
4. Any Wallpaper Engine-specific caveats

If the request is ambiguous, infer `scene` vs `web` from the user's files, APIs, and terminology.
