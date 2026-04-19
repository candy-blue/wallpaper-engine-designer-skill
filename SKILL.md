---
name: wallpaper-engine-designer
description: Use when the task involves Wallpaper Engine scene wallpapers, web wallpapers, SceneScript, shader programming, user properties, particles, puppet warp, parallax, audio visualization, or Wallpaper Engine-specific implementation guidance. Choose scene or web first, then use the bundled reference files in this skill repository before coding.
---

# Wallpaper Engine Designer

Use this skill for Wallpaper Engine work that needs product-specific guidance rather than generic game-dev or web-dev advice.

## Bundled References

- Read [references/doc-paths.md](references/doc-paths.md) for the doc structure and entry points
- Read [references/task-recipes.md](references/task-recipes.md) for task-to-doc routing
- These files are part of this skill repository, so do not depend on any local filesystem path

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

- `scene/overview`
- `scene/first/gettingstarted`

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

- `web/overview`
- `web/first/gettingstarted`

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

## Reference Strategy

- Use `references/doc-paths.md` when you need a map of the documentation tree
- Use `references/task-recipes.md` when the user describes a goal like "music reactive wallpaper" or "custom property"
- Keep answers grounded in Wallpaper Engine terms: scene, web, SceneScript, timeline, user properties, shader, puppet warp, parallax

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
