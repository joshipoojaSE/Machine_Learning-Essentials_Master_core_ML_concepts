# Dominant Color Extraction — Simple Explanation

The goal is to find the **5 most representative colors** in an image, like a color palette.

We can use the **K-Means** algorithm that we just learned.

## How does it work?

1. **Read the image:** Every pixel contains three color values — Red, Green, and Blue (RGB).
2. **Convert pixels into data:** Treat each pixel as a point with three features: `(R, G, B)`.
3. **Apply K-Means:** Set `K = 5` to group similar-colored pixels into five clusters.
4. **Find dominant colors:** The centroid of each cluster represents one dominant color.
5. **Display the palette:** Convert the five centroid values into colors and show them as swatches.

## Example

| # | Color  | Example RGB       |
|---|--------|-------------------|
| 1 | Orange | (230, 126, 34)    |
| 2 | Gray   | (128, 128, 128)   |
| 3 | Dark   | (40, 35, 30)      |
| 4 | Beige  | (225, 205, 170)   |
| 5 | Brown  | (120, 75, 40)     |

*Illustrative palette inspired by a warm-toned image. The RGB values are examples only.*
