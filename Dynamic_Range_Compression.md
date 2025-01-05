This tool can be used to compress the dynamic range of an image,
reducing highlights and lifting shadows. This is done by applying
[Fattal's tone mapping algorithm](http://www.cs.huji.ac.il/~danix/hdr/).
There are three parameters to tune:

### Amount

Sets the amount of compression, where lower values mean less
compression. The default value of 20 gives a reasonable starting point.

### Detail

The amount of detail that is preserved can be tuned with this parameter.
Negative values smooth the image, positive values recover detail that is
lost during the tonemapping. Technically, this parameter attenuates
which contrast-rich areas get compressed or not, and is linked to the
value α from the original research paper. The default value of 0 gives
no detail recovery, and usually a slightly positive value is desired.

### Anchor

The compression can be biased towards shadows or highlights by setting
this parameter. Lower values give overall darker images, and higher
values give overall lighter images. The default value is 50, resulting
in no bias. Technically, this parameter is linked to the value β from
the original research paper.