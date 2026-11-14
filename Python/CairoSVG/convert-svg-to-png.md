# [Issue]

SVG to PNG???????????

# [Solution]

1. Import cairosvg, io and PIL <- Image

2. Load SVG to CairoSVG and use svg2png function:

```
svg2png(bytestring=None, *, file_obj=None, url=None, dpi=96,
            parent_width=None, parent_height=None, scale=1, unsafe=False,
            background_color=None, negate_colors=False, invert_images=False,
            write_to=None, output_width=None, output_height=None)
```

## Example:

```
import cairosvg

c = cairosvg.svg2png(url="smile.svg", output_width=256, output_height=256)

i = Image.open(io.BytesIO(c)).convert("RGBA")

i.save("smile.png")
```