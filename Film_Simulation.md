<img src="Rt_haldclut_london.jpg" title="Rt_haldclut_london.jpg"
width="900" alt="Rt_haldclut_london.jpg" /> The *Film Simulation* tool
allows you to match the colors of your photo to a chosen reference with
a single click.

To use this tool you need some images in the *Hald Color Look-Up Table
(Hald CLUT) pattern*. Either download the *RawTherapee Film Simulation
Collection* below, or make your own. The first time you run this tool
you will find a message informing you that you need to point RawTherapee
to a folder which contains the reference images this tool uses. After
downloading the *RawTherapee Film Simulation Collection* or making your
own, go to "Preferences \> Image Processing \> Film Simulation" and
point it to the folder which contains them. A restart of RawTherapee is
required.

## Startup time

It is important that you create a folder which you will only use for
storing downloaded or self-made Hald CLUT images. Don't store anything
else in that folder. The reason for this is that RawTherapee scans this
folder every time you start it, so if the folder contains more files
than necessary you will experience a **very slow startup time** (it
could take minutes). If you use any RawTherapee version since February
2016, you will be warned if scanning on startup takes more than 10
seconds. When that happens, just click the button in the popup to stop
the scan, then go to "Preferences \> Image Processing \> Film
Simulation" to see which folder is being used, and either point
RawTherapee to a folder which contains only Hald CLUT images and nothing
more, or to an empty folder if you don't want to use the Film Simulation
tool.

To give you an idea of how the startup time is affected, RawTherapee
takes about 2.5s to start when using an empty Hald CLUT folder, and
about 100ms longer, 2.6s, when using a Hald CLUT folder containing 500
files in it (that's more than in our *RawTherapee Film Simulation
Collection*). If, however, you were to accidentally tell RawTherapee
that the Hald CLUT folder is `C:\Program Files (x86)`, then the startup
time could take several minutes. As you can see, there is no reason to
worry when using Hald CLUTs as long as you use a dedicated folder as
suggested, keeping only Hald CLUT images in it.

## How It Works

![](Hald_CLUT_Identity_12.png "Hald_CLUT_Identity_12.png") This tool
uses specially prepared images in what is called a Hald CLUT pattern. It
contains all the possible colors mapped out in a specific arrangement,
modified from the known original state of the *Hald_CLUT_Identity.tif*
image. It scans each pixel of the Hald CLUT image you choose, computes
the difference between that pixel's color and the corresponding pixel's
color in the identity file, and then tweaks that color in your photo
accordingly. If your photo contains colors not present in the Hald CLUT
image, the missing colors will be interpolated so that posterization
will not occur.

For a full explanation, refer to Eskil Steenberg's page on Hald CLUT:
<http://www.quelsolaar.com/technology/clut.html>

To generate an identity 12-level 16-bit Hald CLUT image using
ImageMagick, run this command in a console:

`convert hald:12 -depth 16 -colorspace sRGB hald12_16bit.tif`

## Caveat

We recommend you use ImageMagick to generate the identity file if you
need to generate one, as the program for generating them on
www.quelsolaar.com has a bug which can cause issues with highlights. You
can of course use the identity file we provide here - it is bug-free.
Furthermore, we recommend that you use Hald CLUTs in the TIFF format if
you're using RawTherapee-4.2.140 or older, as there was a small gamma
bug which made the image slightly darker overall. This bug has been
fixed in version 4.2.141. You could of course ignore the issue
altogether if you're using Hald CLUTs for aesthetic purposes, as the
change in brightness is subtle and can easily be compensated for using
RawTherapee's exposure slider or curves, or explained away as being part
of the CLUT's intended look.

## Make Your Own

This section explains how to put the Hald CLUT identity file to use so
that it reproduces a specific rendering of color and lightness.

1.  Open a photo in RawTherapee or some other image editing program and
    tweak it to your liking. Remember that the Film Simulation tool can
    only reproduce global tonal changes, so make no local changes - no
    local contrast, no tone-mapping, etc.; make no changes which move
    pixels - no distortion correction; use no sharpening or noise
    reduction; make only global tonal adjustments - color and saturation
    changes, curves, levels, color and film modes. Save the sidecar file
    or write down the changes you made so that you can reproduce the
    changes in the next step.
2.  Open the identity Hald CLUT image in the same program and apply the
    same sidecar file or re-do the same tweaks as you did in the step
    above.
3.  Save this image as an 8-bit sRGB TIFF or PNG in the Hald CLUT folder
    you pointed RawTherapee to. It's now ready for use. Restart
    RawTherapee so that your new Hald CLUT appears in the list.

Even if your Hald CLUT image contains colors in only 8-bit precision,
missing values will be interpolated so that posterization will not occur
in your photo. As such, since there is no loss of quality, we recommend
using the level 12 identity file and storing your self-made Hald CLUT
images in the sRGB color space, 8-bit per channel. See the
[Caveat](Film_Simulation#Caveat "wikilink") section above to help you
decide whether to use the TIFF or PNG format.

If you apply this Hald CLUT to a photo in RawTherapee and the photo
unexpectedly and unintentionally becomes considerably darker or lighter
than it should have, then it's likely that the program which you ran it
through did something with the gamma. To remedy, you have to undo what
that program did. Try generating your own 12-level Hald CLUT but instead
of using the "sRGB" colorspace use just "RGB".

### Advanced - Identity DNG

Some programs might not let you open a TIFF image. If the program
supports DNG files, and demosaiced ones at that (what Adobe DNG
Converter refers to as "Linear (Demosaiced)"), then you can use this
trick. Using ImageMagick, ExifTool and the commands below, making use of
the fact that DNG is just a form of TIFF, you can generate an identity
Hald CLUT in DNG format:

    convert hald:12 -depth 16 -colorspace RGB -gravity NorthWest -splice 4x4 -gravity SouthEast -splice 4x4 foo.tif
    exiftool -DNGVersion=1.4.0.0 -PhotometricInterpretation='Linear Raw' foo.tif
    mv -v foo.tif Hald_CLUT_Identity_12.dng

Raw editing programs will discard a certain number of pixel rows and
columns from the image edges for technical reasons to do with
demosaicing. How many rows and columns get discarded depends entirely on
the program. You need to figure this out. A 12-level identity Hald CLUT
will have precisely 1728x1728 pixels. When you process that CLUT in a
program whose color effects you're trying to emulate, the saved image
must have precisely 1728x1728 pixels. Since you're fooling the program
into thinking it's working on a raw file, and since it will probably
discard some pixels around the edges, you need to figure out exactly how
many rows and columns of padding are needed and add them around the
image. RawTherapee cuts off 4 pixels all around when reading demosaiced
DNG files, so the command above first adds a 4 pixel row and column to
the bottom and right edges, then another 4 pixel row and column to the
top and left edges. When you open this image in the target program, zoom
into each side's edge and figure out whether you need to add more (or
remove some), then modify the command accordingly.

Once you have the borders figured out, merely open this DNG in the
target program and follow the steps above in the "Make your own"
section.

## RawTherapee Film Simulation Collection

This archive contains a collection of film simulation profiles in the
*Hald Color Look-Up Table (Hald CLUT) pattern*. Unless otherwise noted
in the filename, they are all in the sRGB color space, 8-bit per
channel, in the PNG image format. Most of them are designed to mimic the
results of various film stocks, pushed and pulled in various ways or
faded over time.

Apply these images to your photos in Hald CLUT-capable software such as
RawTherapee to instantly match the colors of your photo to the chosen
reference.

The suffixes +, ++, +++, -, --, --- refer to the strength the film was
[pushed or pulled](https://en.wikipedia.org/wiki/Push_processing) during
development (non-linear), and "generic" refers to the film type usually
sold for rebranding.

[Download](http://rawtherapee.com/shared/HaldCLUT.zip) (402MB!)

<!-- -->

Changelog
2015-09-20
Added the "CreativePack-1" color collection.

Converted all TIFFs to PNG (except for the identity image).

2015-03-25
The identity CLUT had a bug causing cyan colors in the highlights, it
has been replaced with a fixed one.

Numbered the files so they are sorted in the correct order when pushed
or pulled (--, -, normal, +, ++).

2014-08-25
The first public release.

Re-organized into *Color* and *Black-and-White*, sub-folders sorted by
brand.

2014-08-15
Expanded README.txt and added disclaimer.

2014-07-05
The first internal release.

All images re-compressed with maximum lossless compression.

Learn more about Hald CLUTs here:


<http://www.quelsolaar.com/technology/clut.html>

<http://blog.patdavid.net/2013/08/film-emulation-presets-in-gmic-gimp.html>

<http://blog.patdavid.net/2013/09/film-emulation-presets-in-gmic-gimp.html>

Credits:


Pat David -
<http://rawtherapee.com/forum/memberlist.php?mode=viewprofile&u=5101>

Pavlov Dmitry -
<http://rawtherapee.com/forum/memberlist.php?mode=viewprofile&u=5592>

Michael Ezra -
<http://rawtherapee.com/forum/memberlist.php?mode=viewprofile&u=1442>

Disclaimer:


The trademarked names which may appear in the filenames of the Hald CLUT
images are there for informational purposes only. They serve only to
inform the user which film stock the given Hald CLUT image is designed
to approximate. As there is no way to convey this information other than
by using the trademarked name, we believe this constitutes fair use.
Neither the publisher nor the authors are affiliated with or endorsed by
the companies that own the trademarks.