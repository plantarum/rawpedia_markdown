__NOTOC__ Note: This translation of the "Retinex" French page is a
working document.

__TOC__

# Generalities

While the eyes are able to see correctly the colours through a poor
lighting, a coloured surrounding or a veil of fog, cameras badly manage
in theses conditions. It is by copying the eyes biological mechanisms to
adapt itself to these conditions that the MSR algorithm (MultiScale
Retinex) has been created. In addition to the digital photography, the
Retinex algorithm (Retinex is the contraction for Retina + Cortex) is
used in astronomy to show up information laying in the astronomical
photographs, in medicine to detect not much visible structures in
radiography and tomodensitometry. Numerous theories and algorithms have
been working out for more than 20 years. The first experimentation has
been proposed by Rahman in 1996. The approach follows the human visual
perception and the Edwin Land's retinal function. In a way, this
approach is pretty similar to CIECAM. This function and more
particularly its general form is similar to a DOG (Difference Of
Gaussian). The idea consists of characterizing the luminous information
of a point from its intensity and the intensity of its neighbours. This
said, this approach has no scientific basis and is only lying on
experience and various empirical constants. Over the years many
improvements have been added, but from my own point of view, no one is
fully satisfactory. I relied on two documents :

- "Automatic Image Haze Removal Based on Luminance Component" (Fan Guo,
  Zixing Cai, Bin Xie, Jin
  Tang"[1](http://www.mcs.csueastbay.edu/~grewe/pubs/DistSensorNetworkBook2011/Atmosphere/HazeREmoval_SingleImage_Luminance.pdf)
- "Retinex Algorithm on Changing Scales for Haze Removal with Depth Map"
  (Weixing Wang, Lian
  Xu)"[2](http://www.sersc.org/journals/IJHIT/vol7_no4_2014/30.pdf)
- and from some programming tricks inspired from "2003 Fabien Pelisson
  \<Fabien.Pelisson@inrialpes.fr\>"

The use of Retinex might be beneficial to images processing:

- that are hazy, misty or having a veil of fog
- with important luminance gaps
- where the user looks for special effects (tone mapping …)

## Retinex at the beginning of the processing

It is the algorithm described in this page, with its limitations,
advantages and drawbacks.

## Retinex in "Wavelets"

I installed 2 possibilities to enable Retinex in the Wavelet process:
[Wavelet levels/fr](Wavelet_levels/fr "wikilink"). Some of the quoted
limitations are no more there !

Quick comparison between the both versions " Retinex in Wavelets" and "
Retinex at the beginning of the processing":
[Wavelet_levels/fr#Avantages_.28.2B.29_et_inconv.C3.A9nients_.28-.29_de_Retinex.2Ffr_par_rapport_.C3.A0_Retinex_in_wavelet](Wavelet_levels/fr#Avantages_.28.2B.29_et_inconv.C3.A9nients_.28-.29_de_Retinex.2Ffr_par_rapport_.C3.A0_Retinex_in_wavelet "wikilink")

# Imposed limitations by RawTherapee

The basic algorithm impose a reference to the whole image, and not to a
crop or a reduction like in the RawTherapee processing. This limitation
imposed by the gaussian function causes several consequences:

- The processing has been shifted from its dedicated place, that should
  have been close to "Lab Adjustments" - near the beginning of the
  RawTherapee processing – that is necessarily (except if somebody has
  an idea to do different) a raw process. As a consequence, non raw
  files (TIFF, JPG, …) can't be processed with this algorithm? This
  problem should be solved soon (November 2015 ??).
- The second consequence of this position is that the characteristics of
  the raw data situated just after demosaicing are very different that
  the ones situated downstream: no gamma, no gamut limitation, no white
  balance, no RGB conversion… so we must expect artefacts and poor
  luminance and colour rendering.
- The third consequence is the system response time which imposes to
  re-actualize the whole process after each change in the settings.
- The fourth, sometimes, will need a white point modification, in order
  to avoid colours distortions (for example: a magenta sky).
- But advantage, this process being situated before "Denoise", the noise
  reduction will be here fully effective.

Nevertheless, despite these handicaps, as we will see it further,
results are more than satisfactory as well about processing time that in
contrast and colours rendering, particularly by joining Retinex and
Wavelets actions.

# Algorithm principle

For more information, see the "pdf" documents given in the
"Generalities" section.

## To elaborate a "Transmission Map" file obtained by

- making the difference, for luminance only, between each pixel
  logarithm of the input image and the neighbouring pixels logarithm of
  the matching gaussian image. The standard deviation (gaussian
  function) used here is very high - usually in RawTherapee sigma values
  from 0.5 to 5 are common – here the values range from 10 to 280
  (Single Scale Retinex), it is the user choice.
- modifying the input image luminance distribution by

:\* applying a gamma before the "Transmission Map" file creation

:\* applying an inverse gamma to restore the input image characteristics
This modification of the distribution allows:

:\* to change the image tonality

:\* to modify the "Transmission Map" file to take into account for
example the under or over exposed areas.

- applying several time (Scale) – 3 times, not modifiable by the user –
  this algorithm with an addition using empirical coefficients (Multi
  Scale Retinex). (Low scale values increase the apparent contrast, but
  give a perspective look to the image, high scale values make the image
  more natural but they have a tendency to increase the noise).
- a variation of MSR by the user according to the desired effect
  (Uniform, Low, High, Highlight)
  - Uniform: Strive to process low and high intensities in a balanced
    way.
  - Low: Improve low intensities areas
  - High: Improve the rendering of the more exposed areas
  - Highlight: Improve the rendering of the highlight areas that may
    become magenta, but can bring strong artefacts.
- choosing the colorspace
  - logarithmic L\*a\*b\*
  - logarithmic HSL
  - linear HSL – this version doesn't comply with Retinex algorithm but
    in some cases it allows a more suitable image processing.

So, we get a logarithmic distribution "Transmission Map" – except in
linear mode! - that we will be able to "subtract" to the input image,
either to get an image theoretically free from mist and from veil fog or
to get special effects. This distribution owns approximatively a
gaussian distribution with a minima (minT) about, according to the
images – higher for images with veil – from -10 to -40, an average close
to from -1 to +2, a standard deviation often about 2 to 6 and a maxima
(maxT) about 10 to 40. The negative values mean low intensity and
positive values mean high intensity. Caution, these values are
logarithmic coefficients that stand for very high values (log 1000 =
6.9) (exp 10 \# 22000)...(exp 20) \# 500.000.000. In theory we should
use high "Scale" and gaussian values in the areas closest to the lens
(where the veil effect is low) and low values in the distance (where the
veil effect is important).

## To process the mask issued from the gaussian process

The "Transmission Map" file correspond to a recursive process of:

- The source image – Input image which went through various
  modifications by the histogram equalizer and the gamma.
- The "mask" files directly issued from the gaussian process (scale,
  radius, method low.. high…)

## "Mask" display type

"Mask" files processing (the idea came to me by studying the Rusell
Cottrell's plugin) will allow to decrease flares and artefacts. I added
a combo-box to choose the display type. This is both an educational
system and also an aid to find the "right" settings.

- Process:
  - Standard: it is the default setting
  - Mask: display the mask obtained by the Retinex algorithm issued from
    the gaussian process. We will see here the impacts:
    - of the various settings upstream: method (low, uniform, high and
      highlight), radius, gamma, histogram equalizer. In the other hand,
      the other settings downstream have no effect on this display:
      contrast, gain, brightness, threshold and the curve "Transmission
      Map".
    - of the various settings of the "Mask equalizer".
    - you can export these settings (TIFF/JPG) to use this mask in
      external software (Gimp, Photoshop).
  - Unsharp mask: you can use this option to subtract the mask to the
    input image. In this case, an action on "strength" will allow to
    balance between the input image and the mask. So we get the
    possibility to have images with very high radius values.
  - Transmission: display an "image" of the "Transmission Map" file.
    - this "image" doesn't match the reality that matches to a
      logarithmic scale which values are mostly situated between -30 and
      +30.
    - (fixed)