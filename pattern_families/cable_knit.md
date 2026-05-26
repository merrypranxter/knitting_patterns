# Cable Knit

Braided yarn architecture.

## What It Is

Cable knitting creates **twisted, braided columns** by temporarily holding stitches on a cable needle, knitting other stitches, then working the held stitches. The result looks like ropes or braids running across the fabric.

## Construction

- **Cable needle**: Holds stitches while others are worked
- **Stitch crossing**: Held stitches cross in front or behind working stitches
- **Panel structure**: Cables are usually worked within stockinette panels
- **Reversible distinction**: Cables pop on right side; wrong side is usually stockinette reverse

## Visual DNA

- **Rope/braid motifs**: Twisted vertical columns crossing over each other
- **Dimensional relief**: Cables stand proud of the background
- **Shadow play**: Crossover points create depth and shadow
- **Traditional motifs**: Rope cables, honeycomb, plaited cables, diamond cables
- **Common uses**: Aran sweaters, Celtic-inspired knits, luxury accessories

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `cable_width` | 0.05–0.3 | Width of one cable column |
| `crossover_freq` | 2–10 | Rows between cross points |
| `relief_height` | 0.0–0.2 | Normal displacement for cable pop |
| `twist_direction` | -1 / 1 | Left or right twist |
| `background_stitch` | 0–1 | 0 = reverse stockinette, 1 = seed stitch |

## GLSL Snippet

```glsl
float cable_knit(vec2 uv, float width, float freq, float twist) {
    float col = uv.x / width;
    float cycle = fract(uv.y * freq);
    float phase = sin(cycle * PI + col * twist);
    float cable = smoothstep(0.0, 1.0, phase) * relief_height;
    return cable;
}
```

## Prompt Template

> "Aran cable knit sweater in [COLOR] wool, thick rope cables crossing over each other in braided relief, deep shadow at crossover points, traditional Irish knit pattern"

## Anti-Drift

- **Not ribbing**: Ribbing has straight columns; cables have crossed columns
- **Not crochet cables**: Crochet can mimic cables but uses post stitches, not cable needle
- **Requires stockinette ground**: Cables pop best against reverse stockinette background
- **Named after ropes**: The technique mimics nautical rope braiding

---

*Twisted columns. The cable needle is the architect.*
