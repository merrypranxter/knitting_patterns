# Eyelets

Pinpoint holes. Deliberate gaps.

## What It Is

Eyelets are **small, isolated holes** in knitted fabric created by a single yarn-over paired with a single decrease. They're simpler than lace patterns — just a hole, not a complex motif.

## Construction

- **Single YO**: One yarn-over creates the hole
- **Single decrease**: K2tog or SSK compensates
- **Placement**: Can be random, in rows, or in specific patterns
- **Size**: Usually small, round holes

## Visual DNA

- **Small round holes**: Distinct, even gaps
- **Often decorative edging**: Along hems, borders, or as all-over texture
- **Subtle lace**: Simpler than full lace patterns
- **Pairs with stockinette**: Usually set within smooth fabric
- **Common uses**: Edgings, summer knits, eyelet panels, decorative details

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `hole_size` | 0.005–0.02 | Small, precise holes |
| `hole_spacing` | 0.02–0.2 | Distance between eyelets |
| `arrangement` | 0–3 | 0 = random, 1 = grid, 2 = diagonal, 3 = border |

## GLSL Snippet

```glsl
float eyelets(vec2 uv, float spacing, float size) {
    vec2 grid = floor(uv / spacing);
    vec2 center = (grid + 0.5) * spacing;
    float dist = length(uv - center);
    return smoothstep(size, 0.0, dist);
}
```

## Prompt Template

> "Eyelet knit fabric in [COLOR] cotton, small round holes in [ARRANGEMENT] pattern on stockinette ground, delicate summer knit texture, slight openness for breathability"

## Anti-Drift

- **Not lace**: Eyelets are simple isolated holes; lace has connected, complex patterns
- **Not dropped stitches**: Eyelets are intentional; drops are mistakes
- **Usually paired with decrease**: Single YO + single decrease = stable fabric

---

*Single yarn-over. The hole is the accent.*
