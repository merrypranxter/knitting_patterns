# Garter Stitch

All knit, all the time.

## What It Is

Garter stitch is created by knitting every row (no purling). The result is a ridged fabric with horizontal bumps on both sides — identical front and back.

## Construction

- **All knit rows**: Every row is knit stitches
- **No purling**: Flat fabric that doesn't require purl knowledge
- **Reversible**: Both sides look the same
- **Lies flat**: Does not curl like stockinette

## Visual DNA

- **Horizontal ridges**: Visible rows of bumps on both sides
- **Thick, squishy**: More depth than stockinette due to doubled ridges
- **Lies flat**: No curling at edges
- **Stretchy**: Very elastic in both directions
- **Common uses**: Scarves, baby blankets, dishcloths, edgings

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `ridge_height` | 0.0–0.05 | Normal displacement for ridges |
| `ridge_frequency` | 0.02–0.1 | Rows per ridge (2 rows = 1 ridge) |
| `squish_factor` | 0.5–1.5 | How compressed the fabric looks |

## GLSL Snippet

```glsl
float garter_stitch(vec2 uv, float rows_per_ridge) {
    float row = floor(uv.y * rows);
    float ridge = floor(row / rows_per_ridge);
    float bump = mod(ridge, 2.0) * ridge_height;
    return bump;
}
```

## Prompt Template

> "Garter stitch scarf in [COLOR] chunky wool, horizontal ridges on both sides, thick squishy texture, lies flat without curling, beginner knit fabric, soft warm hand"

## Anti-Drift

- **Not stockinette**: Garter has ridges on both sides; stockinette is smooth on one side
- **Not ribbing**: Ribbing has vertical columns; garter has horizontal ridges
- **Every row knit**: No purling required; easiest beginner stitch

---

*Every row, a knit. The ridge is the rhythm.*
