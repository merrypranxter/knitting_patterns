# Stockinette

The smooth face of knitting.

## What It Is

Stockinette stitch is created by knitting all stitches on the right side and purling all stitches on the wrong side. The result is a smooth fabric with V-shaped columns on one side and bumpy ridges on the other.

## Construction

- **RS = all knit**: Every stitch on the front is a knit
- **WS = all purl**: Every stitch on the back is a purl
- **Flat knitting**: Requires turning work each row
- **Circular knitting**: All knit rounds = automatic stockinette

## Visual DNA

- **Smooth V columns**: Right side shows vertical columns of V's
- **Bumpy reverse**: Wrong side shows horizontal purl ridges
- **Curling edges**: Stockinette curls at edges due to tension imbalance
- **Stretch**: More horizontal than vertical stretch
- **Common uses**: Sweaters, scarves, blankets, basic knit fabric

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `v_column_width` | 0.01–0.05 | Width of one V column |
| `column_count` | 10–100 | Stitches per row |
| `curl_factor` | 0.0–0.2 | Edge curling amount |
| `smoothness` | 0.5–1.0 | How uniform the V's appear |

## GLSL Snippet

```glsl
float stockinette(vec2 uv, float columns) {
    float col = fract(uv.x * columns);
    float v = abs(col - 0.5) * 2.0 + fract(uv.y * rows) * 0.3;
    return smoothstep(1.0, 0.0, v);
}
```

## Prompt Template

> "Stockinette stitch fabric in [COLOR] wool, smooth right side with vertical V-shaped columns, slight edge curl visible, basic knitted fabric, soft hand"

## Anti-Drift

- **Not reverse stockinette**: Reverse stockinette uses the bumpy side as the face
- **Curls naturally**: All stockinette edges curl; this is normal, not a defect
- **Not garter stitch**: Garter is all knit rows (no purling)

---

*Knit the face, purl the back. The V is the right side.*
