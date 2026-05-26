# Moss Stitch

The British seed.

## What It Is

Moss stitch (double seed stitch) is similar to seed stitch but with a two-row repeat — knit stitches sit above knit stitches for two rows, then shift. Creates a slightly more pronounced, more regular texture than seed stitch.

## Construction

- **2-row repeat**: K1, P1 for two rows, then offset
- **Bigger bumps**: The longer repeat creates more distinct texture
- **Flat and stable**: Doesn't curl, good for borders
- **Reversible**: Same on both sides

## Visual DNA

- **Larger texture**: Bumps are more pronounced than seed stitch
- **Regular grid**: Slightly more organized than seed stitch
- **Matte**: Even light distribution
- **Common uses**: Sweater panels, scarves, borders, textured accessories

## Shader Parameters

| Parameter | Range | Notes |
|-----------|-------|-------|
| `bump_size` | 0.01–0.05 | Larger than seed stitch |
| `bump_height` | 0.0–0.04 | Slightly raised |
| `repeat_shift` | 2 | Two-row offset |

## GLSL Snippet

```glsl
float moss_stitch(vec2 uv, float density) {
    vec2 grid = floor(uv * density);
    float row_group = floor(grid.y / 2.0);
    float is_knit = mod(grid.x + row_group, 2.0);
    return is_knit * bump_height;
}
```

## Prompt Template

> "Moss stitch fabric in [COLOR] wool, pronounced bumpy texture from two-row repeat, regular grid of knit and purl bumps, flat stable hand, British knit tradition"

## Anti-Drift

- **Not seed stitch**: Moss is two-row repeat; seed is one-row
- **Not ribbing**: Moss has no columns
- **UK terminology**: In UK, "moss stitch" = US "seed stitch"; this is double seed

---

*Two-row checkerboard. The bump is bigger.*
