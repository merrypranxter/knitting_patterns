# Bobbles

Popped yarn spheres.

## What It Is

Bobbles are **three-dimensional bumps** created by working multiple stitches into one stitch, then decreasing them back to one. The result is a raised, spherical knot on the fabric surface.

## Construction

- **Increase cluster**: K1, yo, k1, yo, k1 into one stitch = 5 from 1
- **Turn and work**: Knit the 5 stitches for a few rows
- **Decrease back**: K5tog or similar to return to one stitch
- **Pop to front**: The extra fabric forms a ball

## Visual DNA

- **Spherical bumps**: Round, raised dots on fabric surface
- **Shadowed**: Light catches top; shadow at base
- **Tactile**: Visibly dimensional, touchable
- **Often scattered**: Like popcorn across a field of stockinette
- **Common uses**: Aran sweaters, textured accessories, decorative panels

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `bobble_size` | 0.02–0.1 | Diameter of bump |
| `bobble_height` | 0.0–0.15 | Normal displacement |
| `density` | 0.0–0.5 | Percentage of surface covered |
| `arrangement` | 0–2 | 0 = scattered, 1 = grid, 2 = diamond |

## GLSL Snippet

```glsl
float bobble(vec2 uv, vec2 pos, float size, float height) {
    float dist = length(uv - pos) / size;
    float shape = sqrt(max(0.0, 1.0 - dist * dist));
    return shape * height;
}
```

## Prompt Template

> "Bobble knit texture in [COLOR] wool, raised spherical bumps scattered across stockinette ground, deep shadows at bobble bases, tactile 3D surface, Aran-inspired knit"

## Anti-Drift

- **Not popcorn stitch**: Popcorn is crochet; bobble is knit
- **Not nupp**: Nupp (Estonian lace) is a similar bump but worked differently
- **Requires multiple rows**: Bobbles take several rows to build

---

*Multiple stitches into one. The sphere is the excess.*
