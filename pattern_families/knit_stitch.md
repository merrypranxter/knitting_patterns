# Knit Stitch

The fundamental loop. The atom of knitting.

## What It Is

The knit stitch is the basic building block of all knitting. A single loop pulled through another loop, creating an interlocked chain that forms fabric. The "V" shape is the signature.

## Construction

- **Working yarn**: New yarn pulled through an existing stitch
- **Needle insertion**: Into the front leg of the stitch below
- **Loop formation**: New stitch sits on the needle; old stitch drops off
- **Result**: A row of "V" shapes stacked vertically

## Visual DNA

- **V-shaped columns**: Each stitch looks like a small V
- **Vertical ribs**: Columns of V's create subtle vertical lines
- **Smooth face**: The "right side" of stockinette is all knit stitches
- **Elastic stretch**: Loops can expand and contract
- **Common uses**: Every knitted fabric starts here

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `stitch_height` | 0.02–0.08 | Height of one V |
| `stitch_width` | 0.01–0.05 | Width at top of V |
| `leg_thickness` | 0.001–0.01 | Yarn diameter |
| `loop_openness` | 0.0–1.0 | Tension: 0 = tight, 1 = loose |

## GLSL Snippet

```glsl
float knit_stitch(vec2 uv, vec2 pos, float w, float h) {
    vec2 local = (uv - pos) / vec2(w, h);
    float v_shape = abs(local.x) + local.y * 0.5;
    return smoothstep(1.0, 0.0, v_shape);
}
```

## Prompt Template

> "Close-up of hand-knit fabric showing individual knit stitches, V-shaped loops in [COLOR] yarn, slight variation in tension showing handmade quality, soft wool texture"

## Anti-Drift

- **Not purl**: Knit = V on right side; purl = bump on right side
- **Not crochet**: Crochet has completed knots; knitting has continuous loops
- **Foundation of everything**: Stockinette, ribbing, cables all start with knit/purl

---

*The V is the unit. The loop is the connection.*
