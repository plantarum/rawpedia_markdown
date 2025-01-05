**This article is important** - some things may sound obvious if you are
an experienced user, but some things are guaranteed to be unknown to you
and knowing them will let you use RawTherapee faster and easier. Take
five minutes to read it!

<hr>

The panel on the right side of the preview contains the controls for all
the tools available in RawTherapee. They can do a lot, perhaps even more
than you ever may want to! If you're new to RawTherapee or new to raw
processing in general, don't feel overwhelmed, as there is no need to
touch all those sliders to get decent results. In this section you'll
find a brief description of what all those tools are for, tab after tab.

## Panels

A panel is a foldable element which contains buttons, tool, histograms,
etc. The Editor tab has three main panels: the one on the left which
contains the history, the one on the right which contains the tools, and
if you're in "Single Editor Tab Mode" the one on the top which contains
the [Filmstrip](The_Image_Editor_Tab#The_Filmstrip "wikilink"). They can
be hidden away from view with the little arrow buttons or using
[keyboard shortcuts](Keyboard_Shortcuts "wikilink"), making more room
for the image preview.

You can use the mouse scrollwheel to safely scroll up/down in the panels
without fear of accidentally changing a slider, because RawTherapee
requires that you hold the Shift key while using the mouse scrollwheel
if your intention is to manipulate a slider or cycle through the options
in a drop-down menu (called a "combobox").

## Tools

RawTherapee has many tools, and each tool has one or more controls, or
[widgets](https://en.wikipedia.org/wiki/Widget_(GUI)), which you can
turn or move or push or slide to make the program do something. They are
divided up among the Exposure, Detail, Color, Wavelet, Transform, Raw
and Metadata tabs, for example the Exposure tab has tools which deal
with exposure, such as the Exposure tool and the Shadows/Highlights
tool, etc., the Color tab has the White Balance tool, and so on.

Because there are so many tools, you will notice that vertical screen
space is precious, and you will at times hide some tools to see others.
RawTherapee makes this easy. Right-clicking over a tool's title expands
it and collapses all other tools of the same tab. You'll learn to love
this shortcut when you consider the time you would have spent on folding
tools manually...

To the left of most tools' titles is a button which lets you enable or
disable the corresponding tool. The concept of being enabled or disabled
doesn't always make sense - for example what would it mean for the White
Balance tool to be disabled? There must always be some white balance
being used - so these tools instead of an enabled/disabled button just
use a triangle symbol to let you expand or collapse them. Lastly, you
will notice that in the File Browser tab if you select several photos
then the power button can have a third state which looks only
half-enabled - this state, called "inconsistent", means that the tool in
question is not enabled in all of the selected photos.

![Tool disabled.](expanderDisabled.png "Tool disabled.") Tool disabled.

![Tool enabled.](expanderEnabled.png "Tool enabled.") Tool enabled.

![Tool inconistent.](expanderInconsistent.png "Tool inconistent.") Tool
inconistent.

![Tool collapsed.](expanderClosed.png "Tool collapsed.") Tool collapsed.

![Tool expanded.](expanderOpened.png "Tool expanded.") Tool expanded.

## Sliders

Each slider has three values in memory:

- The current value, when you move the slider to any position,
- The 'default' value, the one that the programmer has set as default.
  It can be called back by clicking on the 'Reset' button,
- The 'initial' value, which is the value of the profile used when the
  image was loaded in the editor. It can be called back by
  **Control-clicking** on the 'Reset' button.

As written above, if you want to move a slider using the mouse
scrollwheel, or cycle though a combobox, make sure you hold down the
Shift key while doing so, otherwise instead of moving the slider you
will scroll up/down in the panel.

## Curve Editors

RawTherapee has three types of curve editors – for Threshold Curves,
Tone Curves and Flat Curves. They are discussed below along with some
general pointers.

### Threshold Curves

Threshold Curves are the simplest. They are used to tell a RawTherapee
tool the tones (or hues or saturations values) that you want processed
(or processed differently).

As an example, consider the Threshold curve editor on the Detail -\>
[Sharpening](Sharpening "wikilink") tool.
![](_Sharpening_Threshold.png "_Sharpening_Threshold.png") The setting
shown is telling the Sharpening tool to phase in sharpening quickly in
the black areas (the steep line up on the left), maintain full
sharpening through mid-tones (the plateau area) and then phase out
sharpening slowly in the highlights (the long slope down). Dragging one
of the control points will move the slope leading up or down from the
point. To just move the point, but not the slope as a whole, hold down
the shift key while you drag.

On the top right is a reset button that will reset back to default.

**Warning:** resetting the curve is considered a curve modification, so
if you've just modified the curve and mistakenly pressed the *Reset*
button, there's no way to bring back your curve. (Ctrl-z will go one
step before in the *History* list, not in the curve's edition). This
comment applies to Tone and Flat Curves as well.

You’ll also find Threshold Curves used in the [Contrast by Detail
Levels](Contrast_by_Detail_Levels "wikilink") and the
[Vibrance](Vibrance "wikilink") tools.

You may have noticed that Threshold Curves actually consist of a few
straight lines rather than a curve. If this bothers you, you might want
to take a break before moving on to Flat Curves.

### General Comments on Tone and Flat Curves

Tone and Flat Curves are more powerful than Threshold Curves and have
some controls that aren’t needed on Threshold Curves.

Each Tone or Flat curve editor has a button to select its type. It's a
so-called 'Toggle' button, i.e. it will stay pressed or stay released
after each click on it. Toggling on/off the curve's button will
respectively display/hide its associated editor. This is very handy and
saves a lot of space when handling groups of curves (e.g. see the Lab
curve editor).

These curves have a Reset button on the right which will reset the
displayed (or pressed button) curve only.

They also have a pipette tool and a node in/out value input tool, which
deserve sections of their own.



#### Pipette

[thumb](image:rt_pipette_2_lab_ba.jpg "wikilink") Most curves in
RawTherapee have a pipette button
[image:editmodehand.png](image:editmodehand.png "wikilink"). This
feature is a great way to target specific hues, tones and areas of a
particular saturation, and using it will make tweaking your images
easier and faster. Let's say you want to change the purple hue of a
flower, to make it more red. Without the pipette, you would have to
guess the exact shade of the hue, else the affected range of hues would
be too wide and you might end up changing something you did not want to
change. With the pipette, you simply click on the flower, and a point
appears in the relevant curve. You can adjust this point to your liking,
knowing it represents the exact hue you want affected.

The pipette tool must be activated for each curve, simply by clicking on
it. Now when you hover the cursor over the main preview you will notice
that a vertical line (or even four of them) appears in the curve panel.
This line represents the value of interest of the pixels you're hovering
over. To place an adjustment point in the curve for the value you're
hovering over, Ctrl+leftclick in the preview, and a dot appears in the
curve. You can adjust that point without leaving the preview area, just
keep holding the left mouse button after you placed the curve point, and
moving the mouse up and down moves the point up and down. Remember that
holding Ctrl while editing a curve point decreases your mouse speed so
that you can very finely adjust points, but usually you will not need
this, so after Ctrl+leftclicking to place the point, let go of Ctrl, but
keep holding the left mouse button.

To deactivate the pipette, either right-click anywhere in the preview
area, or left-click on the same pipette's button again.

You do not need to deactivate the previous curve's pipette to use it on
a new curve, just activate it as usual, and the old one automatically
deactivates.



#### Curve Node In/Out Value

Introduced in version 4.2.192, each curve has a node in/out value input
tool. You can use this tool for example to match node values on a photo
of a color target with known patch values.

The tool works with nodes, and the most likely way you will create these
nodes is by using the pipette. For this example, we will start with a
curve without any nodes and create some using the pipette. Click the
node value editor button
[image:Gtk-edit.png](image:Gtk-edit.png "wikilink") next to the curve,
and also click the pipette's button
[image:editmodehand.png](image:editmodehand.png "wikilink"). You will
now see "I" (in) and "O" (out) values displayed under the curve. They
correspond to the point under the mouse cursor if you hover it over the
curve. Hover the cursor over the image preview. Since you activated the
pipette, you can Ctrl+click on a spot in the preview area to place a
node which corresponds to that spot's value in the curve (whatever that
value may be - for example for the L\* curve, the value is the internal
value of the pixel you've placed the spot over at that point in
RawTherapee's internal pipeline, and the output value is that value
affected by your curve). Do that, Ctrl+click on a spot in the preview. A
node appears in the curve. To edit the node's in/out values, right-click
on the node. It turns red with a red ring around it. Now you can edit
the in/out values and see the node move in real-time. Once you are done
editing, either right-click anywhere inside the curve area other than on
the node to go out of node editing mode, or just click the node value
editor button again to deactivate it.

### Tone Curves

Tone Curves are somewhat misnamed since, while some are used to adjust
tones, others are used to adjust saturation, chromaticity or other
properties. Their purpose is to map an input value (on the horizontal or
X axis) to an output value (measured on the vertical or Y axis). If Math
isn’t your first language, don’t worry – after a little playing with
them, everyone seems to quickly develop an intuitive understanding.

<figure>
<img src="Tone_Curve.png" title="Tone_Curve.png" />
<figcaption>Tone_Curve.png</figcaption>
</figure>

As an example, consider the figure to the right – part of the
[Exposure](Exposure "wikilink") tool. The left part of the graph
represents the darker tones, the right part represents the brighter
tones of the photo. You can see that the bottom left of the curve has
been moved up. This will cause dark areas to be boosted. Similarly the
top right of the curve has been pulled down, cutting back the bright
areas.

The figure shows the curve type drop down. Tone curves allow four
different ways of manipulating the curve:

- **Linear:** The default type - a straight line that results in no
  change to input values. The mathematically inclined may observe that
  it is a graph of y=x. The rest of us just set the control to linear to
  “turn off” the curve.
- **Custom:** The type most commonly seen in other software. Click to
  drop a control point anywhere on the curve and then drag the control
  point to change the curve’s shape. The top-right point represents the
  brightest areas in the photo. Drag that point vertically down to make
  the highlights less bright; move it horizontally to the left to make
  bright areas brighter, perhaps at the cost of some overexposure. The
  bottom-left point represents the darkest areas in the photo. Move that
  point horizontally to the right to make the photo darker, perhaps at
  the cost of some underexposure. Move it vertically up to make the
  darks lighter.
- **Parametric:** Allows you to use sliders rather than dragging the
  curve directly. For the Parametric curve type, clicking the right
  mouse button over the zone selector
  (![Image:Parametric_curve_bar.png](Parametric_curve_bar.png "Image:Parametric_curve_bar.png"))
  will reset the handles' position to their default values. (The global
  reset button will reset them too.)
- **Control Cage:** At first sight this curve type looks very much like
  the Custom curve, but there are some differences. With the Custom
  curve, the curve touches all the control points. This is not the case
  with the control cage curve – the control points attract the curve
  towards them but the curve doesn’t actually go through them. Another
  difference is that the control cage allows for a straight section of
  the curve, while you can't do this with the custom curve. The cage
  curve needs at least three points for that (so five in total). Holding
  down the Shift key while dragging a point will help you to easily
  create a straight line by snapping the point to the line made by the
  previous and next point (displayed in red by the 'snap to' tool). Many
  users prefer Control Cage type curves to the alternatives.

### The Flat Curve

[frame](image:Flat_curve_justcurve.png "wikilink") A number of tools in
RawTherapee use the *flat curve*:

- [Lab Adjustments](Lab_Adjustments "wikilink")
  - [LH](Lab_Adjustments#LH_Curve "wikilink")
  - [CH](Lab_Adjustments#CH_Curve "wikilink")
  - [HH](Lab_Adjustments#HH_Curve "wikilink")
- [Defringe](Defringe "wikilink")
  - [Hue](Defringe#Hue "wikilink")
- [HSV Equalizer](HSV_Equalizer "wikilink")
  - [H](HSV_Equalizer#H "wikilink")
  - [S](HSV_Equalizer#S "wikilink")
  - [V](HSV_Equalizer#V "wikilink")

It's very simple to use once you understand it, so let's use the [HSV
Equalizer](HSV_Equalizer "wikilink") in the
[image:colour.png](image:colour.png "wikilink") Color tab as an example.
Click on the drop-down icon
[image:Drop-down.png](image:Drop-down.png "wikilink") next to the H(ue)
button and choose "*Minima/Maxima control points*"
[image:CurveType-controlPoints.png](image:CurveType-controlPoints.png "wikilink").
You'll see six dots on the horizontal line in the middle and six
vertical lines that cross these dots. Notice that those lines are
colored; from left to right: red, yellow, green, aqua, blue and magenta.
Now click on the very left dot (the cursor changes into a little hand)
and move it slightly upward and downward. Result: red colors quickly
change to green, blue and magenta as the cursor is moved up, and to
pink, blue and green when moved down.

Notice that a new horizontal line appears when you start dragging a
color point, and see how its color changes. The vertical axis represents
input colors, and the horizontal axis output colors.

When you click and drag a vertical line (the line, not the point!), the
very first movement will determine the kind of move: vertical or
horizontal (so take care with this first movement if you want to have a
predictable result). If you want to move the point in both directions at
the same time, then click and drag the point itself. To move the point
only in one direction (only horizontally or only vertically) you can use
the 'snap to' function by holding down the Shift key while moving the
point.

[frame](image:Flat_curve_zoom.png "wikilink") It's easy to see if a
point is on its neutral value (i.e. on the middle line) because the
color of the point will be green. As soon as you move a point off its
neutral value, it changes color to black.

The [HSV Equalizer](HSV_Equalizer "wikilink") wraps around on the
horizontal axis, so the very right vertical line equals the very left
line. You can see this by dragging the red line on the left side a bit
to the left. Now the left point of the graph is at the same position as
the very right point. Holding the **Shift** key while dragging a point
prevents it from wrapping around the horizontal axis, which can be
useful in preventing accidental curve steps in hard-to-see places at the
edges.

You can delete points by dragging them out of the editor field. You can
add points by clicking somewhere on the curve. When you place the mouse
on one of the points, you see a yellow and blue indicator. Place the
mouse on the yellow one and the cursor changes into a left arrow. Now
you can drag this point to the left, to change the slope of the curve.
Ditto for the blue indicator.

To get an idea how this editor works, delete all but two colors (e.g.
red and yellow) and move the graph around, change its slope and see what
happens to your photo.

Reset the *Hue* curve to "*Linear*" (no changes) by clicking on the
reset icon [image:Gtk-undo-ltr.png](image:Gtk-undo-ltr.png "wikilink")
next to the *Value* button. To compare the effects of the *Hue* curve
with linear: switch between "*Linear*" and "*Minima/Maxima control
points*" in the drop-down menu next to this button, or use the history
list on the left side of your screen.

You can save a curve for later use by clicking on the disk button. Note
that only the actual (shown) H, S or V curve is saved, not all three at
once, so don't give your curve a name like my_hsv because it doesn't
describe whether the curve inside it is H, S or V, but instead name your
saved curve files something like my_hue, my_sat and my_val. The
extension will be added automatically, "*.rtc*".

## The Preview Area

The preview is designed to show you the most realistic result possible,
however one must keep in mind that the larger an image is, the longer it
takes to process. For speed reasons, the preview of the effects of most
tools is calculated not on the full-sized image (which would take
exactly as long as saving the image, making using sliders and curves
impossible), but on the preview image which is of the size of your
preview area. Many tools, such as the [Exposure](Exposure "wikilink")
tool, can be applied to an image of any size, and their effects will be
identical regardless of the size of the image they are applied to.
However some tools are size-dependent, for example all of the tools in
the Detail tab, which means if you apply one of these tools to a
full-sized image and to a smaller version of that image, and then
downscale the full-sized image to the smaller image's size, the two
images won't match. For reasons of speed, RawTherapee must use the small
preview image so that your tool tweaking experience may be fast and
fluid, but this means that the effects of size-dependent tools would not
be accurate when applied to a small zoomed-out preview. We made the
decision to either disable the preview effects of these tools entirely
at zoom levels less than 100%, or to keep the preview effects active but
to warn you that what you see at zoom levels less than 100% may be
inaccurate depending on the tool settings (for example [Tone
Mapping](Tone_Mapping "wikilink") and [Wavelet](Wavelet "wikilink") may
be accurate at zoom levels less than 100% or they may be inaccurate,
depending on their settings). You will know which tools these are
because they are marked with a "1:1" icon ![Zoom 100 identifier
icon.](zoom-100-identifier.png "Zoom 100 identifier icon.") next to
their names. RawPedia explains how accurate the preview is for all
affected tools on each tool's page.