You can access the Preferences window by clicking on the Preferences
button [image:Gtk-preferences.png](image:Gtk-preferences.png "wikilink")
which is either in the bottom-left corner of the RawTherapee window, or
the top-right one, depending on your [Editor tab mode
layout](The_Image_Editor_Tab#Editor_Tab_Modes "wikilink").

Note: When you start RawTherapee not just by clicking its shortcut but
by passing an image's filename as an argument so that the image is
opened directly, RawTherapee will run in "[no-File-Browser
mode](The_Image_Editor_Tab#Editor_Tab_Modes "wikilink")". The
Preferences button is missing when RawTherapee is in that mode. Getting
rid of that mode is on the TODO list, see [issue
2238](https://github.com/Beep6581/RawTherapee/issues/2238). To access
Preferences, be sure to start RawTherapee normally without passing any
filename arguments.

## About

Shows information about the original author of RawTherapee and the
current version, details of the build, names of developers and other
contributors and the licence under which RawTherapee is published:
[GPLv3](https://en.wikipedia.org/wiki/GPLv3)

## General Tab

### Layout

RawTherapee lets you use the following modes:

- Single Editor Tab Mode
- Single Editor Tab Mode, Vertical Tabs
- Multiple Editor Tabs Mode
- Multiple Editor Tabs Mode (if available on second monitor)

Remember that if you use multiple "Editor" tabs, each one takes a
substantial amount of RAM. Only use multiple Editor tabs if you have
quite a lot of RAM (exactly how much depends on what resolution your
images are, which tools you use, how many other programs you run in the
background, etc.).

A restart is required for these options to take effect.

### Default Language

Select the language for the GUI out of a list of thirty languages.
English (US) is the default ('mother') language, translations are based
on that one. On Win Vista/7 64bit you can have the language
automatically read from the operation system.

Again, a restart is required to change the language of the GUI.

### Default Theme

Choose between several themes for the GUI, from light to dark. The
effects are visible after a few seconds, so no need to restart here.
Checking 'Use System Theme' might change the appearance of RawTherapee,
although this depends on the platform and the window manager in use.
Just see if it works for you.

"Crop mask color/transparency" is the color of the area outside of a
crop. By clicking on the colored button, a new window appears where you
can also set transparency. If set to 75, the cropped area is still
somewhat visible. Useful to move the crop around and to find the best
composition (hold the **Shift** key and move the crop with the mouse).

Choose the font of your liking here. With smaller fonts more tools can
be displayed on the screen. You can also enable "Slim interface" to fit
some more tools into your screen space.

### Clipping Indication

When clipped highlight
[image:Warnhl.png](image:Warnhl.png "wikilink")/[image:Warnsh.png](image:Warnsh.png "wikilink")
shadow indication is enabled in the preview, areas which are clipped in
at least one channel are painted a solid color. The shade of this color
depends on how strong the clipping is. The threshold values determine
when clipping is considered to begin. The clipping indicators are
calculated on the final image in the output color space as selected for
that image in the [Color
Management](Color_Management#Output_Profile "wikilink") panel.

### Pan Rate Amplification

Imagine a high resolution image is opened, and you are zoomed to 100%.
In order to move the image around (it's called "panning") you would have
to make multiple mouse movements (or have a very large mouse pad!).
RawTherapee saves you from this by using a "pan rate amplification" -
when set to 5, RawTherapee multiplies by 5 every pixel you pan by. If in
one comfortable mouse movement you'd normally move the cursor 500
pixels, with this option set to 5 you will have panned 2500 pixels.

The effect is most visible when you are zoomed in, and least visible
when zoomed out.

### External Editor

You can have RawTherapee send the processed image directly to an
external program, e.g. an image viewer, an image editor or a script. You
do this using the
![<File:Image-editor.png>](Image-editor.png "File:Image-editor.png")
"[Edit Current Image in External
Editor](Edit_Current_Image_in_External_Editor "wikilink")" button in the
Editor tab under the main preview, see the [Saving](Saving "wikilink")
article. It is here in Preferences where you can customize which program
is to be sent this processed image when you click the button.

- Windows


If you use Windows, RawTherapee allows you to set up the path to GIMP,
Photoshop, and to one other external program ("Custom command line").

The recommended way of setting the GIMP option is by pointing
RawTherapee to the folder which contains the `bin` folder which contains
the GIMP executable, `gimp-2.*.exe`. If you use an unofficial version of
GIMP where the executable does not have that name, you may need to use
the command line option instead.

For the Photoshop option, point RawTherapee to the folder which contains
the Photoshop executable, `Photoshop.exe`

For the command line option, simply write the full path including the
executable. Don't worry about spaces or about escaping backslashes.
Environment variables such as `%ProgramFiles%` are not supported.

Examples:


`C:\Program Files\Gimp-2.9\gimp-2.9.exe`

`C:\Program Files\Digital Light & Color\Picture Window Pro 6.0\pw60.exe`

- Linux


If you use Linux, the GIMP option is hard-coded to look for the GIMP
executable `gimp` anywhere.

For the command line option, simply write the full path including the
executable. You may need to enclose the whole line in double quotation
marks if you need to pass arguments, see the example. Environment
variables such as `~` or `$HOME` are not supported.

Examples:


`"/usr/bin/geeqie --remote"`

: The above command opens the image in a single instance of Geeqie. Note that you need to enclose it in double quotation marks because you're passing the "--remote" option.

`/home/bob/programs/luminance hdr/luminance-hdr`

: The above command opens the image in Luminance HDR. No arguments or options passed so no quotation marks needed.

- macOS


If you use macOS, the GIMP option is hard-coded to `open -a GIMP` and
the Photoshop option is hard-coded to `open -a Photoshop`

For the command line option, write `open -a "External Program"` where
`"External Program"` is the name of the program you want to be used to
open the image. Surround the name of the program in quotation marks if
it contains one or more space characters.

Examples:


`open -a "Adobe Photoshop CS6"`

: The above command opens the image in Adobe Photoshop CS6. Note that you need to enclose it in quotation marks because it contains space characters.

`open -a "Affinity Photo Trial"`

: The command above opens the trial version of Affinity Photo. It too needed to be enclosed in quotation marks due to the spaces in the name.

`open -a "/My stuff/Programs/Pixel Mixer"`

: The command above opens a program called "Pixel Mixer" in the "My stuff" folder. We have reports that it is not necessary to write the full path to the program even if it does not reside in the standard `/Applications/` folder.

## Image Processing Tab

### Default Processing Profile

Specify which profile RawTherapee is to use when opening a raw photo and
when opening a non-raw photo. When you have made your own default
profile, you can tell RawTherapee to always use that one. To do that, to
have it show up in the list, you must save it to RawTherapee's
"*config*" folder. You can find out where it is on the [file
paths](File_paths#Processing_Profiles "wikilink") page.

The default processing profile for non-raw files like JPEG or TIFF is
best set to "Neutral". The "Neutral" profile just loads the photo as it
is, without applying anything like [Auto
Levels](Exposure#Auto_Levels "wikilink") or
[Sharpening](Sharpening "wikilink").

### Custom Processing Profile Builder

Executable (or script) file called when a new initial processing profile
should be generated for an image. The path of the communication file
(\*.ini style, a.k.a. "Keyfile") is added as a command line parameter.
It contains various parameters required for the executable or script to
allow a rules-based processing profile generation.

This feature is very powerful; for example it allows you to set lens
correction parameters or noise reduction based on image properties. It
is called just once on the first edit of the picture, or called manually
from the context menu when right-clicking on a thumbnail in the [File
Browser](The_File_Browser_Tab "wikilink") or
[Filmstrip](The_Image_Editor_Tab#The_Filmstrip "wikilink")

<b>Note:</b> You are responsible for using double quotes where necessary
if you're using paths containing spaces.

### Processing Profile Handling

"Save processing profiles next to the input file": When checked,
RawTherapee writes a PP3 file with all the edits you made to your photo
next to the input (raw) file. This represents your work (e.g. sharpening
settings used) and can be reloaded later.

"Save processing profiles to the cache": Instead of creating a PP3 file
next to the raw, this option - when checked - writes the PP3 to the
cache. When you check the last option only, chances are that you lose
your work (the edits) when installing RawTherapee on a new PC for
instance.

It's usually a good idea to only save the processing parameters next to
the input file, since you can e.g. back them up along with the your
raws.

### Dark-Frame

Specify the directory on your hard disk for searching for the dark frame
shots for long exposure noise subtraction. File with coordinates listing
of the bad pixels must be placed in the same directory for auto
correction.

### Flat-Field

Specify the directory on your hard disk for searching for the flat field
reference images.

### Metadata

The "Copy Exif/IPTC/XMP unchanged to output file" option changes
RawTherapee's metadata handling behavior.

- Enabled, it will copy Exif (including Makernotes), XMP and IPTC
  information from the input image into the output image unchanged. You
  will want to keep it enabled if you tag, rate, describe or caption
  your images in other software so that the image saved by RawTherapee
  will contain this information unchanged. However if you add, delete or
  change Exif or IPTC metadata using RawTherapee's "Meta" tab, then with
  this option enabled these changes will be lost - they will not be
  present in the saved image!
- Disabled, RawTherapee will save only that metadata in the output file
  which is enabled in the "Meta" tab - by default all metadata is
  enabled. If you add, delete or change Exif (including Makernotes),
  IPTC or XMP metadata using RawTherapee's "Meta" tab, then disable this
  option.

## File Browser Tab

### Image Directory at Startup

At the top you can define the image directory to use at startup. It
could be the RawTherapee installation directory, the last-visited
directory, the home directory, or a custom directory.

### File Browser / Thumbnail Options

These options determine which information is visible in the thumbnails
and how it should be displayed.

### Context Menu Options

Adjust the grouping of the right-click context menu in the [File
Browser](The_File_Browser_Tab "wikilink") (and
[Filmstrip](The_Image_Editor_Tab#The_Filmstrip "wikilink")).

### Parsed Extensions

Choose which files are recognized as images and displayes in the [File
Browser](The_File_Browser_Tab "wikilink"). All supported extensions are
set by default. They can be deactivated by unchecking the relevant box.
If a desired extension is missing you can easily add it by using the
plus button.

### Cache Options

These options influence the speed of thumbnail loading and generation.
These options are quite self-explanatory.

## Color Management Tab

The "Color Management" tab lets you define the directory where ICC
profiles can be found. You should also define the ICC profile of your
monitor when you've done a calibration. If you don't do it, the image
will be displayed with wrong colors.

The option "Automatically use operation system's main monitor profile"
is currently only supported on Windows, and it support only one monitor.
If you have multiple monitors connected, it will always take the main
monitor's profile (the one with the task bar).

On Mac OS X all displayed colors will be in [sRGB
space](https://en.wikipedia.org/wiki/SRGB), and then, if necessary,
converted by the native OS X color pipeline to match the screen
calibration, if any. This means that you cannot choose a monitor color
profile on OS X. Colors will be displayed correctly, even over multiple
screens, but if you have a wide-gamut screen RawTherapee's displayed
colors will still be limited to sRGB. This will however not affect
output, i.e. you can still produce images with colors outside the sRGB
space.

The Linux version does not support monitor profile auto-detection, but
as long as you load the same ICC profile as used in calibration the
colors will be managed and you will get full use of your wide gamut
monitor, if you have one. If you have more than one monitor with
different profiles you will have to choose a primary one for correct
color and have the RawTherapee window there.

### Rendering Intent

The "[Rendering
intent](https://en.wikipedia.org/wiki/Rendering_intent#Rendering_intent)"
drop-down lets you choose how the ICC profiles are used for translation
between gamuts or color spaces.

Perceptual
If the color gamut of your image is higher than that of your destination
device (monitor or printer) then it is compressed a bit to fit the gamut
of your device as far as possible. This might result in an image with
reduced saturation, but the hue is still kept. It might look a bit dull.
But this is not really that much visible as the color relations stay the
same. This method is activated by default (recommended).

<!-- -->

Relative Colorimetric
The colors existing in the color gamuts of both your image and your
device are kept and displayed 100% perfect. If the color does not exist
within the color gamut of your device the nearest possible value is
taken. This might lead to some banding effects, especially visible in
blue sky. The white point will be corrected.

<!-- -->

Saturation
Very similar to Perceptual, but here it is tried to keep the saturation
and change the hue instead. This is very useful for e.g. screenshots or
similar. It could also be used when you do not care about a possible
color shift as long the image does not look dull.

<!-- -->

Absolute Colorimetric
Similar to relative colorimetric. It tries to reproduce the exact colors
recorded in the original scene. The white point will not be corrected.
It is normally used, when the gamuts of your image and your device are
nearly the same. Used when exact reproduction of specific colors is
needed, e.g. fabric or logo colors.

## Batch Processing Tab

Batch processing is the capability of editing several images at the same
time in the [File Browser](The_File_Browser_Tab "wikilink") tab. That is
why there is a tool panel in the "File Browser". It looks the same as
the tool panel in the [Image Editor](The_Image_Editor_Tab "wikilink")
tab, but since it lets you tweak many files at once we refer to it as
the "batch tool panel". The checkboxes here have three states:
`[ ]` Disabled
`[✓]` Enabled
`[-]` Values differ across selected images.
Batch editing is done by selecting more than one image by using the
**Shift** or **Control** key in the [File
Browser](The_File_Browser_Tab "wikilink"), then you can edit those
images with the tools in the batch tool panel on the right. The way the
sliders' values are used to modify the image depends on the options set
in this "Batch Processing" tab.

When you select a single image, the sliders get the values of the
processing parameters of that specific image. These can be the values of
the default profile or the values from your last edit session of this
photo. If your image is currently being edited in an [Image
Editor](The_Image_Editor_Tab "wikilink") tab, the editor's values will
be reflected in real time in the batch tool panel, and vice versa, so
take care what you're doing.

When selecting more than one image in the "File Browser", the action of
the tool sliders depends on that tool's batch processing mode. Tools
which are not listed function as if they were in the "Set" mode.

The "Add" Mode
This mode may also be understood as "relative". Modifying sliders which
are set to the "Add" mode will result in the value of the modification
being added to the existing value. For example, if you select two images
by holding the **Ctrl** modifier key, one image which has an
[Exposure#Exposure_Compensation Exposure
Compensation](Exposure#Exposure_Compensation_Exposure_Compensation "wikilink")
of -0.5 EV and the other which has +1.0 EV, moving the "Exposure
Compensation" slider up to +0.3 will result in setting a value of -0.2
EV for the first image and +1.3 EV for the second one.

<!-- -->


Using the "Reset" button will move the slider to its default (zero)
position and will then bring back the initial value of that slider for
each selected image.

<!-- -->

The "Set" Mode
This mode may also be understood as "absolute". Modifying sliders which
are set to the "Set" mode will result in the value of the modification
being set, irrelevant of what the existing value was. If we use the same
example as before, moving the slider up to +0.3 EV will result in
setting a value of +0.3 EV for both images (one value for all images).

<!-- -->


Using the 'Reset' button will move the slider to its default position
(different for each slider), and will then reset this parameter for each
image.

<!-- -->

Overwrite Existing Output Files
The option "Overwrite existing output files" sets RawTherapee to
overwrite existing images. When disabled, existing images will not be
overwritten; instead, an index number is appended to the image being
saved.

e.g. If "output.jpg" exists and the option is not checked, the new image
will be saved as "output-1.jpg".

## Performance Tab

The "Performance" tab is only for people who know what they're doing. It
lets you poke under the hood and tweak the parameters of some tools.
These parameters take part in the balance between speed and stability.

### Maximum Number of Threads for Noise Reduction

The [Noise Reduction](Noise_Reduction "wikilink") algorithm in
RawTherapee is very powerful. It is also quite CPU and memory intensive.
People with weak hardware who experience crashes caused by running out
of RAM may find that tweaking this parameter prevents those crashes, at
the cost of longer processing time.

[Noise Reduction](Noise_Reduction "wikilink") has a baseline requirement
of 128MB of RAM for a 10 megapixel raw photo, or 512MB of RAM for a 40
megapixel one, and additionally 128MB of RAM per thread. The more
threads run in parallel, the quicker the computation, but higher the
memory requirement.

Most modern CPUs run two threads per physical core. Find out what CPU
you have and how many cores it has, multiply that by two, and you get
the maximum number of threads it would make sense to run simultaneously.
Let's call this number *T<sub>max</sub>*. You would not benefit from
running more threads than this - in fact you would likely suffer a small
speed penalty.

Setting this parameter to "0" will let your CPU figure out what
*T<sub>max</sub>* is, and use that. If you experience crashes due to
insufficient RAM, then you can calculate *T<sub>max</sub>* yourself and
use a number lower than that.

## Sounds Tab

The "Sounds" tab lets you set an audible notification when a lengthy
operation ends. It is currently only supported on Windows and Linux.

The "Queue processing done" sound is played after the last
[Queue](The_Batch_Queue "wikilink") image finishes processing. The
"Editor processing done" sound is played after a lengthy
in-[editor](The_Image_Editor_Tab "wikilink") operation that took longer
than the specified number of seconds is complete.

Sounds can be muted either by disabling the "Enabled" checkbox or by
setting fields with sound file references to blank values.

The "Queue" and "Editor processing done" text boxes can either point to
wave (.wav) files, or can specify one of the following values:

Windows:

- SystemAsterisk
- SystemDefault
- SystemExclamation
- SystemExit
- SystemHand
- SystemQuestion
- SystemStart
- SystemWelcome

Linux

- bell
- camera-shutter
- complete
- dialog-warning
- dialog-information
- message
- service-login
- service-logout
- suspend-error
- trash-empty
- possibly the name of any file in
  `/usr/share/sounds/freedesktop/stereo/`

### Sounds issues under Linux

RawTherapee relies on libcanberra to produce sounds.
If your sound installation works but that rawtherapee is unable to
produce sound,
you can check directly that libcanberra is working correctly by
compiling this sample:

    hello_world.sh
    --
    #!/bin/bash
    canberra-gtk-play -i phone-incoming-call -d "hello world"
    --

    chmod +x hello_word.sh
    ./hello_word.sh

If the hello_world produces sound, you can check rawtherapee by setting
"phone-incoming-call" in one of the boxes and try decoding an image.

Problems can arise if you installed pulseaudio, desactivated it (eg:
relying on alsa), the hello_world will mostly produce an error message
if this happends.