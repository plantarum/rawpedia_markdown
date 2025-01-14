Negatives are images with reversed lightness and colors, such as those
produced by film cameras. RawTherapee (version 4.2 at the time of
writing) does not yet have a flawless single-click solution for dealing
with them, so this page serves to inform you of the possible workaround
solutions:

1.  Invert a diagonal [tone curve](Exposure#Tone_Curves "wikilink")
    either in the Exposure tool, or all of the curves in the [RGB
    Curves](RGB_Curves "wikilink") tool. The downside is that there are
    tonal shifts when doing this.
2.  Use a negative Hald CLUT via the [Film
    Simulation](Film_Simulation "wikilink") tool. The "RawTherapee Film
    Simulation Collection" contains one, get it from the [Film
    Simulation](Film_Simulation "wikilink") page. The downside is that
    some controls might operate in reverse, such as the Exposure slider,
    and you may experience clipping in the shadows and/or highlights as
    these tools are not designed to work with negatives.
3.  In addition to using the neutral negative Hald CLUT as described
    above, if you have a successful workflow of not only inverting
    negatives but also toning them to your liking in RawTherapee or in
    other software, you could [make your own negative Hald
    CLUT](Film_Simulation#Make_Your_Own "wikilink") which reproduces the
    whole look including negative inversion. To do that, apply the same
    steps to the "identity Hald CLUT image" shipped with the RawTherapee
    Film Simulation Collection as you would to a photo negative, save it
    under a new name, then open a photo negative in RawTherapee and
    apply that new Hald CLUT image. This lets you instantly achieve not
    only negative inversion but also your own toning with the click of a
    button, leaving you only needing to expand the histogram by
    adjusting the Exposure slider or using curves.
4.  Currently the best method is to use the DCP (DNG Camera Profile) for
    your camera model but edited in DNG Profile Editor so that the
    diagonal tone curve is inverted, then manually loading this DCP in
    RawTherapee for all negative shots. Method outlined below.

## Creating a DCP for Negatives

![](DNG_Profile_Editor_inverted_tone_curve.png "DNG_Profile_Editor_inverted_tone_curve.png")
![](Rt_negative_dcp_l_curve.png "Rt_negative_dcp_l_curve.png")

1.  Get [DNG Profile
    Editor](http://www.adobe.com/support/downloads/detail.jsp?ftpID=5494).
    It runs fine in Linux through [wine](https://www.winehq.org/).
2.  Convert one of your camera's or scanner's raw photos (it can be the
    photo of the negative) to DNG by following the guide "[How to
    convert raw formats to
    DNG](How_to_convert_raw_formats_to_DNG "wikilink")".
3.  Open the DNG image in DNG Profile Editor.
4.  In the Color Tables tab, see whether the Base Profile called "Adobe
    Standard (*<your camera model>*)" is available. If it is, then
    select it. If it is not, then select "Choose external profile" and
    find the file titled "*<your camera model>* Adobe Standard.dcp". The
    guide [How to get LCP and DCP
    profiles](How_to_get_LCP_and_DCP_profiles "wikilink") explains how
    to get them and where to find them.
5.  In the Tone Curve tab invert the diagonal so that it goes from
    top-left to bottom-right (move the top point to the bottom).
6.  Still in the Tone Curve tab, there are three "Base Tone Curves" for
    you to choose from. "Base Profile" and "Camera Raw Default" are
    usually identical and have more contrast, while "Linear" makes the
    image look flat. We recommend you save one DCP which uses "Base
    Profile" and another which uses "Linear", and see for yourself which
    one better suits your needs in RawTherapee. Both DCPs will require
    further image tweaking in RawTherapee, but the "Linear" one will
    require more tweaking than the "Base Curve" one, though the latter
    might over-saturate colors - keep an eye on that.
7.  To create the DCP, click "File \> Export *<your camera model>*
    profile...". As recommended in the previous step, save two versions.

To use this new DCP for negatives, once you have your negative raw
opened in RawTherapee go to the Color tab \> Color Management section \>
Input Profile, and select Custom, then find this new DCP file. Enable
"Use DCP's tone curve".

When tweaking images in RawTherapee using these DCPs, remember that
using tone curves which operate on RGB channels (Tone Curve 1 and 2 in
the Exposure tool) will change not only the lightness but also the color
saturation the stronger your curves. You can control color saturation by
using the "Weighted Standard" and "Saturation and Value Blending" modes,
or you can avoid the problem by working in L\*a\*b\* space. The
advantage of working in L\*a\*b\* space as the L\* curve does is that
colors are not changed while you modify the lightness, so you can fix
the lightness first using as strong an L\* curve as you need, and then
fix the color saturation using for example the CC curve.