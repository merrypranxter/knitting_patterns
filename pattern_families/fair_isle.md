# Fair Isle

Color bands, island style.

## What It Is

Fair Isle is a **stranded colorwork technique** where two or more colors are carried across the row, creating horizontal bands of small geometric patterns. Named after a Scottish island.

## Construction

- **Stranded**: Unused color is carried across the back as a "float"
- **Two colors per row**: Usually limited to 2 colors per round
- **Small motifs**: Repeating geometric patterns in narrow bands
- **Float management**: Long floats are "trapped" or "woven in"

## Visual DNA

- **Horizontal color bands**: Stripes of different patterns
- **Small geometric motifs**: Stars, crosses, zigzags, OXO patterns
- **Color palette**: Traditional = natural wool colors; modern = any
- **Floats on reverse**: Back shows horizontal color strands
- **Common uses**: Sweaters, mittens, hats, yoke sweaters

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `band_height` | 0.02–0.1 | Height of each pattern band |
| `motif_size` | 0.01–0.05 | Size of individual pattern unit |
| `color_count` | 2–6 | Total colors in garment |
| `float_length` | 0.01–0.1 | Visible strands on reverse |

## GLSL Snippet

```glsl
vec3 fair_isle(vec2 uv, float bands, sampler2D motifs[]) {
    float band = floor(uv.y * bands);
    vec2 motif_uv = fract(vec2(uv.x * motif_freq, band));
    return texture(motifs[int(band)], motif_uv).rgb;
}
```

## Prompt Template

> "Traditional Fair Isle sweater in [COLOR PALETTE], horizontal bands of small geometric stranded colorwork motifs, visible floats on interior, natural wool, Scottish island knit tradition"

## Anti-Drift

- **Not intarsia**: Fair Isle is stranded; intarsia uses separate bobbins
- **Limited colors per row**: Usually 2 colors max per round
- **Floats must be managed**: Floats longer than 1" are usually trapped
- **Named after island**: Fair Isle, one of the Shetland islands

---

*Stranded color bands. The float is the connection.*
