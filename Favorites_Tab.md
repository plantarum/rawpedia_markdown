## Introduction

RawTherapee 5.6 introduced a new "Favorites" tab, which allows you to
list your favorite tools for quick access. Tools listed in the Favorites
tab are removed from their tabs of origin.

The Favorites tab is hidden by default, and appears when tools are added
to it.

A graphical user interface for easily marking tools as "favorited" is
being worked on, but due to time constraints related to the release
date, this GUI is not ready for 5.6 and will feature in a future
release. For the time being, users who wish to "favorite" specific tools
need to do so manually, as described below.

## Usage

To add a tool to the Favorites tab:

1.  Edit the [`options`](File_Paths "wikilink") file in a text editor.
2.  Locate the `Favorite=` key in the `GUI` section.
3.  Add tools by their code-name (listed below), separated by a
    semicolon and ending with a semicolon. They appear in the order in
    which they are listed in the key. For example, to add Exposure,
    Shadows/Highlights and Resize to the Favorites tab, set the key as
    follows: `Favorite=tonecurve;shadowshighlights;resize;`

Tool code-names:

- Exposure
  - Exposure - `tonecurve`
  - Shadows/Highlights - `shadowshighlights`
  - Tone Mapping - `epd`
  - Dynamic Range Compression - `fattal`
  - Vignette Filter - `pcvignette`
  - Graduated Filter - `gradient`
  - L\*a\*b\* Adjustments - `labcurves`

<!-- -->

- Detail
  - Sharpening - `sharpening`
  - Local Contrast - `localcontrast`
  - Edges - `sharpenedge`
  - Microcontrast - `sharpenmicro`
  - Impulse Noise Reduction - `impulsedenoise`
  - Noise Reduction - `dirpyrdenoise`
  - Defringe - `defringe`
  - Contrast by Detail Levels - `dirpyrequalizer`
  - Haze Removal - `dehaze`

<!-- -->

- Color
  - White Balance - `whitebalance`
  - Vibrance - `vibrance`
  - Channel Mixer - `chmixer`
  - Black-and-White - `blackwhite`
  - HSV Equalizer - `hsvequalizer`
  - Film Simulation - `filmsimulation`
  - Soft Light - `softlight`
  - RGB Curves - `rgbcurves`
  - Color Toning - `colortoning`
  - Color Management - `icm`

<!-- -->

- Advanced
  - - Retinex - `retinex`
    - Wavelet Levels - `wavelet`

<!-- -->

- Transform
  - Crop - `crop`
  - Resize - `resize`
    - Post-Resize Sharpening - `prsharpening`
  - Lens / Geometry - `lensgeom`
    - Rotate - `rotate`
    - Perspective - `perspective`
    - Profiled Lens Correction - `lensprof`
    - Distortion Correction - `distortion`
    - Chromatic Aberration Correction - `cacorrection`
    - Vignetting Correction - `vignetting`

<!-- -->

- Raw
  - Sensor with Bayer Matrix - `sensorbayer`
    - Demosaicing - `bayerprocess`
    - Raw Black Points - `bayerrawexposure`
    - Preprocessing - `bayerpreprocess`
    - Chromatic Aberration - `rawcacorrection`
  - Sensor with X-Trans Matrix - `sensorxtrans`
    - Demosaicing - `xtransprocess`
    - Raw Black Points - `xtransrawexposure`
  - Dark-Frame - `darkframe`
  - Flat-Field - `flatfield`
  - Raw White Points - `rawexposure`
  - Preprocessing - `preprocess`