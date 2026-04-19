---
name: wallpaper-engine-designer
description: Use when the task involves Wallpaper Engine scene wallpapers, web wallpapers, SceneScript, shader programming, user properties, particles, puppet warp, parallax, audio visualization, performance tuning, or Wallpaper Engine-specific implementation guidance. Choose scene or web first, then use the bundled references and examples in this skill repository before coding.
---

# Wallpaper Engine Designer

Use this skill for Wallpaper Engine work that needs product-specific guidance rather than generic game-dev, graphics, or web-dev advice.

## What This Skill Is For

Use it when the user wants to:

- build or debug a **scene wallpaper**
- build or debug a **web wallpaper**
- write **SceneScript**
- react to **user properties**
- add **audio visualization**
- implement **parallax** or **puppet warp**
- decide between **built-in effects**, **timeline**, **SceneScript**, **web JavaScript**, or **shaders**
- improve **performance** or prepare a wallpaper for **publishing**

This skill is meant to produce implementation guidance, not just a doc index.

## Bundled References

Start with the smallest relevant file:

- [references/scene-wallpapers.md](references/scene-wallpapers.md)
- [references/web-wallpapers.md](references/web-wallpapers.md)
- [references/scenescript.md](references/scenescript.md)
- [references/web-api.md](references/web-api.md)
- [references/examples.md](references/examples.md)
- [references/performance-and-publishing.md](references/performance-and-publishing.md)

Supplementary navigation files:

- [references/doc-paths.md](references/doc-paths.md)
- [references/task-recipes.md](references/task-recipes.md)

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
- Then read `references/scene-wallpapers.md`

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
- Then read `references/web-wallpapers.md`

## Core Workflow

1. Identify whether the user needs a scene wallpaper or a web wallpaper.
2. Pick the lightest-weight Wallpaper Engine mechanism that can solve the task.
3. Read only the smallest relevant bundled reference files.
4. Convert the references into concrete steps, code, or debugging guidance.
5. Name the exact Wallpaper Engine subsystem being used in the answer.

## Preferred Order Of Solutions

When several approaches could work, prefer them in this order:

1. Built-in editor features
2. User properties
3. Timeline animation
4. SceneScript for scene-logic needs
5. Web JavaScript for web wallpapers
6. Custom shaders only when built-in effects are not enough

## Read Order By Task

### If the user is building a scene wallpaper

1. Read [references/scene-wallpapers.md](references/scene-wallpapers.md)
2. If code is needed, read [references/scenescript.md](references/scenescript.md)
3. If the user asks for concrete patterns, read [references/examples.md](references/examples.md)
4. If optimization or release is involved, read [references/performance-and-publishing.md](references/performance-and-publishing.md)

### If the user is building a web wallpaper

1. Read [references/web-wallpapers.md](references/web-wallpapers.md)
2. Read [references/web-api.md](references/web-api.md) for Wallpaper Engine browser integration
3. If the user asks for concrete patterns, read [references/examples.md](references/examples.md)
4. If optimization is involved, read [references/performance-and-publishing.md](references/performance-and-publishing.md)

### If the user asks for “how should I do this?”

Read [references/task-recipes.md](references/task-recipes.md) first.

## Expected Output

When responding, prefer this structure:

1. Name the chosen subsystem: `scene`, `web`, `SceneScript`, `timeline`, `user properties`, `shader`, etc.
2. Explain the minimum viable approach.
3. Provide steps or code.
4. Call out Wallpaper Engine-specific caveats.

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

- Keep answers grounded in Wallpaper Engine terms instead of generic equivalents.
- Do not mix SceneScript guidance into web wallpaper code unless the user is building both systems.
- For web wallpapers, initialize `window.wallpaperPropertyListener` as a global object outside `window.onload`.
- For web audio visualizers, register `window.wallpaperRegisterAudioListener(...)` directly and not inside `window.onload`.
- For scene wallpapers, timeline is usually simpler than code for authored loops.
- Use Wallpaper Engine performance docs instead of generic browser or engine optimization advice.
- For shader work, prefer effect shaders. Do not advise replacing system shaders.

## Style Rules

- Be concrete and implementation-oriented.
- Prefer small working snippets over abstract explanations.
- Explain tradeoffs when choosing between timeline, SceneScript, web JavaScript, and shaders.
- If the request is ambiguous, infer `scene` vs `web` from the user's files, APIs, and terminology.
