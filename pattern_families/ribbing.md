# Ribbing

The elastic column.

## What It Is

Ribbing is created by alternating knit and purl stitches in the same row, forming vertical columns that are stretchy and springy. It's used for cuffs, hems, and edges that need to grip.

## Construction

- **Knit/purl alternation**: K1, P1 or K2, P2 or any combination
- **Vertical columns**: Knit columns recede; purl columns advance
- **Reversible**: Same pattern on both sides
- **Elasticity**: Columns compress and expand

## Visual DNA

- **Vertical columns**: Alternating smooth knit and bumpy purl columns
- **Stretch and recovery**: Compresses width-wise, bounces back
- **Depth variation**: Knit valleys, purl ridges (or vice versa)
- **Common counts**: 1×1, 2×2, 3×3, 3×1, 4×2 ribbing
- **Common uses**: Cuffs, hems, necklines, hat brims

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `rib_count` | 1–6 | Knit stitches per rib |
| `rib_width` | 0.01–0.05 | Width of one column |
| `depth_contrast` | 0.0–0.1 | Height difference between K and P |
| `elasticity` | 0.0–1.0 | How compressed the rib appears |

## GLSL Snippet

```glsl
float ribbing(vec2 uv, float rib_w, int k_count, int p_count) {
    float period = float(k_count + p_count) * rib_w;
    float phase = fract(uv.x / period);
    float is_knit = step(phase, float(k_count) * rib_w / period);
    float depth = is_knit ? -depth_contrast : depth_contrast;
    return depth;
}
```

## Prompt Template

> "[COUNT] ribbing on sweater cuff in [COLOR] wool, alternating vertical knit and purl columns creating stretchy elastic texture, slight compression visible, garment detail"

## Anti-Drift

- **Not seed stitch**: Seed stitch alternates K and P every stitch; ribbing alternates by column
- **Not cable**: Cable has twisted columns; ribbing has straight columns
- **Elasticity comes from structure**: The knit/purl columns act like springs

---

*Knit and purl in columns. The stretch is the architecture.*
