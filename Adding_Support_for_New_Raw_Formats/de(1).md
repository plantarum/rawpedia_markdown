Created for referencing.

Todo-List / State:

- Translation: open
- Content completely cleared: open
- Expression and didactics checked: open
- Spelling checked: open

Ready for publishing: no

------------------------------------------------------------------------

# Unterstützung neuer Raw-Formate zufügen

Adding perfect support for new raw formats in RawTherapee is easy. You
can do it yourself, or you can take the needed photos and send them to
us so we can do the measurements ourselves and add support for your
camera.

## Introduction

Reading a raw file properly requires knowing some things about it, and
RawTherapee looks for this information in three places:

- In the embedded dcraw code,
- In the raw file itself,
- In a text file called camconst.json

The needed information is gathered from all three places, and
camconst.json is the most important source of it. If any information
overlap occurs, camconst.json takes priority.

camconst.json allows one to set the following:

- Color matrices for [Illuminant
  D65](http://en.wikipedia.org/wiki/Illuminant_D65), in dcraw format,
- white and black levels,
- raw crop size and offset to remove spurious rows and columns,
- masked area size and offset from which black levels can be calculated

for each combination of color channel, ISO and aperture for a given
camera make and model. For this reason, camconst.json serves both as a
place for quickly adding detailed support for new raw formats as well as
a place for improving support for cameras already but imperfectly
handled by dcraw.

## Needed Photos

To make the required measurements for perfect support, you will need to
take several series of photos with specific settings:

- Each photo must be completely overexposed everywhere! Do this by
  pointing your camera at a bright light (e.g. the sky, a lamp), zooming
  in as needed, and increasing exposure time until everything is
  absolutely clipped. Of course shoot in raw mode. If your camera has
  several raw modes, use the full one, uncropped, lossless compression
  if possible.

1.  If your camera has built-in noise reduction, turn it off. Take a
    series of photos as described above, one photo for every ISO value
    your camera supports, making sure not to exceed an exposure time of
    0.5s, using an aperture of f/8. As an example, for a typical camera
    you would end up with about 8 photos: ISO100, ISO200, ISO400,
    ISO800, ISO1600, ISO3200, ISO6400, ISO12800. New cameras often
    include intermediate ISO values, e.g. ISO160, ISO320, etc. If your
    camera includes such ISO values, it is important that you shoot them
    as well.
2.  If your camera has built-in noise reduction, turn it on. Take a
    second series of photos as described above, one photo for every ISO
    value your camera supports 1 stop apart, making sure that the
    exposure time in all cases is at least 2 seconds, not less, using an
    aperture of f/5.6. That's another about 8 photos.
3.  Some cameras scale raw values for larger apertures, particularly
    Canon and Nikon models. The only way to know whether your camera
    does this for sure is to take a photo and measure it. Take one photo
    using your lens's widest aperture, e.g. f/1.7, at ISO100 with long
    exposure noise reduction turned off, and send it to us along with
    the rest of the shots. If we detect that there is raw scaling (or if
    you detect it yourself if you do your own measurements) then we will
    ask you shoot a series of photos at every ISO value one stop apart,
    with an exposure time less than 0.5s, from the widest aperture your
    lens supports down every 1/3 of a stop until such an aperture where
    raw scaling is no longer performed. This could mean many photos.
    Handling raw scaling caused by large apertures is not very important
    so don't feel daunted by it, you don't need to do it even if your
    camera does do raw scaling, but if you have the time and bandwidth
    then it would be better to check for it.

At the very least, you should end up with a series of about 8 photos
from point 1. It is recommended that you take photos for both points 1
and 2, leading to about 16 photos, plus the one raw scaling test photo
from point 3. If it is found that your camera performs raw scaling, you
could additionally take the needed series described in point 3, but
since this could potentially mean many photos (e.g. 50 or more) it's not
expected.

Compress all these photos, upload them to
[filebin.net](http://filebin.net/) and send us the full link either
through our [GitHub](https://github.com/Beep6581/RawTherapee/issues/new)
page or in the [Forum](http://rawtherapee.com/forum).

Completely clipped photos can have amazing compression, don't forget to
compress them (7-Zip, ZIP, bzip2, whatever) before uploading! As an
example, 10 completely clipped Sony 7M2 raw files with long-exposure
noise reduction disabled weigh 234MB but if you ZIP them you get a 1MB
file.

## Details

For exact documentation, detailing the required photos and instructions
how to measure them, read the comments inside the camconst.json file:
<https://github.com/Beep6581/RawTherapee/blob/master/rtengine/camconst.json>