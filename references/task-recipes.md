# Wallpaper Engine Task Recipes

## Build a first scene wallpaper

Read:

- `scene/first/gettingstarted`
- `scene/first/effects`
- `scene/first/assets`
- `scene/first/properties`
- `scene/first/publishing`

## Add editor-side customization

Read:

- `scene/userproperties/overview`
- The specific property type page
- `scene/scenescript/introduction` if code needs to react to properties

## Choose between timeline and SceneScript

Read:

- `scene/timeline/introduction`
- `scene/scenescript/introduction`

Guideline:

- Use timeline for simple authored loops
- Use SceneScript for cursor, audio, time, media, or property-driven behavior

## Write SceneScript

Read:

- `scene/scenescript/introduction`
- `scene/scenescript/tutorials`
- `scene/scenescript/reference`
- The matching `reference/class`, `reference/event`, or `reference/module` page

## Add music response

Scene wallpaper:

- `scene/audiovisualizer/overview`
- `scene/audiovisualizer/albumcover`
- `scene/audiovisualizer/mediainformation`

Web wallpaper:

- `web/audio/visualizer`
- `web/audio/media`

## Build a web wallpaper

Read:

- `web/overview`
- `web/first/gettingstarted`
- `web/customization/properties`
- `web/api/propertylistener`

Important:

- Keep `window.wallpaperPropertyListener` global and outside `window.onload`

## Add Wallpaper Engine web APIs

Read:

- User properties: `web/api/propertylistener`
- Audio: `web/audio/visualizer`
- RGB: `web/api/rgb`
- iCUE: `web/api/icue`
- FPS limiting: `web/performance/fps`

## Create a custom visual effect

Read in this order:

1. `scene/effects/effect/*`
2. `scene/shader/overview`
3. `scene/shader/tutorials/desaturation`

Use shader programming only when built-in effects cannot cover the request.

## Character deformation and animation

Read:

- `scene/puppet-warp/introduction`
- `scene/puppet-warp/charactersheet`
- `scene/puppet-warp/animationmixing`
- `scene/puppet-warp/inversekinematics`
- `scene/puppet-warp/attachments`
- `scene/puppet-warp/blendshapes`

## Mouse depth and layered movement

Read:

- `scene/parallax/introduction`
- `scene/parallax/depthparallax`
- `scene/parallax/oversized`

## Optimize and publish

Read:

- `scene/performance/resolution`
- `scene/performance/texture`
- `web/performance/fps`
- `scene/first/publishing`
