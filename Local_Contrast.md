<div class="pagetitle">

Local Contrast

</div>

The Local Contrast tool adds local contrast to an image by applying an
unsharp mask with a large blur radius. It it an easy way to give an
image a little more 'punch'. In effect, the image is blended with a
blurred version of itself, amplifying the local tones (highlights get
lighter, shadows get darker), thus creating more contrast. The contrast
can be tuned by several parameters explained below.

This tool was first implemented by [G'MIC](http://gmic.eu/) and then
ported to RawTherapee. Its effect is applied in L\*a\*b\*-space and only
on the lightness channel.

<div class="img-comp-wrapper">
<div class="thumbinner thumbcompare tnone" style="width: 500px">

<imgcomp img1='LocalContrast-Off.jpg' img2='LocalContrast-On.jpg'  width=500 />

<div class="thumbcaption">

**Left side:** original image
**Right side:** image with local contrast applied (Radius = 100, Amount
= 0.5)

</div>
</div>
</div>

### Parameters

- **Radius** determines the extent of the local contrast (i.e. the
  radius of the blurring). Higher values give a smoother, but stronger
  contrast. Lower values give a more localized, less pronounced
  contrast.
- **Amount** determines the overall strength of the effect. Higher
  values amplify the differences between the original image and the
  blurred image, thereby increasing contrast.
- **Darkness level** modifies only those areas of the image that were
  darkened with respect to the original. Higher values amplify the
  change (making darker parts even darker), lower values diminish the
  change. N.B. A value of 0 means the local contrast is only modified by
  making the image lighter.
- **Lightness level** works similarly, but only on areas that were
  lightened.

Note that setting both the "Darkness level" and "Lightness level" to 0
effectively disables the tool.