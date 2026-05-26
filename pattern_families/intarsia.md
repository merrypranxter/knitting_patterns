# Intarsia

Color blocks, no floats.

## What It Is

Intarsia is a **colorwork technique** where separate bobbins of color are used for each color area. The colors are not carried across; instead, they are twisted together at color boundaries.

## Construction

- **Separate bobbins**: Each color area has its own yarn supply
- **Twist at boundary**: Colors are twisted together where they meet
- **No floats**: Back is as clean as the front (mostly)
- **Large color blocks**: Works best for bold, distinct shapes

## Visual DNA

- **Sharp color boundaries**: Clean edges between color areas
- **No stranded floats**: Back shows twisted joins, not horizontal floats
- **Bold shapes**: Large blocks of color rather than small motifs
- **Often pictorial**: Can create images, letters, or large geometric forms
- **Common uses**: Picture knits, logos, large geometric patterns, argyle

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `color_block_count` | 2–20 | Number of distinct color areas |
| `boundary_sharpness` | 0.0–0.02 | How clean the color edge is |
| `twist_visibility` | 0.0–0.1 | Slight texture at join |
| `block_scale` | 0.05–0.5 | Size of color areas |

## GLSL Snippet

```glsl
vec3 intarsia(vec2 uv, sampler2D color_map) {
    float color_id = texture(color_map, uv).r;
    return palette[int(color_id * num_colors)];
}
```

## Prompt Template

> "Intarsia knit sweater with [IMAGE] in bold color blocks, sharp clean boundaries between colors with twisted joins, no stranded floats on back, pictorial knit art"

## Anti-Drift

- **Not Fair Isle**: Fair Isle strands colors across; intarsia uses separate bobbins
- **Not duplicate stitch**: Duplicate stitch is embroidery on top; intarsia is woven in
- **Requires bobbins**: Each color section needs its own yarn supply
- **Best for large shapes**: Small details are hard to manage with many bobbins

---

*Separate bobbins, twisted joins. The block is the unit.*
