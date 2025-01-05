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

## Rendering Intent

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

colors is needed, e.g. fabric or logo colors.