<figure>
<img src="Rt-5-misty1.jpg" title="Rt-5-misty1.jpg" />
<figcaption>Rt-5-misty1.jpg</figcaption>
</figure>

The Image Editor tab is where you tweak your photos. By default
RawTherapee is in "*Single Editor Tab Mode, Vertical Tabs*" (SETM) which
is more memory-efficient and lets you use the *Filmstrip* (described
below). You can switch to "*Multiple Editor Tabs Mode*" (METM) by going
to "*Preferences \> General \> Layout*", however each Editor tab will
require a specific amount of RAM relative to the image size and the
tools you use, and also the *Filmstrip* is hidden in this mode, so we
recommend you first give SETM a try.

## The Preview Panel

The central panel holds a preview of your photo. This preview is
generated from the actual raw data by processing it according to the
settings either you manually set, or those that are stored in the
[processing profile](Sidecar_Files_-_Processing_Profiles "wikilink")
used when opening that photo, as specified in "*Preferences \> Image
Processing \> Default Processing Profile*". The preview will show you
the effect of all the adjustments you make. Note that the effects of
some tools are only accurately visible when you are zoomed in to 1:1
(100%) or more. These tools are marked in the interface with a "1:1"
icon ![Zoom 100 identifier
icon](zoom-100-identifier.png "Zoom 100 identifier icon") next to the
tool's name.

The image you see in the preview is taken from the working profile's
color space and converted into the monitor profile's color space, if a
monitor profile is loaded, or into sRGB if one is not. It does not take
into account the "[Output
Profile](Color_Management#Output_Profile "wikilink")" section of the
"[Color Management](Color_Management "wikilink")" tool.

### Eek! My Raw Photo Looks Different than the Camera JPEG

After opening a raw photo you will notice that it looks different, often
worse - darker, less sharp, more dull, lacking contrast, more noisy -
than your camera's JPEG, or than the same raw photo when viewed in other
software. What gives? Witches, aliens, possums, or by design?

There are three things you must know first to understand what is
happening here:

1.  Your camera does not show you the real raw data when you shoot raw
    photos. It processes the raw image in many ways before presenting
    you with the histogram and the preview on your camera's digital
    display. Even if you set all the processing features your camera's
    firmware allows you to tweak to their neutral, "0" positions, what
    you see is still not an unprocessed image. Exactly what gets applied
    depends on the choices your camera's engineers and management made,
    but usually this includes a custom tone curve, saturation boost,
    sharpening and noise reduction. Some cameras, particularly low-end
    ones and [Micro Four-Thirds
    system](http://en.wikipedia.org/wiki/Micro_Four_Thirds_system), may
    also apply lens distortion correction to not only fix [barrel and
    pincushion
    distortion](http://en.wikipedia.org/wiki/Distortion_(optics)#Radial_distortion)
    but also to hide severe
    [vignetting](http://en.wikipedia.org/wiki/Vignetting) problems. Most
    cameras also underexpose every photo you take by anywhere from
    -0.3EV to even -1.3EV or more, in order to gain headroom in the
    highlights. When your camera (or other software) processes the raw
    file it increases exposure compensation by the same amount, making
    the brightness appear correct and hoping to recover some highlights
    in the process. RawTherapee shows you the real raw data which may
    mean your photos appear dark, so it is up to you whether you apply
    the required exposure increase and how you go about doing so,
    whether by using the Exposure Compensation slider or one of the
    various tone curves. Increasing exposure compensation makes noise
    more apparent regardless whether it is your camera or RawTherapee
    which does it, but other than this \[b\]RawTherapee does not "add
    noise"\![/b\] Many cameras apply noise reduction to the JPEGs
    (behind your back) to lower the noise level after increasing the
    exposure compensation, so you should expect there to be a difference
    between your out-of-camera JPEG and RawTherapee's image if noise
    reduction in RawTherapee is not enabled.
2.  Every DSLR raw file contains a processed JPEG image. Most raw files
    contain a JPEG image of the same full resolution as your camera can
    shoot, and some raw files contain as many as three JPEG images
    differing only in resolution. When you open raw files in other
    software, what you are usually seeing is **not** the raw data, but
    the embedded, processed JPEG image. Examples of software which are
    either incapable of or which in their default settings do not show
    you the real raw data:
    [IrfanView](http://en.wikipedia.org/wiki/IrfanView),
    [XnView](http://en.wikipedia.org/wiki/XnView),
    [Gwenview](http://en.wikipedia.org/wiki/Gwenview),
    [Geeqie](http://en.wikipedia.org/wiki/Geeqie), [Eye of
    GNOME](http://en.wikipedia.org/wiki/Eye_of_GNOME),
    [F-Spot](http://en.wikipedia.org/wiki/F-Spot),
    [Shotwell](http://en.wikipedia.org/wiki/Shotwell_(software)),
    [gThumb](http://en.wikipedia.org/wiki/GThumb), etc. It is worth
    mentioning at this point that if you shoot in "RAW+JPEG" mode, you
    are in fact wasting disk space and gaining nothing for it, as your
    raw files already contain the embedded JPEG files which you can view
    using the listed programs. The embedded JPEG may differ from an
    'external' one as saved using "RAW+JPEG" mode in compression.
3.  Most raw development programs (programs which do read the real raw
    data instead of just reading the embedded JPEG) apply some
    processing to it, such as a base tone curve, even at their most
    neutral settings, thereby making it impossible for users to see the
    real, untouched contents of their raw photos. Adobe Lightroom is an
    example. Comparing RawTherapee's real neutral image to a
    quasi-neutral one from these other programs will expose the
    differences.

RawTherapee, on the other hand, is designed to show you the real raw
image in the main preview, leaving the way you want this data processed
up to you. When you use the "Neutral" processing profile you will see
the demosaiced image with camera white balance in your working color
space with no other modifications. You can even see the non-demosaiced
image by setting the [demosaicing](demosaicing "wikilink") option to
"None". To provide you with a more aesthetically pleasing starting
point, we do ship a collection of processing profiles with RawTherapee.
After installing RawTherapee, the default profile for processing raw
photos is eponymously called "Default". We also ship the "Default ISO
Medium" and "Default ISO High" profiles which are designed to give a
good starting point to moderately noisy and very noisy images,
respectively.

None of the shipped profiles (at least none of the ones shipped in
RawTherapee 4.2) are designed to imitate your camera's look. Why not?
Every camera is different. My camera's image quality at ISO1600 could be
far noisier than your camera's. My camera's response to colors differs
from yours. Even the same camera can behave differently at various
settings. To provide such profiles, we would need access to raw files
for every supported camera model, often multiple raw files in various
shooting modes for a single camera, and countless
[person-hours](http://en.wikipedia.org/wiki/Man-hour). This may be
possible as a community effort, but it is not a job for a small team.
Even then, of what purpose would RawTherapee be if you ended up with a
camera JPEG look?

It is far more reasonable that you learn how to use the powerful tools
that RawTherapee provides to get the most out of your raws, to surpass
the camera look.

As of September 2015 we are starting to ship DCP input profiles made
using [DCamProf](http://www.ludd.ltu.se/~torger/dcamprof.html) which
include an [optional tone
curve](http://www.ludd.ltu.se/~torger/dcamprof.html#dcp_tone). This
curve is modeled after Adobe Camera Raw's default film curve and renders
a result similar to your "camera look". The reason we include the curve
in new DCP profiles is because it makes for a good vibrant starting
point (as opposed to the flat look of using the "Neutral" processing
profile) without having to use [Auto
Levels](Exposure#Auto_Levels "wikilink") and without having to touch any
of the other tools, and it is entirely optional. Do read the article on
[input profiles](Color_Management#Input_Profile "wikilink"). If we ship
a DCP for your camera model which includes the tone curve, the "Tone
curve" checkbox in Color Management \> Input Profile \> DCP will be
clickable. Applying the (Neutral) processing profile will disable the
tone curve. While the input color profile is applied at the first stages
of the [toolchain pipeline](Toolchain_Pipeline "wikilink"), the DCP tone
curve is applied later in the pipeline at some point after the Exposure
tool.

You can create a processing profile ideally tailored to your camera and
lens combination, and set RawTherapee to use it by default on your raw
photos. See the [Creating processing profiles for general
use](Creating_processing_profiles_for_general_use "wikilink") article to
learn how.

### Preview Modes

In addition to the normal preview, RawTherapee supports a number of
other preview modes to help you tweak your photos. Preview modes are
controlled via buttons in the *Editor* toolbar or via [keyboard
shortcuts](Keyboard_Shortcuts "wikilink"). Only one preview mode can be
engaged at a time.

<div style="float: right">

<table>
<caption>align="bottom" | * The preview is returned to normal by
deselecting any other mode.</caption>
<thead>
<tr class="header">
<th><p>Preview Mode</p></th>
<th><p>Shortcut</p></th>
<th><p>Button</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="padding:10px;"><p>Regular*</p></td>
<td></td>
<td><figure>
<img src="preview_mode_1_regular.png"
title="Image:preview mode 1 regular.png" />
<figcaption>Image:preview mode 1 regular.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td style="padding:10px;"><p>Red channel</p></td>
<td style="text-align: center;"><p>r</p></td>
<td><figure>
<img src="preview_mode_2_red.png"
title="Image:preview mode 2 red.png" />
<figcaption>Image:preview mode 2 red.png</figcaption>
</figure></td>
</tr>
<tr class="odd">
<td style="padding:10px;"><p>Green channel</p></td>
<td style="text-align: center;"><p>g</p></td>
<td><figure>
<img src="preview_mode_3_green.png"
title="Image:preview mode 3 green.png" />
<figcaption>Image:preview mode 3 green.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td style="padding:10px;"><p>Blue channel</p></td>
<td style="text-align: center;"><p>b</p></td>
<td><figure>
<img src="preview_mode_4_blue.png"
title="Image:preview mode 4 blue.png" />
<figcaption>Image:preview mode 4 blue.png</figcaption>
</figure></td>
</tr>
<tr class="odd">
<td style="padding:10px;"><p>Luminance channel</p></td>
<td style="text-align: center;"><p>v</p></td>
<td><figure>
<img src="preview_mode_5_luminance.png"
title="Image:preview mode 5 luminance.png" />
<figcaption>Image:preview mode 5 luminance.png</figcaption>
</figure></td>
</tr>
<tr class="even">
<td style="padding:10px;"><p>Focus Mask</p></td>
<td style="text-align: center;"><p>Shift+f</p></td>
<td><figure>
<img src="preview_mode_6_focus.png"
title="Image:preview mode 6 focus.png" />
<figcaption>Image:preview mode 6 focus.png</figcaption>
</figure></td>
</tr>
</tbody>
</table>

align="bottom" \| \* The preview is returned to normal by deselecting
any other mode.

</div>

The following preview modes are currently supported:

- Red channel,
- Green channel,
- Blue channel,
- Luminosity, which is calculated as 0.299\*R + 0.587\*G + 0.114\*B,
- Focus mask, to see which areas are in focus

Image:Preview_1_regular.jpg\|Regular Image:Preview_2_red.jpg\|Red
Image:Preview_3_green.jpg\|Green Image:Preview_4_blue.jpg\|Blue
Image:Preview_5_luminosity.jpg\|Luminosity
Image:Preview_6_focus.jpg\|Focus Mask

#### Red, Green, Blue and Luminosity Preview Modes

When clipping indicators are engaged in the RGBL preview modes, shadow
clipped areas are indicated in a blue color and highlight clipping is
indicated in red. As during normal preview, the lightness of the
clipping highlight is indicative of the degree of clipping.

Preview of individual channels may be helpful when editing RGB curves,
planning black/white conversion using the channel mixer, evaluating
image noise, etc. Luminosity preview is helpful to instantly view the
image in black and white without altering development parameters, to see
which channel might be clipping or for aesthetic reasons.

#### Focus Mask

![Focus mask indicating the focusing
plane](Preview_6_focus_2.jpg "Focus mask indicating the focusing plane")
The focus mask is designed to highlight areas of the image which are in
focus. Naturally, focused areas are sharper, so the sharp areas are
being highlighted. The focus mask is more accurate on images with a
shallow depth of field, low noise and at higher zoom levels.To improve
detection accuracy for noisy images evaluate at smaller zoom, around the
10-30% range. Note that the preview is rendered more slowly when the
focus mask is enabled.

The current implementation analyzes the preview image which is rescaled
from the original captured size. This process of rescaling reduces the
noise and is helpful to identify truly sharper details rather than noise
itself which may also contain micro texture. At the same time, rescaling
of the original image to the preview size compresses larger scale
details into a smaller size, and it may introduce aliasing artifacts,
both of which could lead to false positives. You can increase your
confidence by viewing the mask at various zoom levels. It is not always
fault proof, but can be helpful in many cases.

**Warning**: Be sure to double-check your images if you decide to delete
them based on the focus mask.

### Background color of the preview

The background color of the preview panel surrounding the image area may
be changed to ease image preview during editing and to better visualize
image cropping. A vertical stack of three thin buttons in the preview
modes toolbar above the image preview panel allows to set the background
color of the area around the photo preview.

<div align="center">

<table>
<thead>
<tr class="header">
<th><p>Preview<br />
Background</p></th>
<th><p>Shortcut</p></th>
<th><p>Button</p></th>
<th><p>Preview Background<br />
and Crop Visualization</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Theme-based</p></td>
<td style="text-align: center;"><p>8</p></td>
<td><figure>
<img src="Previewback_7_theme.png"
title="Image:Previewback_7_theme.png" />
<figcaption>Image:Previewback_7_theme.png</figcaption>
</figure></td>
<td><figure>
<img src="Previewback_flower_theme.png"
title="Previewback_flower_theme.png" width="180" />
<figcaption>Previewback_flower_theme.png</figcaption>
</figure></td>
<td><p>The cropped area of the image is masked with a theme-based color.
The cropped area visibility is based on the crop mask color and
transparency as set in "<em>Preferences &gt; Default Theme &gt; Crop
mask color/transparency</em>".</p></td>
</tr>
<tr class="even">
<td><p>Black</p></td>
<td style="text-align: center;"><p>9</p></td>
<td><figure>
<img src="Previewback_8_black.png"
title="Image:Previewback_8_black.png" />
<figcaption>Image:Previewback_8_black.png</figcaption>
</figure></td>
<td><figure>
<img src="Previewback_flower_white.png"
title="Previewback_flower_white.png" />
<figcaption>Previewback_flower_white.png</figcaption>
</figure></td>
<td><p>The cropped area of the image is masked with black.</p></td>
</tr>
<tr class="odd">
<td><p>White</p></td>
<td style="text-align: center;"><p>0</p></td>
<td><figure>
<img src="Previewback_9_white.png"
title="Image:Previewback_9_white.png" />
<figcaption>Image:Previewback_9_white.png</figcaption>
</figure></td>
<td><figure>
<img src="Previewback_flower_black.png"
title="Previewback_flower_black.png" />
<figcaption>Previewback_flower_black.png</figcaption>
</figure></td>
<td><p>The cropped area of the image is masked with white.</p></td>
</tr>
</tbody>
</table>

</div>

### Detail Window

The "New detail window" button
![Image:new-detail-window.png](new-detail-window.png "Image:new-detail-window.png"),
situated below the main preview next to the zoom buttons, opens a new
viewport over the main preview of an adjustable size and of adjustable
zoom. This lets you work on the photo zoomed-to-fit while examining
several areas of interest at a 100% zoom (or even more). The benefit of
using this feature is particularly important to users with slower
machines, though not only them, as the zoomed-out main preview takes a
shorter amount of time to update than if you were to zoom it to 100%
because working at a zoom level less than 100% excludes certain slow
tools, such as Noise Reduction, while the little detail windows zoomed
to 100% do include all tools and are fast to update because of their
small size. This allows you can use the main preview for your general
exposure tweaks where it is necessary to see the whole image, and one or
more detail windows to get sharpening and/or noise reduction just right.

### Preview refresh delay

Changing any tool's parameters sends a signal for the preview image to
be updated accordingly. Imagine what would happen if there was no "delay
period", and you dragged, for example, the exposure slider from 0.00 to
+0.60. A signal would be sent to update the preview for every single
change of that value - for +0.01, +0.02, ... +0.59, +0.60. Updating the
preview 60 times would be completely unnecessary and actually take
longer than it takes you to move the slider. This is especially true for
more complicated tools, such as noise reduction, where a preview update
can take even a second (depending on your CPU and preview size). The
solution is to introduce a very short delay during which parameter
changes are ignored, and the signal to update the preview is sent only
after no parameter change has been registered after this time.

We have introduced two such paramters:

AdjusterMinDelay
Default value = 100ms.

This is the minimum time to wait before the preview is refreshed.

AdjusterMaxDelay
Default value = 200ms.

This is the maximum time to wait before the preview is refreshed. If you
keep changing a parameter, RawTherapee will not wait longer than this
short time period before triggering a preview refresh. While the minimum
delay is there to prevent overloading your CPU with unnecessary preview
refreshes, this delay is to guarantee that you can see what happens to
the image as you slowly change some parameter.

You can adjust both of these values in the options file in the [config
folder](File_Paths "wikilink").

## The Left Panel

To the left is a panel which optionally shows the main histogram
("*Preferences \> General \> Layout \> Histogram in left panel*"), and
always shows the *Navigator*, *History* and *Snapshots*. You can hide
this panel using the ![Hide left panel
icon](panel-to-left.png "Hide left panel icon") hide icon, or its
[keyboard shortcut](Keyboard_Shortcuts "wikilink").

### Main Histogram

![](Rt_histogram_crop_scale-off.png "Rt_histogram_crop_scale-off.png")
![](Rt_histogram_crop_scale-on.png "Rt_histogram_crop_scale-on.png")
![](Rt_histogram_raw.png "Rt_histogram_raw.png")
![](Rt_histogram_rgbindicator.png "Rt_histogram_rgbindicator.png")

The main histogram can show the histograms of the red
![Image:histRed.png](histRed.png "Image:histRed.png"), green
![Image:histGreen.png](histGreen.png "Image:histGreen.png"), blue
![Image:histBlue.png](histBlue.png "Image:histBlue.png"), CIELab
Luminance ![Image:histValue.png](histValue.png "Image:histValue.png")
and [Chromaticity](http://en.wikipedia.org/wiki/Chromaticity)
![Image:histChro.png](histChro.png "Image:histChro.png") channels of the
photo as it would look if you saved it. Use this information to prevent
clipping in your end result. If the raw image has no clipping but the
end result does, you can easily identify the channel(s) that need
adjusting and take the needed steps to prevent it, if it is undesirable.

It can show you the histogram of the raw data
![Image:histRaw.png](histRaw.png "Image:histRaw.png") before any
transformations such as demosaicing are applied to it. Use this
information to see whether there is any clipping in the raw image.
Clipped raw data cannot be recovered. Some clipped highlights can be
[reconstructed using the Color Propagation
method](Exposure#Highlight_Reconstruction "wikilink").

When there is a disproportionately bright area relative to the rest of
the image, this will show up as a spike in the histogram. If you want to
show this on a linear histogram, unscaled in the y-axis, you will
sacrifice seeing the low levels in order to fully show the spike. You
can toggle scaling of the histogram in the y-axis
![Image:histFull.png](histFull.png "Image:histFull.png") to help deal
with this, then high values will be scaled down so that you may better
see the rest of the histogram.

You can show or hide the RGB Indicator Bar
![Image:histBar.png](histBar.png "Image:histBar.png"), which is situated
under the histogram and shows you the exact place on the histogram of
the R, G, B or L values of the pixel your cursor is currently hovering
over in the main preview.

The histogram can be moved to the left/right panel from "*Preferences \>
General \> Layout \> Histogram in left panel*".

The values the main histogram and Navigator panel shows are either those
of the working profile, or of the gamma-corrected output profile. You
can choose which you prefer in "*[Preferences \>
General](Preferences#General_Tab "wikilink") \> Use working profile for
main histogram and Navigator*".

### Navigator

The *Navigator* panel shows a thumbnail of the currently opened image,
and RGB, HSV and Lab values of the pixel your cursor is currently
hovering over.

The values the main histogram and Navigator panel shows are either those
of the working profile, or of the gamma-corrected output profile. You
can choose which you prefer in "*[Preferences \>
General](Preferences#General_Tab "wikilink") \> Use working profile for
main histogram and Navigator*".

<div style="clear: both">
</div>

### History

Under the *Navigator* it is the *History* panel. While editing a photo,
all your actions are recorded in this *History* panel. By clicking on
the different entries, you can step back and forth through the different
stages of your work.

### Snapshots

Under the *History* panel is a panel called *Snapshots*. Its use is in
that you can save a snapshot of the photo with all the adjustments up to
that point in time, and then proceed to further modify your photo to
give it a different appearance, saving new snapshots at every moment you
feel you might have reached a version of your photo worth saving. Once
you have two or more snapshots, you can just click on them to flip
through the different versions and stick with whichever one you like
best. In the future, the snapshots will be saved to the PP3 sidecar
file. For now, the history and snapshots are lost when you load a new
photo in the *Image Editor* or close RawTherapee.

## The Right Panel

To the right is a panel which optionally shows the main histogram and
*Processing Profiles* selector ("*Preferences \> General \> Layout \>
Histogram in left panel*"), and always shows the
[Toolbox](Toolbox "wikilink"). You can hide this panel using the ![Hide
right panel icon](panel-to-right.png "Hide right panel icon") hide icon,
or its [keyboard shortcut](Keyboard_Shortcuts "wikilink").

### Processing Profile Selector

The *Processing Profiles* drop-down list lets you apply bundled or
custom [processing
profiles](Sidecar_Files_-_Processing_Profiles "wikilink"). See the [File
Paths](File_Paths "wikilink") article for information on where these
processing profiles reside on your system.

Pay attention to the "*Processing profile fill mode*" button!

"Fill" mode [image:Profile-filled.png](image:Profile-filled.png "wikilink")
When the button is activated and you open a partial profile, the missing
values will be replaced with RawTherapee's hard-coded default values.

For instance if you apply a partial profile which contains only
sharpening settings, all of the remaining tools (such as Exposure, Tone
Mapping, Noise Reduction, Resize, etc) will pop into their default
positions.

"Preserve" mode [image:Profile-partial.png](image:Profile-partial.png "wikilink")
If the button is deactivated and you open a partial profile, only those
values in the profile will be applied, and the missing ones remain
unchanged.

For instance if you apply a partial profile which contains only
sharpening settings, only those sharpening settings will be applied, and
your other tools remain unchanged.

The state of this button will make no difference if you apply a full
profile, but most of the profiles bundled with RawTherapee are partial
(for good reason).

### Toolbox

The *Toolbox*, in the right panel, contains all the tools you use to
tweak your photos. Each tool has its own RawPedia article.

## Editor Tab Modes

RawTherapee allows you to work on photos in two modes:

- *Single Editor Tab Mode* (SETM), where you work only on one photo at a
  time, and each photo is opened in the same *Editor* tab. There is a
  horizontal panel called the
  *[Filmstrip](The_Image_Editor_Tab#The_Filmstrip "wikilink")* at the
  top of the *[Editor](The_Image_Editor_Tab#The_Filmstrip "wikilink")*
  tab showing the rest of the photos in that folder for easy access.
  There are *Previous Image* and *Next Image*
  ![<File:Nav-prev.png>](Nav-prev.png "File:Nav-prev.png")
  ![<File:Nav-next.png>](Nav-next.png "File:Nav-next.png") buttons in
  the bottom toolbar (and [keyboard
  shortcuts](Keyboard_Shortcuts "wikilink") for them) to switch to the
  previous/next image.
- *Multiple Editor Tabs Mode* (METM), where each photo is opened in its
  own *[Editor](The_Image_Editor_Tab#The_Filmstrip "wikilink")* tab. The
  *[Filmstrip](The_Image_Editor_Tab#The_Filmstrip "wikilink")* is hidden
  in this mode and there are no previous/next buttons. Having multiple
  photos opened at the same time requires more RAM.

Try both modes and see which one suits you best. To do that, click on
the *Preferences* icon ![Preferences
icon](Gtk-preferences.png "Preferences icon") in the bottom-left or
top-right corner of the RT window, choose "*General \> Layout*" and set
*Editor Layout* to your preferred choice.

Use this *Preferences* window to select a different language for the
user interface, to choose a different color theme, change the font size,
etc.

It is also possible to start RawTherapee in no-File-Browser-mode
(without the *File Browser* tab) by specifying RawTherapee to open an
image from your operating system's file browser (in other words,
right-click on a photo and select "*Open With \> RawTherapee*"), or by
using the image filename as an argument when starting RawTherapee from
the command line (`rawtherapee /path/to/some/photo.raw`). This mode was
introduced for people with little RAM as not having a *File Browser* tab
means RawTherapee uses a little less memory, however in practice the
amount of memory saved is little and the usability cost outweighs the
little benefit, so it is likely to be removed in the future (see [issue
2254](https://code.google.com/p/rawtherapee/issues/detail?id=2254)).

## The Filmstrip

![](Rt_filmstrip_21_toolbar-visible.jpg "Rt_filmstrip_21_toolbar-visible.jpg")
![](Rt_filmstrip_21_toolbar-hidden.jpg "Rt_filmstrip_21_toolbar-hidden.jpg")

If you use *Single Editor Tab Mode* ("*Preferences \> General \>
Layout*") you can display a horizontal panel above the preview, this is
called the *Filmstrip*. It contains thumbnails of all images in the
currently opened album, and is synchronized with the currently opened
image so that you can use [keyboard
shortcuts](Keyboard_Shortcuts "wikilink") or the previous ![Open
previous image icon](nav-prev.png "Open previous image icon") and next
![Open next image icon](nav-next.png "Open next image icon") image
buttons to open the previous/next image without needing to go back to
the *[File Browser](The_File_Browser_Tab "wikilink")* tab.

As of RawTherapee version 4.2.10, you can hide the Filmstrip's toolbar
to save screen space. There are two ways of doing this: one way just
toggles the toolbar on/off without resizing the filmstrip to the new
height, and the other way does the same but also automatically resizes
the filmstrip's height. Both are invoked via [keyboard
shortcuts](Keyboard_Shortcuts "wikilink") only. As resizing the
filmstrip's height will trigger a refresh of the image preview and this
might take a while if using CPU-hungry tools like noise reduction while
zoomed in at 100%, the mode that doesn't resize has been implemented for
users with slow machines. Users with fast machines will find the
auto-resizing mode more helpful.


== Monitor Profile and Soft-Proofing == The widgets under the main
preview in RawTherapee 5 allow you to apply a monitor color profile to
the preview image. This enables users who have calibrated and profiled
their monitors to get an instant and accurate preview of their work,
whether you're staying in sRGB or working in a wide gamut. Note: OS X
users are limited to sRGB and will not get an accurate preview otherwise
([see
discussion](https://discuss.pixls.us/t/wide-gamut-preview-in-os-x/2481)),
while users of Linux and Windows will get a correct wide-gamut preview.

Go to Preferences \> [Color
Management](Preferences#Color_Management_Tab "wikilink") and point the
"Directory containing color profiles" to the folder into which you saved
your monitor ICC profile. Restart RawTherapee for the changes to take
effect. Now you will be able to select your monitor's color profile in
the combo-box under the preview. Use the "Relative Colorimetric"
rendering intent unless you have a good reason otherwise.

One can also enable soft-proofing of the preview. This will show you
what your image will look like once it gets transformed by the output
profile in the "[Color
Management](Color_Management#Output_Profile "wikilink")" tool. If you
want to adjust an image for printing and you have an ICC profile for
your printer-paper combination you could set that as your output
profile, enable "Black point compensation" so that the blackest black in
your image will match the blackest black your printer-paper combination
is capable of reproducing, then enable soft-proofing. You will see what
your image will look like if you print it. This allows you to make
adjustments and get an instant preview of the result, saving you time
and ink on test prints.

You should have a calibrated and profiled monitor in order for the
soft-proofing preview to be accurate.

The items you see in the monitor profile combobox (under the main
preview) and in the output profile combobox (in the [Color
Management](Color_Management "wikilink") tool) are ICC files located in
a folder which you can point RawTherapee to by going to
"[Preferences](Preferences "wikilink") \> [Color
Management](Preferences#Color_Management_Tab "wikilink") \> Directory
containing color profiles".