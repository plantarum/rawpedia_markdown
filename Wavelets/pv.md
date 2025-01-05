<div class="develop">

NOTE: this is a work in progress

</div>
<div class="pagetitle">

Wavelet Levels

</div>

## How is this tool organized?

The Wavelet Levels tool is very extensive and its inner workings are
truly complex. Except for some tasks such as interpolation or color
management, you can fully process a photograph only with this tool,
although its best virtue is its ability to complete and refine the
effects of other tools.

The general structure consists of a **tool configuration** block,
followed by a series of ***modules*** (groups of options) that perform
specific tasks. You will be able to turn on and off the modules you
want, although if you turn off them all the effect will be the same as
deactivating the tool.

## What are Wavelets?

A [Wavelet](https://en.wikipedia.org/wiki/Wavelet), or more precisely a
[Wavelet Transform](https://en.wikipedia.org/wiki/Wavelet_transform), is
a complex mathematical function which is very useful in image
processing, as it allows you to split images into several levels of
detail so you can work on the one that interests you.

The wavelets term was introduced in the early 1980s by French physicists
Jean Morlet and Alex Grossman: they used the French word *ondelette*,
which means *small wave*. Later, this word was adapted to English
changing *onde* by *wave*, leading to *wavelet*.

The *Wavelet Transform* is similar to a *Fourier Transform*: it is a
matter of representing data as combinations of known and predefined
waves (the frequencies), so that the result is as close as possible to
the original data. Roughly speaking, the main difference for
two-dimensional images is that in the Wavelet Transform the data being
analyzed are represented as the frequencies present at the points of the
image, whereas in the standard Fourier Transform they are only
represented as the frequencies present in the full image. Therefore,
using wavelets offers more precision when analyzing the data.  
<span style="font-size: 0.7em; font-style: italic;">\[Obviously this is
a very simplistic and summarized explanation: mathematicians would
surely have a lot to say here...\]</span>

![](Wavelet_daubechies20.png "Wavelet_daubechies20.png")RawTherapee uses
wavelets in various tools, and in this one in particular it uses the
[Daubechies](https://en.wikipedia.org/wiki/Daubechies_wavelet) wavelet,
with which it decomposes the elements of the image in the [L\*a\*b\*
color space](https://en.wikipedia.org/wiki/CIELAB_color_space) elements
(*L\**, *a\** and *b\**).

Decomposing the image involves analyzing by means of an
[algorithm](https://en.wikipedia.org/wiki/Algorithm) the «internal»
contrast of groups of pixels (2x2=4 pixels on the first level, 4x4=16
pixels on the second level, ...) in three directions: vertical,
horizontal and diagonal. This analysis converts the values of these
contrasts into sets of wavelets with different amplitudes and
intensities and stores their characteristics in coefficient matrices,
which indicate how the wavelets should be combined to regenerate an
image as similar as possible to the original one.

And every time you make modifications (contrast, tone, noise, ...) this
regeneration is done automatically and interactively, so that you can
immediately see the result of your adjustments.

In this sense, the moment the image is decomposed, it ceases to exist
and only remain several sets of coefficients (one set for each level)
which will be used by the tool. These sets represent two different
results:

- Several levels of detail: the first level corresponds to details with
  an area of 2x2 pixels; the tenth level corresponds to «details» with
  an area of 1024x1024 pixels. The choice of how many to use depends on
  your needs, however keep in mind that the more levels you extract, the
  more processing time and memory will be needed.


On the other hand, since only *variations* (gradients, or differences)
in [hue](https://en.wikipedia.org/wiki/Hue) or
[luminance](https://en.wikipedia.org/wiki/Luminance) are analyzed at
each level, if an image is absolutely uniform in luminance and color,
the levels will not contain any information. That is, the differences
extracted in each level come from digital noise and changes in contrast
(or chromaticity) due to edge effects, fog or other optical phenomena
coming from the scene.

- A residual image: it is the result of removing the details present in
  all the levels analysed from the original image, with the important
  particularity that the modification of the characteristics of a level
  (contrast, chromaticity, etc.) has no effect on the residual image.
  And vice versa.

Moreover, for each level the tool takes into account the set of
coefficient values and calculates their arithmetic mean (so that at each
level the mean will be different) and the [standard
deviation](https://en.wikipedia.org/wiki/Standard_deviation). Adding the
maximum and minimum coefficients to these data, a distribution curve is
generated which represents the characteristics of each level (it should
be noted that this curve is not
[Gaussian](https://en.wikipedia.org/wiki/Normal_distribution)). All of
this is used in different ways in the tool's algorithms.

## In practice

After decomposition, the resulting levels can be used for different
purposes: image compression, noise reduction, [secret
watermarking](http://www.intechopen.com/books/discrete-wavelet-transforms-algorithms-and-applications/application-of-discrete-wavelet-transform-in-watermarking),
specific residual image treatment for astronomy, etc.

Depending on your needs, you will have to work with an individual level
of detail, with several levels of detail (one after another), with the
residual image, or with all of them combined.

The size of the details included in each level is:

<figure>
<img src="Wavelet_detail_size.png" title="Wavelet_detail_size.png" />
<figcaption>Wavelet_detail_size.png</figcaption>
</figure>



**1 (Finest)** : 2x2 pixels

**2** : 4x4 pixels

**3** : 8x8 pixels

**4** : 16x16 pixels

**5** : 32x32 pixels

**6** : 64x64 pixels

**7** : 128x128 pixels

**8** : 256x256 pixels

**9 (Coarsest)** : 512x512 pixels

**Extra** : 1024x1024 pixels

If you were to select 5 detail levels, the changes in the different
levels would be limited to details with 32 pixels size or smaller. In
this case the residual image would have all the details of the image,
except those included in levels *1* to *5*. And since those details
removed are relatively small, the residual image would be quite similar
to the original image.

On the other hand, if you chose *level 9* you could change the details
with a size of 512 pixels and 1024 pixels (*level Extra*). In this case
the residual image would be quite different from the original image, as
the levels from *1* to *Extra* would contain all the details, so little
more than a blurred background would be left.

In any case, the wavelets decomposition separates in the residual image
and in each level the
*[lightness](https://en.wikipedia.org/wiki/Lightness)* and the
*[chroma](http://www.huevaluechroma.com/015.php)* channels ([*a\** and
*b\**](https://en.wikipedia.org/wiki/CIELAB_color_space#CIELAB)). Thanks
to this you can apply different adjustments to the brightness and tones
of each level, without preventing you from performing a completely
different processing on the residual image. This means that the levels
and the residual image are independent: the tool will only modify those
levels where you make changes, the rest will remain untouched and the
residual image will continue to be what is left after all details in all
levels have been removed (whether they have been modified or not).

Note that if you want to use the Wavelet Levels tool at the same time as
[the CIECAM tool](CIECAM02 "wikilink"), you may get artifacts due to the
fact that the CIECAM color model uses specific values that are close-to
but different from the values of the Lab color space. The way the tool
is coded these artifacts are unavoidable, but their appearance will
depend on the processing made.

#### The preview

The size of the image on screen has a direct impact on the perceived
sharpness and on the appreciation of the minimal changes made in each
module: **the effects of this tool are only visible at full size zoom**
(or larger). In practice, this means that, [for processing speed
reasons](General_Comments_About_Some_Toolbox_Widgets#The_Preview_Area "wikilink"),
you must have the final size of the image in mind and if it's going to
be necessary to reduce it (scale it down, not crop it), then it's
advised to first export it with its final size and process it afterwards
with wavelets. Keep this in mind because otherwise what you see in the
preview will not be the same as the final exported result.

On the other hand there is another limitation: RawTherapee uses in the
preview all the levels it can, ignoring those levels whose details are
larger than the portion of the image you see on the screen. But even if
the changes in the ignored levels are not shown on screen, they will be
applied when processing the image to save it to disk.

**Examples**

- example 1: the image is **4096x2160** pixels, you have enlarged it (to
  100% or more) and in the preview you see a *'1500x1200* pixels area at
  a similar size to which it will have in the final image. This is the
  ideal case and on the screen you can see all the modifications you
  make at all levels (up to the *level Extra*). In addition, the changes
  you made at every level will be included in the final image.
- **example 2**: the image is **4096x2160** pixels, but you have
  enlarged it and in the preview you only see **300x200** pixels, so on
  screen you won't be able to see any change in details bigger than
  *level 7* (details of 128 pixels), but when you save it the changes
  you made in levels *8*, *9* and *Extra* will be included (because the
  image is bigger than 1024x1024 pixels).
- **example 3**: the image is **720x480** pixels and you have enlarged
  it until we only see **300x200** pixels in the preview, so on screen
  you will not be able to see any modification in details bigger than
  those of the *level 7* (details of 128 pixels) ***and in addition***
  when saving it the changes you made in *level 8* will be included
  (details of 256 pixels), but the levels *9* and *Extra* **will NOT**
  be included.

As all this is very important not to forget, the tool itself informs you
how many levels are being used for the preview, under the last slider of
the *Contrast* module. In the examples 2 and 3 above you would see:
«**Preview maximum possible levels = 7**».

#### Contrast by Detail Levels vs Wavelet Levels

It's worth mentioning that RawTherapee has a tool called *[Contrast by
Detail Levels](Contrast_by_Detail_Levels "wikilink")* and although it
looks like the Wavelet Levels tool, there are several relevant
differences between them:

- *Contrast by Detail Levels* has fewer levels (6, instead of up to 10),
- *Contrast by Detail Levels* only allows you to adjust the luminance of
  each level, while Wavelet Levels also allow you to adjust the
  chromaticity of each level,
- *Contrast by Detail Levels* adjusts equally all luminances (or
  chromaticities) present in the level, while Wavelet Levels perform a
  progressive adjustment ([this will be better understood in the
  contrast attenuation section](#The_attenuation_curve "wikilink")),
- *Contrast by Detail Levels* doesn't have residual image.

That said, no one is stopping you from using both tools at the same
time, although please note that *Contrast by Detail Levels* is applied
earlier in the [Pipeline](Toolchain_Pipeline "wikilink"), so depending
on the intensity of the adjustments made there, the details presented in
levels from *1* to *6* may be affected. In other words, since the
contrast will have changed with the *Contrast by Levels of Detail*
settings, the analysis by Wavelet Levels could decompose the image in a
different way, so the results would be different. In any case, if you
have to use both tools, it is recommended that you adjust first the
Contrast by Detail Levels and then adjust the Wavelet Levels.

## General tool configuration

Once the tool is turned on, you can make general adjustments to its
behavior, which will affect all modules.

### Strength

With this slider you can adjust the overall intensity of the tool.

The idea is to envision that two overlapping images are merged: the
original image will be underneath, and the modified image is overlaid on
top of it, setting the opacity (transparency) of the upper image with
the slider, to get a smoother or gradual final image. This way you can
make more aggressive adjustments, which will then be integrated into the
original image through transparency.

### Wavelet levels

This slider lets you decide how many detail levels the image will be
decomposed into. You can choose any level between *4* and *9* (the 10th
level, called *Extra*, appears automatically when you select *level 9*).
The higher the number, the more processing time and memory will be
required.

### Tiling method

A drop-down list allows you to choose from:

- Full image,
- [Tiles](https://en.wikipedia.org/wiki/Euclidean_tilings_by_convex_regular_polygons).

It is always preferable using *Full image*, because it avoids problems
in the transition area between tiles.

However, if you do not have enough RAM, or if you are processing very
large images (e.g., 50 Megapixels or more), you may have to use the
tiles:

| Required memory, in bytes, with 9 detail levels     |
|-----------------------------------------------------|
|                                                     |
| Megapixels (Mpx)                                    |
| To open the image (all tools turned off)            |
| Contrast, Chromaticity or Hue Protecction turned on |
| \+ Avoid color shift                                |
| Total                                               |

### Edge performance

The decomposition of an image into its components by the Daubechies
method may have up to 10 coefficient scales, from D2 (which corresponds
to the Haar decomposition) to D20. In RawTherapee the coefficients *D2
(low), D4 (standard), D6 (standard plus), D10 (medium) and D14 (high)*
are used. The more coefficients are used, the more detail the wavelet
will distinguish and the slightly increased processing time (often
negligible) will occur.

Although there is no direct relationship between the resulting quality
and the number of coefficients (depending on the original image),
choosing the right number of coefficients will allow you to refine the
quality of the lower levels, or that of the residual image:

- in some cases the best results for edge detection are obtained with D2
- in other cases with D6 or D14

This parameter has a fairly high impact on the *[Edge
detection](#Edge_detection "wikilink")* and also in global decomposition
(the relationship between the residual image and each level).

### Preview

This group of controls will help you understand how to work with this
wavelets tool and fine-tuning the parameters of the modules (e.g. on
noise reduction).

You have a total of four drop-down lists, allowing you to tailor what
you see in the preview.

The group is divided into two main drop-down lists (and a couple more
that will be activated when you make certain selections in the main
lists):

- the first one lets you choose the preview background
- the second one lets you choose which levels will be displayed in the
  preview