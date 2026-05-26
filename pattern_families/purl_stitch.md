# Purl Stitch

The bump. The yin to knit's yang.

## What It Is

The purl stitch is the reverse of the knit stitch — the yarn is worked from the front of the fabric, creating a bump or horizontal bar on the right side. It is the same stitch as a knit, just viewed from the opposite side.

## Construction

- **Reverse entry**: Needle enters from the back of the stitch
- **Yarn front**: Working yarn is held in front of the needle
- **Bump formation**: Creates a horizontal ridge on the right side
- **Relationship**: 1 row purl = 1 row knit viewed from the reverse

## Visual DNA

- **Horizontal bump**: Each purl stitch looks like a small horizontal bar
- **Garter ridge**: All purl rows create the ridged texture of garter stitch
- **Reversible**: Purl side of stockinette = bumpy; knit side = smooth
- **Same elasticity**: Purl stretches the same as knit
- **Common uses**: Garter stitch, ribbing, seed stitch, moss stitch

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `bump_height` | 0.0–0.05 | Normal displacement for bump |
| `bump_width` | 0.01–0.05 | Width of horizontal bar |
| `row_spacing` | 0.02–0.08 | Distance between purl bumps |

## GLSL Snippet

```glsl
float purl_stitch(vec2 uv, vec2 pos, float w, float h) {
    vec2 local = (uv - pos) / vec2(w, h);
    float bump = smoothstep(0.0, 0.5, local.y) * smoothstep(1.0, 0.5, local.y);
    return bump * smoothstep(w, 0.0, abs(local.x));
}
```

## Prompt Template

> "Purl stitch texture on hand-knit fabric, horizontal bump ridges in [COLOR] yarn, garter stitch appearance with alternating knit/purl rows visible, soft wool"

## Anti-Drift

- **Same stitch as knit**: Purl is just knit from the other side
- **Not a different technique**: It's the mirror operation
- **Stockinette reverse**: The back of stockinette is all purl bumps

---

*The bump is the mirror. The purl is the reverse.*
