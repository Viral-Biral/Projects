# CAD Portfolio Site — Setup Guide

A single self-contained page (`index.html`) that shows your CAD projects as
interactive 3D models, hosted for free on GitHub Pages. No build tools, no
server — just static files.

## 1. Put it on GitHub

1. Create a **new public repository** on GitHub.
   - If you want it at `https://yourusername.github.io` (no extra path),
     name the repo exactly `yourusername.github.io`.
   - Any other name works too — it'll live at
     `https://yourusername.github.io/repo-name`.
2. Upload `index.html` to the root of the repo (drag-and-drop on the GitHub
   web UI works fine, or `git add` / `git commit` / `git push` if you're
   comfortable with git).
3. Create a folder called `models/` in the repo — this is where your `.glb`
   files will live.

## 2. Turn on GitHub Pages

1. In the repo, go to **Settings → Pages**.
2. Under "Build and deployment," set **Source** to `Deploy from a branch`.
3. Set **Branch** to `main` (or `master`) and folder to `/ (root)`. Save.
4. Wait about a minute, then visit the URL GitHub shows you at the top of
   that same Pages settings screen.

Every time you push a change, the live site updates automatically within a
minute or two.

## 3. Convert a SolidWorks part to a file the browser can show

The page uses `<model-viewer>`, which reads **.glb** or **.gltf** files —
not native `.sldprt` files. You need one conversion step first.

**Easiest, no install required:**
1. In SolidWorks: `File → Save As → STEP (*.step)`.
2. Open [3dviewer.net](https://3dviewer.net) in a browser and drag your
   `.step` file in — it opens directly, no account needed.
3. Use its export option to save as `.glb`.
4. Drop the `.glb` file into your repo's `models/` folder.

**More control (materials, smaller file size):** import the STEP file into
free tools like [FreeCAD](https://www.freecad.org) or
[Blender](https://www.blender.org) and export from there as glTF/GLB —
useful if a model looks too dark, too shiny, or too heavy on 3dviewer.net's
default export.

Either way, keep an eye on file size — anything under ~15 MB loads quickly;
much bigger than that and simplify the mesh first (most CAD packages have a
"reduce triangle count" or tessellation-quality setting on STEP/STL export).

## 4. Swap in your own project

Each project is one `<section class="sheet">` block in `index.html`. To
replace a sample:

1. Change the `src` on the `<model-viewer>` tag to
   `models/your-file.glb` (a relative path — no need for the full URL
   once it's in your own repo).
2. Update the `alt` text, heading, description, and the small metadata
   table underneath.
3. Update `data-title` on the `<section>` — that's what feeds the bottom
   title-block bar.

To add a fourth, fifth, etc. project, copy an entire `<section class="sheet">`
block, paste it above the empty "Sheet 03" slot, and give it the next
`data-sheet` number.

## 5. Personalize

- Swap "Your Name" in the `<h1>` and the title block.
- Point the email/LinkedIn/GitHub/GrabCAD links in the header at your
  actual profiles (or delete the ones you don't want).
- Change the `<title>` and the `<meta name="description">` tag near the
  top — that's what shows up in search results and link previews.

That's the whole loop: STEP → glb → drop in `/models` → point a tag at it →
push. Once it's live, the same link goes straight on your CV.
