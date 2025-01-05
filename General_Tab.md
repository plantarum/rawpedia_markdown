## Layout

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

## Default Language

Select the language for the GUI out of a list of thirty languages.
English (US) is the default ('mother') language, translations are based
on that one. On Win Vista/7 64bit you can have the language
automatically read from the operation system.

Again, a restart is required to change the language of the GUI.

## Default Theme

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

## Clipping Indication

When checked, the raw photo blinks at underexposed and overexposed
areas. The both threshold sliders determine at which values blinking
begins (0..255). In RawTherapee 4.0 the clipping indicators are
calculated on the final image in the output space selected for the
image. The clipping indicator takes the distance to the maximum/minimum
and renders these as grayscale values. Mention the clipping is only
calculated at the end of the processing chain. However, since
RawTherapee 4.0 has a floating point engine, there are fewer positions
within the processing chain where clipping can occur at all.

## Date Format

Determines the date format of the thumbnails in the file browser window.

## Pan Rate Amplification

Imagine a high resolution image is opened, and you are zoomed to 100%.
In order to move the image around (it's called "panning") you would have
to make multiple mouse movements (or have a very large mouse pad!).
RawTherapee saves you from this by using a "pan rate amplification" -
when set to 5, RawTherapee multiplies by 5 every pixel you pan by. If in
one comfortable mouse movement you'd normally move the cursor 500
pixels, with this option set to 5 you will have panned 2500 pixels.

The effect is most visible when you are zoomed in, and least visible
when zoomed out.

## External Editor

When you send a raw from within RawTherapee to an external editor for
further processing, RawTherapee needs to know which program you want to
use. If that's not the Gimp, you can specify the path to your favorite
photo editor here.

## About

Shows information about the original author of RawTherapee and the
current version, details of the build, names of developers and other
contributors and the licence under which RawTherapee is published:
[GPLv3](https://en.wikipedia.org/wiki/GPLv3)