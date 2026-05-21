# Advent Cut-Out Studio

Advent Cut-Out Studio is a delightfully overengineered paper cutout animation laboratory.
It is a digital recreation of the magic that occurred many years ago while creating the John, Chris, Adam, and Robin advent calendar, now rebuilt as a stop-motion workbench for paper scraps, found pictures, and suspiciously ambitious GIF plans.

> THIS DIDN’T WORK.
> THEN IT SORT OF WORKED.
> THEN IT BROKE AGAIN.
> THEN IT BECAME THE PROJECT.

## Versioning System

`index.html` is always the latest working bench. Before changing it, archive the current copy as the next numbered `index-vN.html` file: inspect the highest existing archive number, rename the current `index.html` to the next one, and create a new `index.html` for the new experiment.

That system is half release trail and half lab notebook. It keeps old tables intact while the newest one gains sharper scissors.

## Stop-Motion Workflow

1. Pick paper or search Wikimedia Commons for an image source.
2. Draw a freehand loop around the part worth keeping, or use the whole image.
3. Tap a cutout in the bin to place it on the stage.
4. Drag it into place, pull corner handles to scale it, and turn the rotation handle for a new pose.
5. Capture frames as the pose changes across the timeline.
6. Export the current placeholder PNG while the full animated GIF encoder is still fermenting.

## Cutting System

Papers are procedural paper sources with a little noisy texture. Wikimedia Commons results open on the same cutting table so outside media follows the same ritual: draw a shape, clip the source through that path, preserve transparent regions, and trim away transparent edges before the cutout joins the bin.

The Wikimedia integration uses the Commons API search flow and thumbnails for browsing. Clicking a result loads the image as a canvas-safe cutout source, so found media can become animation material instead of a stranded reference picture.

## Stage Transforms

Every placed cutout is a transformable stage object with its own canvas, position, size, rotation, scale, and selection state. The stage renders those objects through canvas translation, rotation, and scale transforms. Selected objects show a bounding box, four scaling handles, and a rotation handle built for both pointer and touch work.

The stage can also wear a chosen background color, an uploaded background image, and optional alignment dots. That is the sensible engineering part. The less sensible part is how quickly one paper mitten becomes a complete dramatic production.

## Future Plans

The obvious next machine is a real animated GIF encoder. After that: richer frame editing, animation playback controls, duplicate and layer commands, reusable cutout collections, and enough timeline niceties to make long stop-motion sessions feel deliberate instead of heroic.
