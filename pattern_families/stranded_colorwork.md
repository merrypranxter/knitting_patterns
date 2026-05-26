# Stranded Colorwork

More than two colors, horizontal bands.

## What It Is

Stranded colorwork is the umbrella term for techniques where multiple colors are carried across a row. Fair Isle is the most famous, but other traditions exist — Norwegian, Swedish, Baltic, and more.

## Construction

- **Floats on reverse**: Unused colors carried across the back
- **Color dominance**: Which color is held above/below affects appearance
- **Two-handed knitting**: One color in each hand for efficiency
- **Steeking**: Cutting open knitted tubes for cardigans (traditional in some cultures)

## Visual DNA

- **Multi-color bands**: Horizontal stripes of different motifs
- **Float texture**: Slight dimpling from float tension
- **Cultural motifs**: Stars, snowflakes, reindeer, geometric borders
- **Warmth**: The extra layer of floats adds insulation
- **Common uses**: Sweaters, mittens, socks, yokes, accessories

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `tradition_type` | 0–5 | 0 = Fair Isle, 1 = Norwegian, 2 = Baltic, etc. |
| `motif_library` | — | Culture-specific patterns |
| `color_count_per_row` | 2–5 | More = more complex |
| `float_visibility` | 0.0–0.1 | Texture from reverse floats |

## GLSL Snippet

```glsl
vec3 stranded_colorwork(vec2 uv, float rows, sampler2D tradition) {
    float band = floor(uv.y * rows);
    return texture(tradition, vec2(uv.x, band / num_bands)).rgb;
}
```

## Prompt Template

> "[TRADITION] stranded colorwork sweater in [COLOR PALETTE], horizontal bands of [MOTIF] patterns with visible float texture on interior, warm wool, traditional Nordic knit"

## Anti-Drift

- **Fair Isle is a subset**: All Fair Isle is stranded; not all stranded is Fair Isle
- **Steeking is radical**: Cutting knitted fabric on purpose, then reinforcing
- **Color dominance matters**: The color held lower (dominant) appears slightly larger
- **Not intarsia**: Stranded carries all colors; intarsia uses separate bobbins

---

*Floats across the back. The tradition is the motif library.*
