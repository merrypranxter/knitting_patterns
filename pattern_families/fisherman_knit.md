# Fisherman Knit

Heavy cables, Irish sea.

## What It Is

Fisherman knit (Aran knit) is a traditional **Irish cable and texture knitting** characterized by dense cables, bobbles, honeycomb, and diamond patterns. Originally from the Aran Islands.

## Construction

- **Multiple techniques**: Cables, bobbles, seed stitch, moss stitch combined
- **Natural wool**: Traditionally undyed, cream-colored sheep's wool
- **Symbolic patterns**: Each pattern family has traditional meaning
- **Handknit density**: Traditionally very dense for water resistance

## Visual DNA

- **Dense cables**: Thick rope cables running vertically
- **Honeycomb panels**: Textured diamond shapes
- **Diamond patterns**: Lattice and cable diamonds
- **Bobble accents**: Popped spheres within patterns
- **Heavy hand**: Thick, warm, substantial fabric
- **Common uses**: Sweaters, cardigans, accessories, traditional Irish knit

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `cable_density` | 2–10 | Number of cables per garment |
| `panel_layout` | — | Honeycomb, diamond, cable panels |
| `wool_texture` | 0.0–1.0 | Natural wool fuzz |
| `pattern_relief` | 0.0–0.2 | Depth of textured panels |

## GLSL Snippet

```glsl
float fisherman_knit(vec2 uv, float panel_w) {
    float panel = floor(uv.x / panel_w);
    float local = fract(uv.x / panel_w);
    if (panel == 0.0) return cable(uv, local);
    if (panel == 1.0) return honeycomb(uv, local);
    if (panel == 2.0) return diamond_pattern(uv, local);
    return moss_stitch(uv, local);
}
```

## Prompt Template

> "Traditional Aran fisherman sweater in natural cream wool, dense cable panels with honeycomb and diamond textures, thick handknit construction, slight lanolin smell implied, Irish coastal tradition"

## Anti-Drift

- **Not just "cable knit"**: Aran combines multiple techniques, not just cables
- **Symbolic meaning**: Honeycomb = hard work; cables = ropes; diamonds = wealth
- **Traditionally natural**: Undyed wool; modern versions use colors
- **Very dense**: Traditional gauge is tight for weather resistance

---

*Cables, honeycomb, diamonds. The sea is in the stitches.*
