# Knitting Patterns

Loop topology. Yarn snakes holding hands in organized chaos.

This repository documents knitted textile structures as **procedural graph systems** — rows of interlocking loops where each stitch is a node connected to its neighbors above, below, and (in cables) sideways.

## The Core Principle

Knitting is a 1D chain grown into 2D. Each stitch is a loop pulled through the loop below it. The fabric grows row by row, with each row connected to the previous by the loops themselves.

- **Knit stitch**: Loop pulled from back to front → smooth V on right side
- **Purl stitch**: Loop pulled from front to back → bump on right side
- **Row**: A horizontal line of stitches
- **Column**: A vertical line of stitches
- **Gauge**: Stitches per inch × rows per inch

## Visual DNA of Knitted Cloth

- **V-shaped columns**: The signature of stockinette stitch
- **Horizontal rows**: Visible as slight waves between V's
- **Elasticity**: Knit fabric stretches horizontally and vertically
- **Fiber fuzz**: Looped structure catches light with halo
- **Cables**: Groups of stitches temporarily cross each other
- **Colorwork**: Multiple yarns carried across the back

## The Stitch Families

### Basic Stitches
- [Stockinette](pattern_families/stockinette.md) — all knit on right side, all purl on wrong side
- [Garter](pattern_families/garter.md) — all knit every row, ridges on both sides
- [Ribbing](pattern_families/ribbing.md) — knit/purl columns, elastic edge fabric
- [Seed / moss stitch](pattern_families/seed_moss.md) — alternating knit/purl in grid

### Textured Stitches
- [Cable knit](pattern_families/cable_knit.md) — braided loop displacement
- [Bobbles](pattern_families/bobbles.md) — raised knot clusters
- [Waffle knit](pattern_families/waffle_knit.md) — recessed square texture
- [Fisherman / Aran](pattern_families/fisherman_knit.md) — complex cable + texture combos

### Lace Stitches
- [Lace knitting](pattern_families/lace_knitting.md) — yarn-overs create holes
- [Eyelets](pattern_families/eyelets.md) — single hole with decrease

### Colorwork
- [Fair Isle](pattern_families/fair_isle.md) — stranded colorwork, geometric patterns
- [Intarsia](pattern_families/intarsia.md) — blocks of color, no floats
- [Brioche](pattern_families/brioche.md) — slipped stitches with yarn-overs, reversible rib
- [Entrelac](pattern_families/entrelac.md) — modular diamond tiles
- [Slip stitch](pattern_families/slip_stitch.md) — color effects from slipped stitches

## Shader Translation: Knit-Specific Parameters

| Parameter | What It Controls | Range | Notes |
|-----------|---------------|-------|-------|
| `stitch_width` | Width of one V-stitch | 0.01–0.1 | In UV space |
| `stitch_height` | Height of one row | 0.01–0.1 | Usually ≈ stitch_width |
| `v_depth` | How deep the V goes | 0.0–0.5 | Normal displacement |
| `cable_braid_count` | Strands in cable | 2–8 | Even numbers |
| `cable_twist_frequency` | Rows between twists | 4–12 | More = looser cable |
| `yarn_fuzz` | Fiber halo radius | 0.0–1.0 | For wool/acrylic |
| `gauge_tension` | Tightness of stitches | 0.5–2.0 | Higher = denser |
| `color_float_thickness` | Carried yarn on back | 0.0–0.5 | Visible on wrong side |

## Knit-to-Shader Logic

### Stockinette V-Stitch
```glsl
float stockinette(vec2 uv, float stitch_w, float stitch_h) {
    vec2 stitch = vec2(fract(uv.x / stitch_w), fract(uv.y / stitch_h));
    float v_shape = abs(stitch.x - 0.5) * 2.0;
    float row_wave = sin(stitch.y * PI) * 0.1;
    float depth = (1.0 - v_shape) * 0.5 + row_wave;
    return depth;
}
```

### Cable Braid
```glsl
float cable_braid(vec2 uv, float width, float twist_freq) {
    float x = fract(uv.x / width);
    float row = floor(uv.y * rows_per_unit);
    float twist_phase = mod(row, twist_freq) / twist_freq;
    float strand_offset = sin(twist_phase * PI * 2.0) * 0.3;
    float strand = smoothstep(0.0, 0.3, abs(x - 0.5 - strand_offset));
    return strand;
}
```

## Prompt Templates

### Basic Knit Texture
> "Macro photograph of a [STITCH TYPE] knit fabric in [FIBER], showing the [V-shapes/ridges/bumps] of individual stitches, soft fiber fuzz catching light, cozy tactile texture, shallow depth of field"

### Cable Knit
> "A complex Aran cable knit sweater in [COLOR] [FIBER], showing raised braided cables crossing over seed-stitch ground, cable twists every [N] rows, soft halo of fuzz, winter textile detail"

### Fair Isle
> "Traditional Fair Isle colorwork knit in [FIBER], featuring [COLOR COUNT] colors in geometric [MOTIF] pattern, stranded floats visible on reverse side, Shetland island tradition"

## Anti-Drift: Knitting-Specific

- **Never confuse knit and crochet** — Knit = continuous interlooped rows; Crochet = discrete knot-node units
- **Stockinette curls** — The edges roll; flat stockinette without edge treatment is suspicious
- **Fair Isle has floats** — If there are no carried yarn strands on the back, it's intarsia or duplicate stitch
- **Garter stitch is bumpy on both sides** — If one side is smooth, it's stockinette
- **Cable knit must have a ground** — Cables sit on a base fabric (usually stockinette or reverse stockinette)

---

*This repo treats knitting as graph traversal. Each row is a walk. Each cable is a temporary swap of edges. The yarn is the path.*
