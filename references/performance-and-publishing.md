# Performance And Publishing

Use this file when the user asks about optimization, memory usage, FPS limiting, packaging, or Workshop release.

## Scene Wallpaper Performance

### Texture memory budget

Practical guidance from the docs:

- around `300 MB` VRAM usage is a good target
- below `500 MB` is usually acceptable
- going too high can make some desktops unstable or sluggish

Use the editor statistics view to inspect active texture memory.

### Keep textures small

- keep background resolution close to real target needs
- crop imported layers to the smallest useful size
- remove unnecessary padding if the layer will not use effects that extend beyond its bounds

### Texture compression

Wallpaper Engine can use compressed formats such as `DXT5` and `DXT1`.

Tradeoff:

- much lower VRAM usage
- some quality loss

In many practical wallpapers, the visual loss is small compared with the performance gain.

### Power-of-two padding

Compressed textures are padded to power-of-two dimensions. This can waste memory.

Example pattern:

- a `1920 x 1080` image may pad to `2048 x 2048`
- reducing one axis strategically can lower waste significantly

Always re-check project resolution after these optimizations so the wallpaper is not cropped incorrectly.

## Web Wallpaper Performance

### Respect the global FPS limit

Use `applyGeneralProperties` to read the user's FPS setting and throttle the render loop with `requestAnimationFrame`.

This should be the default optimization pattern for animated web wallpapers.

### Avoid unnecessary work

- pause expensive updates when possible
- clamp audio values
- avoid loading too many files from directory properties at once

## Publishing

### Before publishing

- remove debug logging
- verify the wallpaper behaves correctly in preview and on desktop
- confirm user properties are named clearly
- test fallback behavior for optional files and directories

### Important backup rule

Publishing to the Workshop is not a backup for project files.

If the user needs to keep editing the wallpaper later, project files still need to be backed up separately.

### Preview assets

Wallpaper Engine supports static previews and GIF previews.

Useful preview guidance:

- GIF previews work best at small sizes
- `128x128` is the ideal preview size for in-app use
- keep GIFs lightweight

### Updating an existing wallpaper

Re-publishing updates the existing Workshop item rather than creating a brand new one, but propagation can take some time.
