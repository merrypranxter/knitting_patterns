# Lace Knitting

Holes with intention.

## What It Is

Lace knitting creates **deliberate holes** in the fabric using yarn-overs (adding extra stitches) paired with decreases. The holes form decorative patterns — leaves, flowers, geometric openwork.

## Construction

- **Yarn-over (YO)**: Creates the hole by wrapping yarn around needle
- **Decreases**: K2tog, SSK, etc. — compensate for added YO stitches
- **Pattern charts**: Lace is usually charted with symbols for each stitch
- **Blocking required**: Wet blocking opens up the lace pattern

## Visual DNA

- **Open holes**: Visible gaps where yarn-overs were placed
- **Leaf/flower motifs**: Naturalistic shapes from hole placement
- **Geometric openwork**: Diamonds, triangles, hexagons from systematic YO placement
- **Reversible distinction**: Some lace is reversible; some has a definite right side
- **Delicate hand**: Lightweight, airy, often requires fine yarn

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `hole_size` | 0.005–0.05 | Size of yarn-over gap |
| `hole_density` | 0.0–0.5 | Percentage of fabric that is hole |
| `motif_scale` | 0.1–1.0 | Size of lace pattern repeat |
| `blocking_openness` | 0.0–1.0 | How much holes open after blocking |

## GLSL Snippet

```glsl
float lace_knitting(vec2 uv, float motif_size, float hole_ratio) {
    vec2 motif = fract(uv / motif_size);
    float hole_pattern = texture(lace_chart, motif).r;
    float hole = hole_pattern * hole_ratio;
    return 1.0 - hole; // 1.0 = yarn, 0.0 = hole
}
```

## Prompt Template

> "Hand-knit lace shawl in [COLOR] mohair, delicate openwork pattern with [MOTIF] shapes from yarn-overs and decreases, blocked and stretched to reveal pattern, airy lightweight fabric"

## Anti-Drift

- **Not dropped stitches**: Lace holes are intentional; dropped stitches are mistakes
- **Requires blocking**: Lace looks messy before blocking; after blocking, the pattern opens
- **Not crochet lace**: Knitted lace uses yarn-overs; crochet lace uses chains and spaces
- **Charted**: Lace patterns are almost always charted, not written out

---

*Yarn-over and decrease. The hole is the design.*
