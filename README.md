# Photo Mosaic, Built with pandas

A photo rebuilt from hundreds of my own photos. Every "pixel" of the mosaic is another picture, picked by matching colors.

<table>
  <tr>
    <td width="50%"><img src="original.jpg" alt="Original photo"></td>
    <td width="50%"><img src="mosaic.jpg" alt="Photo mosaic"></td>
  </tr>
  <tr>
    <td align="center"><b>Original</b></td>
    <td align="center"><b>Mosaic</b> (open the image and zoom in to see the tiles)</td>
  </tr>
</table>

## How it works

1. **Image → DataFrame.** Load the base photo into pandas with one row per pixel (`x, y, r, g, b`), about 5 million rows for this image.
2. **Profile every tile.** Compute the average RGB color of each photo in my tile library.
3. **Grid the base image.** Split it into small square regions and find each region's average color.
4. **Find the best match.** For each region, choose the tile photo with the smallest Euclidean distance in color space:
   `distance = √((r₁ − r₂)² + (g₁ − g₂)² + (b₁ − b₂)²)`
5. **Assemble** the winning tiles into the final image.

Reducing each item to a feature vector and matching on distance is the same idea behind nearest-neighbor recommendations and customer segmentation.

## About

Built for STAT 107 (Data Science Discovery) at the University of Illinois Urbana-Champaign, Fall 2025. It was a guided course project, so this repo shows the approach and the result rather than the assignment's solution code.

**Tools:** Python · pandas · Pillow
