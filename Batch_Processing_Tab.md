Batch processing is the capability of editing several images at the same
time in the [File Browser](The_File_Browser_Tab "wikilink") tab. That's
why there's a tool panel in the "File Browser".

This is done by selecting more than one file by using the **Shift** or
**Control** key in the "File Browser", then you can edit those images
with the tools on the right. The way the sliders' values are used to
modify the image depends on the options set in this "Batch Processing"
tab.

When you select a single image, the sliders get the values of the
processing parameters of that specific image. These can be the values of
the default profile or the values from your last edit session of this
photo. If your image is currently being edited in an
[Editor](The_Image_Editor_Tab "wikilink") tab, the editors' values will
be reflected in real time in the Batch tool panel editor, and vice
versa, so take care of what you're doing.

When selecting more than one image in the "File Browser", the action of
the tool sliders depends on that tool's batch processing mode. Tools
which are not listed function as if they were in the "Set" mode.

## The "Add" Mode

This mode may also be understood as "relative". Modifying sliders which
are set to the "Add" mode will result in the value of the modification
being added to the existing value. For example, if you select two images
by holding the **Ctrl** modifier key, one image which has an
[Exposure#Exposure_Compensation Exposure
Compensation](Exposure#Exposure_Compensation_Exposure_Compensation "wikilink")
of -0.5 EV and the other which has +1.0 EV, moving the "Exposure
Compensation" slider up to +0.3 will result in setting a value of -0.2
EV for the first image and +1.3 EV for the second one.

Using the "Reset" button will move the slider to its default (zero)
position and will then bring back the initial value of that slider for
each selected image.

## The "Set" Mode

This mode may also be understood as "absolute". Modifying sliders which
are set to the "Set" mode will result in the value of the modification
being set, irrelevant of what the existing value was. If we use the same
example as before, moving the slider up to +0.3 EV will result in
setting a value of +0.3 EV for both images (one value for all images).

Using the 'Reset' button will move the slider to its default position
(different for each slider), and will then reset this parameter for each
image.

## Overwrite Existing Output Files

The option "Overwrite existing output files" sets RawTherapee to
overwrite existing images. When disabled, existing images will not be
overwritten; instead, an index number is appended to the image being
saved. e.g. If "output.jpg" exists and the option is not checked, the
new image will be saved as "output-1.jpg".