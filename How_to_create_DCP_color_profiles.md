## What are DCP profiles and why do I need them?

Technically, each photosite in a digital photography camera's [image
sensor](http://en.wikipedia.org/wiki/Image_sensor) outputs a certain
current based on the number of
[photons](http://en.wikipedia.org/wiki/Photon) of light that hit that
photosite. The current is converted into a number. These numbers, along
with some [metadata](http://en.wikipedia.org/wiki/Metadata), are stored
in what is known as a "[raw
file](http://en.wikipedia.org/wiki/Raw_image_format)". At this point
there is no concept of color and the raw data looks nothing like an
image. As in traditional photography, the image must be "developed" into
a usable form. One of the steps of this development involves translating
the numbers into accurate colors, and for that you need to profile the
camera, to map the numbers to specific known colors.

Practically, you must use a color profile in order to attain accurate
color reproduction, and currently the best way to go about this is using
a "DNG camera profile" (DCP for short - note that this is entirely
different to the other DCP which is the [Digital Cinema
Package](http://en.wikipedia.org/wiki/Digital_Cinema_Package)).
RawTherapee ships with profiles generated for
[D65](http://en.wikipedia.org/wiki/Illuminant_D65) daylight color
temperatures (derived from Adobe, from dcraw, made in-house, or from
you, the dear reader) and these are the basis for developing each raw
file you open. Furthermore, you can create your own DCP profiles
tailored to specific lighting situations for ultimate color accuracy.
Let's say you are shooting a wedding, or panoramas for a virtual tour.
You need accurate and consistent colors. The [color
spectrum](http://en.wikipedia.org/wiki/Color_spectrum) of the light
outside the building is completely different to that inside, and even
inside the light in each room will be different as the general consumer
light bulbs produce light of different temperatures and spectrums, and
there are usually a bunch of light bulbs illuminating a single room. If
you come prepared with a color calibration chart, such as the X-Rite
ColorChecker Passport 24-patch chart, all you need to do is to take a
photo of this chart in the same locations as your normal photos, one
shot per lighting situation (which usually translates to one shot per
room and outside), then generate DCP profiles from these shots and use
them in RawTherapee to achieve correct and consistent colors and [white
balance](http://en.wikipedia.org/wiki/White_balance) between all your
shots.

Find out more:

- QPcard article on ICC and DCP color profiles:
  <http://www.qpcard.com/dcp_icc_profile>
- X-Rite ColorChecker Passport product page:
  <http://xritephoto.com/ph_product_overview.aspx?id=1257>
- X-Rite ColorChecker Passport PDF manual:
  <http://www.xrite.com/documents/manuals/en/ColorCheckerPassport_User_Manual_en.pdf>

## Shooting the color chart

![](ColorChecker100423.jpg "ColorChecker100423.jpg") This guide assumes
you use the X-Rite ColorChecker Passport 24-patch chart.

There are two scenarios when you will want to shoot a chart:

1.  To provide RawTherapee with an accurate general-purpose D65 DCP
    profile for use by everyone with your camera model,
2.  To handle specific non-D65 lighting situations for yourself only.

In the former case, you will want to take extra care to make sure your
profile sticks to the requirements because many people will use it. In
the latter case, you will probably only use that profile on that
specific occasion, and it will be of no use to other people.

Shooting the color chart for inclusion in RawTherapee:

- We need photos in two light conditions: daylight (properly called "CIE
  Standard Illuminant D65", or "D65" for short) and tungsten (properly
  called "CIE Standard Illuminant A", or "StdA" for short).
- Wait for a clear, sunny day when the sun is high above the horizon,
  near the zenith at midday. You don't want stray colors in the spectrum
  which appear when the sun is near the horizon.
- Regarding the D65 shot, find a spot far away from anything that could
  reflect light. Your balcony is not a good spot - the walls will
  reflect light and negatively influence the light spectrum, even if you
  can't see that with your bare eyes. The park is not a good spot. A
  large, empty-ish parking, far away from walls and trees and parked
  cars, is a great place. Anything other than clear sunlight is bad.
  Forget about using a flash. Nothing matches real sunlight.
- Regarding the StdA shot, you need a real tungsten incandescent light
  bulb, the kind that were used everywhere until the world moved to
  compact fluorescent lamps in the last decade. Don't use fluorescent
  lights - even if they have a warm color, the light spectrum is
  absolutely different to tungsten. Don't use halogen lights. Don't use
  tinted bulbs. ![](Gluehlampe_01_KMJ.png "Gluehlampe_01_KMJ.png")
- For the D65 shot, position your color target so that it faces the sky
  at around 10-45 degrees. This ensures that the face of the target is
  evenly lit and that the light reflecting from the ground and nearby
  objects does not bounce off of it. Do not position it at 0 degrees,
  i.e. directly facing the sun, with the sun directly behind your head
  as you shoot the target, as then your chart is very likely to suffer
  from glare.
- For the StdA shot, use an angle of around 10 degrees. While the sun is
  far away and you could get away with tilting the chart 45 degrees when
  shooting D65, a light bulb will be close to you and due to the
  inverse-square law a chart tilted 45 degrees could suffer from uneven
  lighting. Don't use 0 degrees to avoid glare.
- Remove all filters from your lens.
- Set your lens to f/8, or to whichever aperture value is in your lens's
  sweet spot - it's usually around f/8. Don't go below f/5.6. This
  minimizes vignetting.
- Shoot at your camera's lowest base ISO, typically ISO100.
- Shoot raw. Exposure bracketing is acceptable and even recommended - it
  will help you/us find the best-exposed shot without clipping. Turn off
  anything which could influence the raw file, such as long exposure
  noise reduction.
- Make sure that the photos are sharp. The DCP generation software needs
  to be able to identify dust and scratches to isolate them, so do not
  shoot out-of-focus or with motion blur.
- Shoot the evenly-exposed chart so that it fills about a third of your
  frame - not more, not less. The center of the frame has the best
  optics and lowest vignetting.
- Open a new issue on the [RawTherapee GitHub
  page](https://github.com/Beep6581/RawTherapee/issues/new), upload your
  D65 and StdA raw photos using [Filebin](https://filebin.net/) and
  paste a link to them in your new GitHub issue. We are interested only
  in the raw photos, not in a ready-made DCP - we will make one
  ourselves. If you bracketed, you can upload a series of each and we
  will choose the best ones.

Shooting the color chart in specific lighting situations for yourself:

- As above, you will want the chart to fill a third of your frame, f/8,
  ISO100, sharp, though the points about light do not apply here. If
  you're shooting at an event at which you will take many photos under
  the same lighting conditions - business portraits, real estate, a
  series of images for a 360° panorama in the forest, or a wedding -
  take a shot of the chart just before (or after) you take your actual
  photos.

## Creating the DCP

There are several ways of creating a DCP. The simplest is using the
software that came bundled with the test target. The higher quality and
open-source alternative is using DCamProf.

### Creating DCP profiles using X-Rite software

Simply install the X-Rite ColorChecker Passport software bundled with
your chart (it works in Linux too using [wine](http://www.winehq.org/),
just follow the same steps as outlined for installing Adobe DNG
Converter in the [How to convert raw formats to
DNG](How_to_convert_raw_formats_to_DNG#Linux "wikilink") article) and
open your shot in it. It expects the shot to be in the DNG format, so
you should first [convert it to
DNG](How_to_convert_raw_formats_to_DNG#Linux "wikilink"). Using it is
straightforward, it's intuitive.

### Creating DCP profiles using DCamProf

DCamProf, written by Anders Torger, is a free and open-source command
line tool for generating camera profiles and performing tasks related to
camera profiles and profiling. Notably, it can generate profiles in both
the ICC and DNG formats, and it is capable of generating high quality,
smooth LUT profiles from CC24 shots or other targets.

The program's homepage has a full list of features and extensive, clear
documentation. Use that as your primary source of information. This
RawPedia article serves merely as a reference, to exemplify the process
of compiling the program (not necessary under Windows and macOS) and
using it to create a dual-illuminant DCP profile.

DCamProf homepage: <http://www.ludd.ltu.se/~torger/dcamprof.html>

Windows and macOS users can download a DCamProf binary and run it. Linux
users may need to compile it. Before compiling, make sure you have the
required dependencies: [LCMS2](http://www.littlecms.com/) and
[libtiff](http://www.remotesensing.org/libtiff/) Compiling is as simple
as downloading and uncompressing the source code of the latest version
of DCamProf, then going into the folder from a terminal and writing
"make".

You will also need [ArgyllCMS](http://www.argyllcms.com/) to be
installed as we need to use some of its tools. In the example code
below, its tools are prepended with "argyll-". This might not be so on
your system, e.g. in Gentoo and Sabayon the "scanin" tool executable is
called "argyll-scanin" while in Ubuntu its called "scanin". Adjust
accordingly.

To generate a dual-illuminant DCP profile from two ColorChecker Passport
shots:
![](Rt_colorchecker_dcamprof083.jpg "Rt_colorchecker_dcamprof083.jpg")

1.  Take two photographs of the color target as described above in the
    [Shooting the color
    chart](How_to_create_DCP_color_profiles#Shooting_the_color_chart "wikilink")
    section.
2.  For each of the two photos, do the following:

    Open the photo in the latest version of RawTherapee,

    Apply the Neutral profile,

    Rotate it so that the brown patch is in the top-left corner and the
    black one in the bottom-right corner,

    Crop at the corner markers,

    In the Color Management tool click "Save reference image for
    profiling", and in the window that appears make sure "Apply white
    balance" is not checked. Save the one as "daylight.tif" and the
    other as "tungsten.tif" to the same folder which contains the
    compiled "dcamprof" executable.
3.  Go into the folder with the compiled "dcamprof" executable and run:

<!-- -->

    argyll-scanin -v -dipn tungsten.tif /usr/share/argyllcms/ref/ColorChecker.cht data-examples/cc24_ref.cie tungsten-diag.tif
    argyll-scanin -v -dipn daylight.tif /usr/share/argyllcms/ref/ColorChecker.cht data-examples/cc24_ref.cie daylight-diag.tif
    ./dcamprof make-profile -i StdA tungsten.ti3 tungsten.json
    ./dcamprof make-profile -i D50 -C daylight.ti3 daylight.json
    ./dcamprof make-dcp -n "Pentax K10D" -n "Pentax K10D" -t acr -o neutral tungsten.json daylight.json "PENTAX K10D.dcp"

It is very important that during the make-dcp step you specify
tungsten.json first and daylight.json second!

In this example, the output file name is `PENTAX K10D.dcp`. You must use
the name exactly as RawTherapee identifies it. Simply open the D65 or
StdA photo in RawTherapee and toggle the "Quick info" panel (shortcut
key "i") to see which name RawTherapee identifies your camera as.

Your dual-illuminant DCP profile is ready for use.

To have RawTherapee automatically use your new DCP, place the DCP file
in the `dcpprofiles` folder. This folder will typically be inside the
RawTherapee installation folder in Windows, or in
`/usr/share/rawtherapee/dcpprofiles/` in Linux and macOS. Alternatively,
create a new default PP3 for raw files which uses your new DCP - see
[Creating processing profiles for general
use](Creating_processing_profiles_for_general_use "wikilink").

Per default DCamProf will smooth the LUT to prioritize smoothness over
accuracy. This makes the profile more robust for general-purpose use. If
you wish you can control all smoothing parameters manually but it's
generally not needed. See DCamProf's documentation for further
information.

## Inclusion of the color matrix in RawTherapee

The [Adding Support for New Raw
Formats](Adding_Support_for_New_Raw_Formats "wikilink") article covers
adding support for new raw formats and improving support of existing
formats.