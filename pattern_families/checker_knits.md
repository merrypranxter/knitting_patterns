# Checker Knits

Block by block.

## What It Is

Checkerboard knitting creates a pattern of alternating squares, usually in two colors or textures. It can be done with intarsia, stranded colorwork, or texture changes (knit vs. purl).

## Construction

- **Color blocks**: Two colors in alternating squares
- **Texture blocks**: Knit and purl squares creating texture checkerboard
- **Scale variation**: From tiny 2-stitch squares to large blocks
- **Reversible options**: Color blocks reverse colors; texture blocks are same both sides

## Visual DNA

- **Grid of squares**: Regular checkerboard arrangement
- **Color or texture contrast**: Visual distinction between adjacent blocks
- **Optical effect**: Can create depth illusion with shading
- **Classic to modern**: From traditional designs to bold graphic statements
- **Common uses**: Blankets, scarves, bags, panels, graphic knits

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `block_size` | 0.02–0.2 | Size of each square |
| `contrast_type` | 0–1 | 0 = color, 1 = texture |
| `color_1` | RGB | First square color |
| `color_2` | RGB | Second square color |

## GLSL Snippet

```glsl
float checker_knit(vec2 uv, float size) {
    vec2 grid = floor(uv / size);
    return mod(grid.x + grid.y, 2.0);
}
```

## Prompt Template

> "Checkerboard knit blanket in [COLOR 1] and [COLOR 2], alternating squares of stockinette blocks, graphic bold pattern, warm wool, modern geometric knit"

## Anti-Drift

- **Not gingham**: Gingham is woven; checker knit is knitted
- **Can be color or texture**: Two ways to achieve the same visual
- **Not entrelac**: Entrelac has diamonds; checkerboard has squares

---

*Alternating squares. The grid is the game.*
