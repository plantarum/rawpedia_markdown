## About Color Toning

The first question that arises is: What is the definition of, or what do
you hear by, "Colour Toning" or "Split Toning"? Indeed, when consulting
the Web, we generally find out something like: "Colour Toning consist in
colouring a black & white image in a different way according to the
brightness, e.g. colouring highlights in yellow and shadows in blue.

Extending the concept, we can put under the same definition:

1.  the toning of a colour image that allows to add a dominant colour to
    the image. It will be possible to tweak this dominant colour in the
    image highlights and/or shadows.
2.  to extend the toning to the whole luminance spectrum, and not only,
    in a restrictive way, to the highlights and shadows.

In RawTherapee, two types of algorithms try to meet the principles
defined above:

1.  "blending from target colours": in this case, a chromatic value is
    weighted according to a formula like: *"output hue" = "input hue" +
    ("target hue" - "input hue") \* balance* where balance is a
    coefficient between 0 and 1. We can easily find on the internet
    references to this kind of lagorithm.
2.  "RGB channels adding and reduction": in this case, according to the
    luminance (highlights, mid-tones, shadows), each channel is
    amplified at the same time the two others are reduced. e.g. an
    action on the red channel for a given luminance range, will increase
    the "R" channel by X%, and at the same time, "G" and "B" channels
    will be reduced by X%. Note it is not a "Channels Mixer". I did not
    find any references to this kind of algorithm, but studying the
    Photoshop "Colour Balance" module behaviour, I think I figured out
    an algorithm that gives similar results.

From experience, the first algorithm type will give good colour toning
results for colour images but is not easily predictable, and it is not
as good for black and white images, even if, of course, it gives
satisfactory results. This algorithm is embedded in two different ways -
no one is better than the other - that give various results:

1.  RGB mode: each R, G, and B channel has the algorithm explained
    in (i) applied.
2.  Lab mode: each colour component "a" (red/green channel) and "b"
    (blue/yellow channel) have the algorithm explained in (i) applied.
    This mode allows, according to the suggested choices (menus), a
    normal predictability or an important creativity.

The second algorithm type can have three usages based on the "Strength"
slider:

1.  using low values, the user can simulate a "colour balance" and
    accurately tweak the tone colour
2.  using high values, the user will be able to, in "colour" mode, get
    similar results as the "blend" algorithm, but with less creativity
3.  using high values, the user will be able to, in black and white
    mode, get strongly specials effects

## The different methods

### "blend" Methods

The "blend" methods are divided into "L\*a\*b\* blending" that uses both
lab chromatic components "a" and "b", and "RGB-sliders / RGB-curves"
that use the same RGB algorithm but differ in the user interface. The
Lab method isolate the colour component from the luminance, whereas the
two RGB methods indirectly act on the luminance. This difference partly
explain the behaviour gap between these methods.

Even if the interface is different (sliders or curves), the two RGB
methods use only one type of opacity (the colour blending management),
whereas the lab mode offers four of them. The first one "Standard chroma
" is similar to the one used in "RGB-curves". The other three allow
special effects.

The used curves are special flat curves.

1.  the Colour curve displays luminance in abscissa and target hues in
    ordinate. the two vertical lines delimit the main resulting areas.
    by moving:
    - the vertical lines positions;
    - the curve shape;
    - the target hues choices;


    you will obtain different results
2.  The Opacity curve (L\*a\*b\* blending \> Standard chroma or RGB
    curves) displays luminance in abscissa and opacity in ordinate (also
    called Balance) that translate the way the original hue (image) and
    the target hue are assemblied, in this case,the opacity value varies
    from 0 to 1. The highest the curve will be, the more the blending
    near the target hue. When setting the opacity curve to 0, the image
    stay unchanged.

The saturation setting (the effects maximum intensity) can be adjusted:

1.  Manually, in this case the box "Automatic" is not checked. You can
    move the two sliders "Threshold" and "Strength".
2.  Automatically, in this case the box "Automatic" is checked. An
    algorithm takes into account the colour space (sRGB, Adobe,
    Prophoto...) and the image pixels saturation to determine the best
    values for "Threshold" and "Strength".

    This settings are obviously without any effect for images converted
    into black and white.

#### "L\*a\*b\* blending" particularities

##### Special chroma

Here, the flat curve is replaced by a diagonal curve. The two chroma
components "a" and "b" (Lab) are modified with the same amplitude. If
you move the curve under the diagonal, you introduce negative opacity
values, which will bring special effects often unpredictable.

##### Special a\* et b\*

Here, the flat curve is replaced by two diagonal curves. The two chroma
components "a" and "b" (Lab) are individually modified by two different
curves. The first one only acts on the "a" component (Lab), i.e. the
red-green dimension. the second one only acts on the "b" component
(Lab), i.e. the blue-yellow dimension. If you move the curve(s) under
the diagonal, you introduce negative opacity values, which will bring
special effects often unpredictable.

##### Special chroma '2 colours'

Here, like in "Special chroma", the flat curve is replaced by a diagonal
curve. The two chroma components "a" and "b" (Lab) are modified with the
same amplitude. If you move the curve under the diagonal, you introduce
negative opacity values, which will bring special effects often
unpredictable.

The difference with "Special chroma" lies in using the colour curve. In
"Special chroma", the whole curve hue=f(Luminance) is used, in the
"Special chroma '2 colours'" case, only the two hues focused by the
vertical lines are used.

#### RGB-sliders particularities

The searched ergonomic aims to be closed to the Lightroom one (like by
the way "Saturation 2 colours")

You have two sliders with two levels at your disposal, the first one for
highlights, the second one for shadows. For each of both sliders you can
set the wished hue and strength: When set to 0, the two strength sliders
doesn't change anything to the image.

The "Balance" slider allows to set the equilibrium between high and low
lights. By moving it to the left (negative values) the action on
highlights is increased, whereas to the right (positive values) the on
action shadows is increased.

### "Adding" Methods

#### Color Balance Shadows / Midtones / Highlights

This method is very close to the Photoshop module "Colour Balance", both
in its operating mode and its rendering.

You can act differently on the highlights, the mid-tones and the
shadows.

Each slider acts on a colour and its complementary colour: Red and Cyan,
Green and Magenta, Blue and Yellow

The "Strength" slider allows to set the system sensitivity:

1.  with low values - less than 50 - you can use this tool to tweak the
    image colour balance, thus modifying the whole blending to give a
    generalised chromatic correction,
2.  with medium values, you can use this tool as a colour toning,
3.  with high values, you can use this tool as a black and white toning,
    interacting with the [Black and
    White](Black-and-White_addon "wikilink") tool (internal algorithm
    parameters are different for a colour or a black and white action)

Select "Preserve Luminance" to prevent any change of the lightness
values in the image when modifying the colour. This option allows to
preserve tone balance in the image.

#### Saturation 2 colors

This method is close to ACR and Lightroom, both in its operating mode
and its rendering.

It is mostly intended to color toning, even if it may be used in
interaction with the [Black and White](Black-and-White_addon "wikilink")
tool.

Two sliders with two levels are at your disposal, the first one for
highlights and the second one for shadows. For each of the both sliders,
you can tweak the desired hue and strength: if set to zero, a strength
sliders prevent any change to the image.

The "Balance" slider allows to balance the action between high and low
lightness. Moving it to the left (negative values) increase the action
on highlights, to the right (positive values) increase the action on
shadows.

The "Strength" slider allows to set the system whole sensitivity.

Select "Preserve Luminance" to prevent any change of the lightness
values in the image when modifying the colour. This option allows to
preserve tone balance in the image.

## Black and White

It is thanks to going to and fro from the [Black and
White](Black-and-White_addon "wikilink") tool - particularly [Luminance
Equalizer](Black-and-White_addon#Luminance_Equalizer "wikilink")- to the
"Color Toning" tool - particularly [Colour
Balance](#Color_Balance_Shadows_/_Midtones_/_Highlights "wikilink") -
that you will get the most pronounced (black and white) special effects.

## Film Simulation

- In the case of colour [film simulation](Film_Simulation "wikilink"),
  all the "Color Toning" tools are directly available.
- In the case of black and white [film
  simulation](Film_Simulation "wikilink"), it is mandatory to enable the
  the "Black and White" tool. The
  [desaturation](Black-and-White_addon#Desaturation "wikilink") method
  is almost neutral and allows a direct use of the black and white
  simulations in all the "Color Toning" tools", but without being able
  to use the special effects of the "Black and White" tool.