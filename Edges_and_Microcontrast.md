Unlike *[Unsharp Mask](Sharpening#Unsharp_Mask "wikilink")*, *Edges* is
a true sharpening algorithm. It does not introduce halos, it can be used
to some degree on noisy images, and it works in the Lab space. *Edges*
sharpens just the edges, and it can be complimented by *Microcontrast*
to enhance texture.

## Edges

Iterations
How many passes the algorithm makes. Higher numbers produce a more
posterized effect.

Quantity
How many adjacent pixels will be searched for an edge. Larger values
lead to sharper edges.

Luminance only
Sharpens the L\* channel only; a\* and b\* channels are untouched.

More information here:
<https://web.archive.org/web/20110625093654/http://www.rawness.es/sharpening/?lang=en>

## Microcontrast

Quantity
Uniformity

A 3x3 matrix is better suitable for noisier images.