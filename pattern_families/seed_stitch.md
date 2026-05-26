# Seed Stitch

The checkerboard of knitting.

## What It Is

Seed stitch (moss stitch in UK) is created by alternating knit and purl stitches both horizontally and vertically, creating a bumpy, textured fabric that looks like scattered seeds.

## Construction

- **K1, P1 alternation**: Every stitch alternates with its neighbor
- **Row offset**: Next row starts with the opposite stitch
- **Creates bumps**: Knit stitches sit between purl bumps in all directions
- **Reversible**: Same texture on both sides

## Visual DNA

- **Scattered bumps**: No visible columns or rows — just texture
- **Matte surface**: Catches light evenly, no shine direction
- **Dense, flat**: Doesn't curl, doesn't stretch much
- **Textured hand**: Tactile, slightly rough surface
- **Common uses**: Edgings, blankets, accessories, textured panels

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `bump_density` | 0.01–0.05 | Stitches per bump |
| `bump_height` | 0.0–0.03 | Normal displacement |
| `irregularity` | 0.0–0.2 | Hand-knit slight variation |

## GLSL Snippet

```glsl
float seed_stitch(vec2 uv, float density) {
    vec2 grid = floor(uv * density);
    float is_knit = mod(grid.x + grid.y, 2.0);
    float bump = is_knit * sin(uv.x * PI * density) * sin(uv.y * PI * density);
    return bump * bump_height;
}
```

## Prompt Template

> "Seed stitch fabric in [COLOR] wool, scattered bumpy texture from alternating knit and purl stitches, matte surface with no directional lines, flat dense hand, textured knit"

## Anti-Drift

- **Not ribbing**: Ribbing has columns; seed stitch is checkerboard
- **Not garter stitch**: Garter has horizontal ridges; seed has scattered bumps
- **Same on both sides**: True reversible texture

---

*Checkerboard knit and purl. The bump is the seed.*
