Use this tool to independently influence the highlights and the shadows
of the image.

## Sharp Mask

\<gallery caption="Shadows/Highlights "Sharp mask" effect" style="clear:
both"\> <File:Sh_sm_1.jpg%7CThe> source image.
<File:Sh_sm_2.jpg>\|"Sharp mask" turned off. <File:Sh_sm_3.jpg>\|"Sharp
mask" turned on.

</gallery>

In order to separate the dark areas from the light ones, a lightness
mask (invisible to the user) is created. There are two algorithms for
doing this; one blurs the image, while the other retains sharp edges
between light and dark zones. Neither one is "better", both have their
own merits. The soft mask approach can lead to halos, but it is quick.
The sharp mask is slow, but it doesn't cause halos, though it can cause
edge artifacts at close inspection.

## Highlights

The Highlights slider makes the brightest parts of the image less bright
without touching the darker tones. To make the effect stronger, use
higher values. A slider value of 100 will turn the whites light gray.

## Tonal Width for Highlights

This slider controls the strength of the Highlights slider. Higher
values give a stronger effect. A value of 100, combined with Highlights
100, turns the whites into middle gray (you probably won't want
that...).

## Shadows

This slider lifts the shadows and applies an effect that is sometimes
called 'fill-light' (or 'fill-flash') in other software. Higher values
lighten the shadow areas more.

## Tonal Width for Shadows

This slider controls the strength of the Shadows slider. A maximum value
of 100 gives the strongest 'lift shadows' effect.

## Local Contrast

Local Contrast is an adaptive contrast adjustment depending on contrast
within a specified area. It increases contrast in small areas while
keeping the global contrast (which can be set with the contrast sliders
in Exposure or Lab). The resulting image will look more
'three-dimensional'. This feature is very useful when you have a foggy
image or took your picture through a window. The effect is somewhat
similar to an unsharp mask with a high radius and a small value. A
setting between 5 and 20 works best for most shots.

## Radius

The value of the Radius slider influences the Highlights, Shadows and
Local Contrast sliders. The larger the radius, the stronger the effect
of local contrast. The effective area of the Highlights and Shadows
sliders also increases.

If you are bored, set the first four sliders to 100 and play with Local
Contrast to transform your favorite raw processor into a cheap effect
machine!