# Brioche

The squish monster.

## What It Is

Brioche is a **reversible, thick, ribbed fabric** created by working yarn-overs together with slipped stitches. It produces a dense, squishy, deeply textured fabric that looks the same on both sides.

## Construction

- **Slip 1, yo**: Slip a stitch with yarn-over wrapped around it
- **Bark / burp**: Brioche knit (br-k) or brioche purl (br-p) works the pair
- **Reversible**: Same appearance on both sides
- **Thick**: Two layers of fabric in one

## Visual DNA

- **Deep vertical ribs**: Pronounced columns with deep valleys
- **Squishy hand**: Compresses dramatically, springs back
- **Reversible**: Identical front and back
- **Color possibilities**: Two-color brioche creates stunning vertical stripes
- **Common uses**: Scarves, cowls, hats, squishy accessories

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `rib_depth` | 0.0–0.2 | Deep vertical channels |
| `squish_factor` | 0.5–2.0 | How compressible it appears |
| `color_layers` | 1–2 | Single or two-color brioche |
| `column_width` | 0.02–0.08 | Width of each rib |

## GLSL Snippet

```glsl
float brioche(vec2 uv, float width, float depth) {
    float col = abs(fract(uv.x / width) - 0.5) * 2.0;
    float rib = smoothstep(0.0, 0.3, col) * smoothstep(1.0, 0.7, col);
    return rib * depth;
}
```

## Prompt Template

> "Two-color brioche knit scarf in [COLOR 1] and [COLOR 2], deep vertical ribs with squishy compressible texture, reversible identical both sides, thick cozy hand, luxury knit accessory"

## Anti-Drift

- **Not ribbing**: Brioche is thicker and squishier; ribbing is simpler
- **Not fisherman's rib**: Similar but constructed differently
- **Requires specific technique**: Regular knit/purl won't produce brioche
- **Two-color is stunning**: Vertical color columns with deep texture

---

*Slip and yarn-over. The squish is the signature.*
