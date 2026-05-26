# Slip Stitch Patterns

Color without stranding.

## What It Is

Slip stitch patterns create **color effects by slipping stitches** rather than working them. A stitch is passed from one needle to the other without being knit, creating vertical strands or texture shifts.

## Construction

- **Slip stitch (sl)**: Move stitch without working it
- **Color changes**: New color is introduced while slipping old color stitches
- **No floats**: Color is carried vertically, not horizontally
- **Mosaic knitting**: A specific slip-stitch colorwork system

## Visual DNA

- **Vertical strands**: Slipped stitches create vertical lines of color
- **Mosaic patterns**: Two-color geometric patterns from systematic slipping
- **Texture variation**: Slipped stitches are tighter and sit differently
- **Efficient colorwork**: Only one color per row; no stranding needed
- **Common uses**: Colorwork for beginners, texture patterns, mosaic designs

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `slip_frequency` | 0.0–0.5 | Percentage of stitches slipped |
| `vertical_strand_length` | 0.02–0.2 | How far a slip carries |
| `color_contrast` | 0.0–1.0 | Difference between colors |
| `pattern_type` | 0–2 | 0 = random, 1 = mosaic, 2 = texture |

## GLSL Snippet

```glsl
float slip_stitch(vec2 uv, float slip_rate, float rows) {
    float row = fract(uv.y * rows);
    float col = floor(uv.x * cols);
    float is_slipped = step(slip_rate, random(vec2(col, floor(uv.y * rows))));
    return is_slipped; // 1.0 = slipped, 0.0 = worked
}
```

## Prompt Template

> "Slip stitch colorwork fabric in [COLOR 1] and [COLOR 2], vertical color strands from slipped stitches creating [PATTERN] motif, no horizontal floats, efficient two-color knit"

## Anti-Drift

- **Not stranded**: Slip stitch carries color vertically; stranded carries horizontally
- **Mosaic is specific**: Mosaic knitting is a named slip-stitch colorwork system
- **Tighter gauge**: Slipped stitches pull fabric tighter; adjust needle size
- **Not intarsia**: No bobbins needed; just two colors alternating

---

*Slip, don't knit. The strand is the color path.*
