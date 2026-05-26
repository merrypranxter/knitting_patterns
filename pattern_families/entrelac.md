# Entrelac

Woven squares from knit stitches.

## What It Is

Entrelac is a **modular knitting technique** that creates a fabric of interlocking diamond or rectangular blocks, each worked separately in sequence. The result looks like woven basketry or tilework.

## Construction

- **Tiered blocks**: Worked in tiers of rectangles or diamonds
- **Pick up stitches**: Each new block is started by picking up stitches from the previous block
- **Direction changes**: Blocks are worked in alternating directions
- **Tunisian adjacent**: Entrelac resembles Tunisian crochet in appearance

## Visual DNA

- **Diamond grid**: Interlocking tilted squares creating a woven appearance
- **Color blocks**: Often uses color changes at block boundaries
- **Dimensional texture**: Each block sits slightly proud of neighbors
- **No actual weaving**: Despite appearance, it's all knit stitches
- **Common uses**: Scarves, bags, blankets, accessories

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `block_size` | 0.05–0.2 | Width of one diamond |
| `tier_count` | 2–20 | Number of block rows |
| `color_per_block` | 0–1 | Whether each block changes color |
| `edge_depth` | 0.0–0.05 | Slight ridge at block boundaries |

## GLSL Snippet

```glsl
float entrelac(vec2 uv, float size) {
    vec2 grid = floor(uv / size);
    vec2 local = fract(uv / size) - 0.5;
    float diamond = abs(local.x) + abs(local.y);
    return smoothstep(1.0, 0.0, diamond);
}
```

## Prompt Template

> "Entrelac knit blanket in [COLOR PALETTE], interlocking diamond blocks in alternating directions, woven appearance from modular knit construction, color changes at block edges, textured hand"

## Anti-Drift

- **Not woven**: Despite appearance, entrelac is knitted
- **Not mitered squares**: Mitered squares decrease to a point; entrelac blocks are rectangles
- **Requires picking up stitches**: Each block starts from the edge of the previous
- **Looks like basketweave**: The interlocking diamonds resemble woven texture

---

*Modular diamonds. The block is the tile.*
