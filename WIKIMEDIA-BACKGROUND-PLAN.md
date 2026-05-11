# Wikimedia + Background Controls Plan

This update turns the Advent Cut-Out Studio into a proper source-driven paper machine.

## Requested features

- Add a Random Wikimedia button.
- Pull a random Featured Picture from Wikimedia Commons.
- Put that image into the source drawer/bin so it can be cut like paper.
- Keep user photo uploads as cuttable sources.
- Let the user change the stage background color.
- Let the user upload a background image.
- Let the user remove the dot grid.

## Implementation notes

The Scriptable snippet uses `Request`, `ListWidget`, and `config`, which are iOS Scriptable-only APIs. In the browser version, the same idea needs to use `fetch`, DOM elements, `Image`, and a CORS-safe canvas flow.

The Wikimedia call can use:

```js
https://randomincategory.toolforge.org/Featured_pictures_on_Wikimedia_Commons?server=commons.wikimedia.org&type=file&debug=1
```

Then parse the redirect location and query the Commons API for a thumbnail:

```js
https://commons.wikimedia.org/w/api.php?action=query&titles=TITLE&prop=pageimages&format=json&pithumbsize=1200&origin=*
```

The image should be loaded with `crossOrigin = 'anonymous'` before drawing it to canvas, otherwise exported frames/GIFs can be blocked by a tainted canvas.

## UI direction

Sources should eventually include:

- Paper swatches
- Uploaded photos
- Random Wikimedia image
- Advent site image drawer
- Saved scraps
- Previous frames

The app should become a lean, mean, paper cut-out machine: one source area, one cut area, one stage, one timeline.
