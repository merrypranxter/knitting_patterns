# Waffle Knit

Pocket texture in yarn.

## What It Is

Waffle knit creates a **three-dimensional grid of recessed squares** by combining knit and purl stitches in a specific arrangement. Similar to woven waffle but achieved through knitting.

## Construction

- **K-P arrangement**: Systematic placement of knits and purls creates pockets
- **Reversible**: Same texture on both sides (sometimes slightly different)
- **Thick and warm**: The pockets trap air
- **Stretches**: More elastic than woven waffle

## Visual DNA

- **Square indentations**: Recessed cells with raised borders
- **Grid regularity**: Repeating pattern of pockets
- **Thermal quality**: Air pockets provide insulation
- **Stretchy hand**: Knit construction adds elasticity
- **Common uses**: Thermal underwear, blankets, baby clothes, sweaters

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `cell_size` | 0.02–0.1 | Size of each waffle cell |
| `pocket_depth` | 0.0–0.1 | Normal displacement |
| `border_thickness` | 0.002–0.02 | Raised border width |

## GLSL Snippet

```glsl
float waffle_knit(vec2 uv, float size) {
    vec2 cell = fract(uv / size);
    vec2 border = smoothstep(0.0, 0.2, cell) * smoothstep(1.0, 0.8, cell);
    float pocket = border.x * border.y;
    return pocket;
}
```

## Prompt Template

> "Waffle knit thermal fabric in [COLOR] cotton, 3D grid of small square pockets with raised borders, stretchy warm hand, knit version of waffle texture, baby blanket material"

## Anti-Drift

- **Not woven waffle**: Knit waffle is stretchy; woven waffle is rigid
- **Pockets are structural**: Created by stitch arrangement, not pressing
- **Thermal property**: The air pockets make it warmer than flat knit

---

*Knit and purl grid. The pocket is the warmth.*
