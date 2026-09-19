# Latency: tap a colour, see the swatch update

Image generation takes several seconds. A colour tap cannot wait.

**Rule:** changing colour is instant (tint or Pillow). Changing stitch, yarn weight, or fiber may take seconds.

## Four moves

**1. Show something immediately.**  
Pillow already draws a stitch-shaped, hex-correct placeholder in tens of milliseconds. Use that first. If we already have a saved photo for this spec, show that instead.

**2. Colour tap = recolour, never regenerate.**  
Keep the same fabric structure. Run `apply_color_tint` (Assignment B, cell 10) — or redraw the Pillow texture in the new hex. Do not call DALL·E for a colour change.

**3. Pre-generate and cache the common set.**  
Overnight: popular stitches × yarn weights × 8–12 brand colours. Store them under the same spec hash we use in the notebook. In the app, that hash is a CDN/Redis lookup. When the user opens a project, prefetch this stitch × the palette they are browsing.

**4. Nicer image in the background.**  
Queue at most one high-quality job per *structure*, not per colour. Keep the placeholder on screen; swap when ready. If the user changes stitch, cancel the old job. Use a faster/cheaper image model only for a new structure (or a “high quality” toggle). Colour taps never hit the image API.

## What the user feels

- Tap colour — paint-chip fast, no spinner.
- Change stitch — placeholder now, optional upgrade later.
- Popular combo — already on disk/CDN.
- Rare combo — placeholder now, one job in the queue, they keep planning.

If colour taps are still slow, we remove live generation from that path entirely. That is this design, not a backup plan.
