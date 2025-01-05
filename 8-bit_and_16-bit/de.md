Todo-List / State:

- Translation: open
- Content completely cleared: open
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# 8- und 16-Bit Bilddatenformat

"8-bit" when referring to image formats typically means that the program
assigns 8 [bits](https://en.wikipedia.org/wiki/Bit) (eight "1" or "0"
values, which together make one
[byte](https://en.wikipedia.org/wiki/Byte), capable of representing an
[integer](https://en.wikipedia.org/wiki/Integer) value from 0
\[00000000\] to 255 \[11111111\]) to each pixel's color channel, and
each pixel in the files RawTherapee saves has three color channels -
red, green and blue.

Most modern raw-capable [DSLR](https://en.wikipedia.org/wiki/DSLR)
cameras use 12- or 14-bit analog-to-digital converters to record the
sensor data. This means that when choosing an 8-bit-per-channel output
format in your camera, such as JPEG, one loses some information. It's
not as simple as it may seem though, cameras record data linearly (due
to limitations in hardware design) while JPEG, TIFF and PNG [gamma
encode](https://en.wikipedia.org/wiki/Gamma_correction) their data
meaning that they distribute more values in the shadow range and less in
the highlights which better matches the eye's sensititvity. This means
that an 8 bit JPEG can display as much as log2((1/2^8)^2.2) = 17.6 stops
of dynamic range which indeed exceeds the 14 stops of the current best
cameras, which explains why you sometimes can see a camera's shadow
noise even in an 8 bit JPEG. However due to the fewer values in
highlights we lose precision there compared to the camera. Practically
this is not a problem when the output file is the definitive one and
will not be processed anymore, however a photo can be vastly improved
when saved as raw data and processed using a state of the art raw
processing program, such as your's truly - RawTherapee.

Once you have processed a photo in RawTherapee, you are faced with the
same choice - to save the image with a color resolution of 8 bits per
channel, or 16 bits per channel (only
[TIFF](https://en.wikipedia.org/wiki/TIFF) and
[PNG](https://en.wikipedia.org/wiki/Portable_Network_Graphics), not
[JPEG](https://en.wikipedia.org/wiki/JPEG)). If you plan to post-process
your photos after RawTherapee in a 16-bit-capable image editing program,
it is better to save them in a lossless 16-bit format. Uncompressed TIFF
is suggested as an intermediate format, as it is quick to save and
stores all the metadata ([Exif](https://en.wikipedia.org/wiki/Exif),
[IPTC](https://en.wikipedia.org/wiki/IPTC_Information_Interchange_Model),
[XMP](https://en.wikipedia.org/wiki/Extensible_Metadata_Platform)) of
the original file (PNG generally discards metadata!).

There is some confusion over the naming of 8, 16, 24 and 32-bit files.
Here is a clarification, but it gets confusing, so put your tin foil hat
on. You do not actually need to read this to use RawTherapee, it is just
background knowledge. Each of the red, green and blue channels stored in
a JPEG, PNG or TIFF file is actually a colorless image, but when you
combine these three colorless images together, you get a color image.
This is how all digital representation of images works - color images
are always decomposed into their components in one way or another. Of
the file formats that RawTherapee can save to (JPG, PNG and TIFF), each
pixel contains information for three color channels - red, green and
blue. We say "8 bits per channel" to make it clear that these 8 bits
apply to one color channel only. The reason is that you might encounter
references to "8-bit images", and here it gets confusing, because the
person who wrote that may have been referring to a grayscale format
which stores only one channel, or to a color format that stores three
channels, with 8-bit precision each. Another notation for the very same
"8-bit" images that RawTherapee saves is "24-bit". Woo, confusing. Or is
it? Each pixel is made of 3 channels, and each channel stores 8 bits of
data, so we have a total of 24 bits of data per pixel. It gets worse.
Image editing programs can also store a fourth channel, called "alpha".
To put it simply, alpha describes how transparent a pixel is. These
alpha channels also have a "color resolution" of 8 bits. Both PNG and
TIFF files can handle alpha, JPEG can't. If you have an 8 bits per
channel image with an alpha channel, it can also be described as a
32-bit image; R (8) + G (8) + B (8) + alpha (8) = 32. The ultimate
problem is that you can also have an image that assigns as many as 32
bits per color channel. These images can be described as "32-bit" images
as well as "96-bit images" (because R (32) + G (32) + B (32) = 96). All
real HDR files are stored in image formats that assign at least 16-bit
floating-point numbers for each pixel per color channel, such as the EXR
format, or 32-bit ones, such as the RGBE format. To summarize, an "8-bit
per channel" image with three channels (RGB) can also be called a
"24-bit per pixel" image, and a "16-bit per channel" image with three
channels can also be called a "48-bit per pixel" image. In both cases
use the former (the full "x bit per channel" description, don't just say
"x bit"!), it’s more clear what you mean.

[Category:General](Category:General "wikilink")