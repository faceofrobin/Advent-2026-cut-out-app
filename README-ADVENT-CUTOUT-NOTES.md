# Advent Cut-Out Studio: Field Notes from the Paper Mine

## Correct file to preview right now

Preview this file first:

```text
index-new.html
```

That is the newest working cleaned prototype committed to the repo.

Current file roles:

```text
index.html      = old inherited Stop Motion Studio export
index-v1.html   = version marker / original-era snapshot note
index-new.html  = newest cleaned paper cut-out prototype
```

Once the file promotion is complete, `index-new.html` should become the new `index.html`, and the prior `index.html` should remain preserved as a versioned historical file.

---

## The Insane Back-and-Forth, Recorded for Posterity

This project immediately developed lore.

What happened:

1. The GitHub repo was found: `faceofrobin/Advent-2026-cut-out-app`.
2. At first, the repo appeared empty or inaccessible.
3. Then `index.html` appeared.
4. Then it vanished emotionally, but not technically.
5. Direct updates to `index.html` failed because GitHub rejected stale SHA values.
6. We tried again.
7. It failed again.
8. We created `index-v1.html` successfully.
9. That proved file creation worked better than file replacement.
10. We tried to update `README.md`.
11. That got weird too.
12. We created `index-new.html` successfully.
13. That file is now the known-good cleaned prototype.
14. The correct next step is to promote `index-new.html` to `index.html` once the connector, Codex, or GitHub UI cooperates.

The working rule from this point forward:

> Never trust one magical overwrite. Preserve versions. Make small commits. Keep the fossils.

---

## Versioning Rule

For this project:

```text
index.html      = current deployable version
index-v1.html   = old version / fossil
index-v2.html   = next fossil
index-v3.html   = next fossil after that
```

This is slightly redundant with Git history, but it is useful because the app is a single-file HTML artifact likely to be FTP uploaded and visually compared.

Git is the official record.
The version files are the museum display cases.

---

## Project Identity

This is not a sleek animation platform.

This is:

- construction paper stop motion
- digital scissors
- a craft table in a browser
- an Advent calendar that swallowed a GIF machine
- a school art room at midnight
- Terry Gilliam-adjacent collage energy
- a children’s museum kiosk with suspicious amounts of ambition
- a tiny paper theater for weird seasonal miracles

The app should stay tactile, playful, and slightly unstable in the charming way.

It should not become sterile.
It should not become corporate.
It should not become boring.

The correct design sentence is:

> A box of paper scraps with a camera button.

---

## What the App Should Become

The intended tool is a lean, mean paper cut-out machine.

Core loop:

1. Choose a paper, texture, uploaded image, or Advent image.
2. Draw around the shape.
3. Cut it out.
4. Store it in a drawer/bin.
5. Drag it onto the stage.
6. Move pieces around.
7. Capture frames.
8. Preview the animation.
9. Export GIF / PNG sequence / sprite sheet.

---

## Future Advent Site Integration

Target site:

```text
https://advent.faceofrobin.com/
```

Live extraction has not been performed in this repo session because live web browsing was not available through the assistant environment.

But the integration idea is absolutely possible.

The Advent site can become a source drawer for the cut-out app.

Future source drawers:

```text
Papers
Uploads
Advent Images
Saved Cutouts
Frames
Exports
```

### Best future architecture

Have `advent.faceofrobin.com` expose a JSON manifest of images:

```json
[
  {
    "title": "Day 1",
    "url": "https://advent.faceofrobin.com/images/day01.png",
    "day": 1,
    "category": "advent"
  }
]
```

Then the cut-out app can fetch that manifest and populate an `Advent` drawer.

### PHP option

If images live in a folder, use a PHP endpoint to scan the directory and return JSON.

Example idea:

```php
<?php
header('Content-Type: application/json');
$dir = $_SERVER['DOCUMENT_ROOT'] . '/images';
$base = 'https://advent.faceofrobin.com/images/';
$files = array_values(array_filter(scandir($dir), function($file) {
  return preg_match('/\.(png|jpg|jpeg|webp|gif)$/i', $file);
}));
echo json_encode(array_map(fn($file) => [
  'title' => pathinfo($file, PATHINFO_FILENAME),
  'url' => $base . rawurlencode($file)
], $files));
```

---

## CORS Warning

If the app draws images from `advent.faceofrobin.com` onto a canvas, browser security rules matter.

To export frames, GIFs, or PNGs, the canvas must not be tainted.

Use:

```js
const img = new Image();
img.crossOrigin = 'anonymous';
img.src = imageUrl;
```

And make sure the image server sends an appropriate header such as:

```text
Access-Control-Allow-Origin: *
```

or a stricter domain-specific version.

Same-domain hosting is easiest.

---

## Stop-Motion Capture Roadmap

Next major system:

- capture frame
- duplicate frame
- delete frame
- reorder frames
- onion skin previous frame
- preview playback
- export animated GIF
- export PNG sequence
- export sprite sheet

The old inherited `index.html` had a tiny custom GIF encoder. It may be reused, but a better long-term path may be a more robust browser encoder or a PNG-sequence export first.

---

## Recommended Next Commit

Promote the working prototype:

```text
copy index-new.html -> index.html
```

Then preserve the current old `index.html` as:

```text
index-v2.html
```

or rename the existing original-era marker if desired.

Because the connector has struggled with direct `index.html` replacement, this may be an ideal Codex task.

---

## Codex Recommendation

Yes, Codex may be the better tool for the direct file surgery.

Suggested Codex prompt:

```text
In the repository faceofrobin/Advent-2026-cut-out-app:
1. Preserve the current index.html as index-v2.html.
2. Replace index.html with the current contents of index-new.html.
3. Keep index-new.html for now.
4. Add or update README.md using README-ADVENT-CUTOUT-NOTES.md as the source notes.
5. Do not remove index-v1.html.
6. Commit the changes with a clear message.
```

---

## Final Project Description

Advent Cut-Out Studio is a browser-based paper-cutout animation toy.

It turns color swatches, uploaded images, and eventually Advent calendar artwork into draggable stop-motion pieces.

It should stay weird.
It should stay tactile.
It should stay handmade.

It should always feel like someone dumped a pile of paper scraps onto the internet and handed the scraps a camera.
