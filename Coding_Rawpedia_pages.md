<div class="pagetitle">

Coding Rawpedia pages

</div>

***<big>What follows are a set of coding rules needed to add special
features on Rawpedia pages, while using the customized Pivot
skin.</big>**''
***<big>This page is not intended to translate it, just to help those
who write documentation pages.</big>**''

## Page titles

At the very top of each page you should add this code:

<div style="margin-left: 2em;">

    <div class="pagetitle">Page Title</div>

</div>

so the page title looks as the one present in this page. Just copy/paste
the code, and edit the page title.

## Table of Contents

Even though Mediawiki automatically adds a table of contents (ToC)
whenever there are 3 or more sections in the page, if you want to force
the ToC appearing no matter what, add this code:

<div style="margin-left: 2em;">

    __TOC__

</div>

If on the other hand, you don't want a table of contents in your page,
add this code:

<div style="margin-left: 2em;">

    __NOTOC__

</div>

According to the Mediawiki documentation, those codes can be added
anywhere in the page code, but it would make more sense if you add them
just below the page title, so anybody looking at the page code will
immediately know what do you wish to happen with the ToC.

## Empty lines

No matter what your subconscious mind tells you to do, **don't add
unnecessary empty lines** just for the shake of formatting content: the
appropriate empty space needed between paragraphs, lists, images..., is
handled with CSS rules, and most probably you will only generate odd
behaviours with those extra empty lines.

## Images

There are mainly 2 kinds of images: on the one hand we have those small
images that follow text (which are positioned inline), and on the other
there are images that are blocks, with their own meaning, and somehow
isolated from the text.

### Inline images

Here you can consider the size of the images, even though they will
always be relatively small to fit in a sentence: there are images that
can be thought of as individual *letters* (as are icons), as opposed to
images that fit inside a line of text, but are larger.

#### Icons

- You can add icons to a sentence like this:


**Lorem ipsum dolor sit amet,
[image:Profile-filled.png](image:Profile-filled.png "wikilink") nullam
mauris est, pharetra a fringilla vitae.**

<!-- -->


And you will code it like this:

<div style="margin-left: 2em;">

    Lorem ipsum dolor sit amet, [[image:Profile-filled.png|image:Profile-filled.png]] nullam mauris est, pharetra a fringilla vitae.

</div>

- If you also wish to add some text that will show as a tooltip while
  hovering the icon *(hover the icon in the next example)* :


**Pellentesque tempor turpis vel orci. [Ornare
dapibus](image:preferences.png "wikilink") sit amet rutrum sapien.**

<!-- -->


You just have to add the tooltip text after a pipe symbol. And the code
will look like:

<div style="margin-left: 2em;">

    Pellentesque tempor turpis vel orci. [[image:preferences.png|Ornare dapibus]] sit amet rutrum sapien.

</div>

- There's a chance that sometimes the image is just too big to look fine
  next to the text surrounding it. In such situations you can set a
  width to shrink appropriately the image:


**Pellentesque tempor turpis vel orci. [Ornare
dapibus](image:preferences.png "wikilink") sit amet rutrum sapien.**

<!-- -->


You will add another pipe symbol, and then the desired image width:

<div style="margin-left: 2em;">

    Pellentesque tempor turpis vel orci. [[image:preferences.png|Ornare dapibus]] sit amet rutrum sapien.

</div>


However, bear in mind that more often than not it will be better to
scale down the image in an editor and reupload the smaller image.

#### Images inside tables

The way to code them follows the same principles than with inline
images, in spite that usually they will be larger images.

#### Larger images that lead or end sentences

You will code them mostly the same, with the same options, but it's
advisable that you enclose them inside a **`<div>`**, and state on which
side of the viewport (or paragraph) it should be placed. Usually they
will be placed at the left side of the paragraph.

There is a slight rendering difference if those images are included in a
plain paragraph, or in a list (this case is specially useful when
explaining the meaning of a setting or a slider, and placing the image
at the end of the paragraph):

<div style="overflow: hidden">

<figure>
<img src="wavelet_contrast_shadow.png"
title="wavelet_contrast_shadow.png" />
<figcaption>wavelet_contrast_shadow.png</figcaption>
</figure>

</div>

**Praesent efficitur enim in felis elementum, congue blandit augue
hendrerit. Donec bibendum nec nisi eget dapibus. Sed augue augue,
porttitor nec volutpat at, porttitor pellentesque tellus. Nulla tempus
vestibulum fringilla. Vivamus in orci risus. Donec vel nulla at libero
fermentum tincidunt.**

- **In hac habitasse platea dictumst. Praesent quis tellus scelerisque,
  fringilla libero quis, facilisis arcu. Donec eu tellus eget neque
  dignissim sodales vitae et quam. Donec scelerisque dignissim ex, ut
  lacinia massa fringilla eu. Mauris efficitur lacinia finibus. Sed eget
  aliquam dui. Vestibulum vel nunc a sem aliquam laoreet**
  <div style="overflow: hidden">

  <figure>
  <img src="wavelet_contrast_highlight.png"
  title="wavelet_contrast_highlight.png" />
  <figcaption>wavelet_contrast_highlight.png</figcaption>
  </figure>

  </div>

The images will be located at the beginning or the end of the paragraph,
and are coded like:

<div style="margin-left: 2em;">

    <div style="overflow: hidden">[[File:wavelet_contrast_highlight.png|left]]</div>

</div>

### Framed images

Those are big images, usually shown downscaled, so if you wish to see
them full size, you will have to click them.

They are usually styled with a frame around the image, that also
encompasses the optional image caption.

#### Image styled **as a thumbnail**

This is the default way of coding these images, and will render them
within a frame, 300px wide (plus the width of the border line, plus the
space around the image and inside the frame), and placed to the right.

In this example there are also an image caption and a link that will
lead you to the specified url when you click the image:



![](Wavelet_daubechies20.png "Wavelet_daubechies20.png") **Pellentesque
sodales non odio in venenatis. Suspendisse imperdiet laoreet dictum.
Phasellus at tortor vel ante interdum pellentesque non at justo. Nam
luctus, risus quis ullamcorper ultrices, justo justo commodo massa, ut
ultrices ex ante porta metus. Cras vestibulum turpis vel enim
condimentum gravida. Suspendisse potenti. Curabitur euismod nunc
placerat pharetra elementum. Pellentesque sodales non odio in venenatis.
Suspendisse imperdiet laoreet dictum. Phasellus at tortor vel ante
interdum pellentesque non at justo. Nam luctus, risus quis ullamcorper
ultrices, justo justo commodo massa, ut ultrices ex ante porta metus.
Cras vestibulum turpis vel enim condimentum gravida. Suspendisse
potenti. Curabitur euismod nunc placerat pharetra elementum.
Pellentesque sodales non odio in venenatis. Suspendisse imperdiet
laoreet dictum. Phasellus at tortor vel ante interdum pellentesque non
at justo. Nam luctus, risus quis ullamcorper ultrices.**

It's coded as:

<div style="margin-left: 2em;">

    [[File:Wavelet_daubechies20.png|thumb]]

</div>

#### Image styled **as a custom width thumbnail**

It's the same as a standard thumbnail, but with a custom width
***smaller*** than the original image size. If you set a size bigger
than the image, it will render the image at 100%, but no bigger.

This time a left positioning is added, too:



![](wavelet_contrast_buttons.png "wavelet_contrast_buttons.png") '''Nunc
et semper magna. Fusce vel dolor orci. Suspendisse eget velit
pellentesque turpis sodales pretium at finibus velit. Aenean dolor nibh,
tempus nec sapien eu, rhoncus posuere tortor. Sed scelerisque lacus id
risus convallis euismod. Praesent in ante non purus varius eleifend.
Nulla tempor, arcu suscipit posuere ultricies, diam elit euismod sem,
quis dignissim est arcu id quam. Nullam gravida posuere aliquam. Nunc et
semper magna. Fusce vel dolor orci. Suspendisse eget velit pellentesque
turpis sodales pretium at finibus velit. Aenean dolor nibh, tempus nec
sapien eu, rhoncus posuere tortor. Sed scelerisque lacus id risus
convallis euismod. Praesent in ante non purus varius eleifend. Nulla
tempor, arcu suscipit posuere ultricies, diam elit euismod sem, quis
dignissim est arcu id quam. Nullam gravida posuere aliquam. Nunc et
semper magna. Fusce vel dolor orci. Suspendisse eget velit pellentesque
turpis sodales pretium at finibus velit. Aenean dolor nibh.

<div style="margin-left: 2em;">

    [[File:wavelet_contrast_buttons.png|thumb]]

</div>

#### Image **with a frame (but not a thumbnail)** and it's original size



![](Wavelet_detail_size.png "Wavelet_detail_size.png") **Mauris dui
erat, viverra ac magna eu, egestas consequat mi. Integer tristique,
justo quis dignissim vehicula, leo quam tincidunt mi, nec porttitor nunc
augue quis enim. Nunc id sapien ipsum. Fusce diam mauris, placerat eu
arcu vitae, fringilla pulvinar magna. Orci varius natoque penatibus et
magnis dis parturient montes, nascetur ridiculus mus. Nam eget hendrerit
ex. Donec posuere dictum nunc eu placerat. Curabitur sed turpis
vestibulum, euismod purus et, laoreet tellus. Mauris eget ex nisl.
Mauris ultrices consequat felis sit amet euismod. Mauris dui erat,
viverra ac magna eu, egestas consequat mi. Integer tristique, justo quis
dignissim vehicula, leo quam tincidunt mi, nec porttitor nunc augue quis
enim. Nunc id sapien ipsum. Fusce diam mauris, placerat eu arcu vitae,
fringilla pulvinar magna. Orci varius natoque penatibus et magnis dis
parturient montes, nascetur ridiculus mus. Nam eget hendrerit ex.
Curabitur sed turpis vestibulum, euismod purus et, laoreet tellus.
Mauris eget ex nisl. Mauris ultrices consequat felis sit amet euismod.
Mauris dui erat, viverra ac magna eu, egestas consequat mi. Integer
tristique, justo quis dignissim vehicula, leo quam tincidunt mi, nec
porttitor nunc augue quis enim. Nunc id sapien ipsum.**

Take into account that it won't matter if you set a custom width, as it
will always be rendered with its original size:

<div style="margin-left: 2em;">

    [[File:Wavelet_detail_size.png|right]]

</div>

#### **Full width images**

*Full width* means that the image will be rendered as wider as possible,
until it fills the available space.

There are two variations of the same concept: images big enough to fill
the whole space, and images that at 100% size won't fill the whole
space.

##### Heroed images

These are images that almost fill the width of the screen (except for
the sidebar). The concept is similar as in *Hero images*, thus the name
*heroed*.

With the next example we are displaying a big image (bigger than the
viewport size), full width, and removing the possibility to click on it
(`link=`) :

<figure>
<img src="Rt_55_trains.png" title="Rt_55_trains.png" />
<figcaption>Rt_55_trains.png</figcaption>
</figure>

Please note that you need to add the `none` option to prevent the image
to overflow the screen.

Note also that you have to add the `frame` option to render the frame
around the image. With the option `class=heroed` the image is given its
full width:

<div style="margin-left: 2em;">

    [[[File:Rt_55_trains.png|none]]

</div>

##### Centered images

In this case the images won't fill the full width, because they aren't
big enough. But we want them to be prominent, so we use the same
formatting as before, but getting some important side effects:

**Nullam neque purus, tincidunt sit amet commodo nec, imperdiet vel leo.
Integer nec mollis elit, in auctor leo. Proin et neque quis tellus
laoreet faucibus. Suspendisse efficitur ligula velit, eget consequat
ante mollis id.**
![](Rt57_histogram_wide_labeled.png "Rt57_histogram_wide_labeled.png")
**Praesent sollicitudin bibendum purus, eget viverra lectus luctus
tincidunt. Orci varius natoque penatibus et magnis dis parturient
montes, nascetur ridiculus mus. Etiam justo neque, volutpat ultricies
lacinia ut, blandit eget ex.**

As seen, the image is centered and the text doesn't wrap around the
image: that's because we have set the `none` option.

<div style="margin-left: 2em;">

    [[File:Rt57_histogram_wide_labeled.png|none]]

</div>

However, if you forget to set the `none` option, or you set the
`left/right` options, on larger screens the text following the image
will wrap around it, **but on smaller screens the image will overflow
the screen**:

**Vivamus maximus nunc suscipit luctus iaculis. Pellentesque rutrum ante
sit amet leo consectetur imperdiet. Nullam elementum nisl sed volutpat
ultrices.**
![](Rt_filmstrip_21_toolbar-visible.jpg "Rt_filmstrip_21_toolbar-visible.jpg")
**Vestibulum ante ipsum primis in faucibus orci luctus et ultrices
posuere cubilia Curae; Suspendisse blandit enim eget nulla mattis
accumsan. Mauris ut lobortis massa. In hac habitasse platea dictumst.
Donec condimentum, nulla ut sagittis porttitor, est lacus laoreet mi,
vitae gravida purus dui non odio.**

This is the incorrect code that leads to the previous image:

<div style="margin-left: 2em;">

    ...sed volutpat ultrices.
    [[File:Rt_filmstrip_21_toolbar-visible.jpg|frame]]
    Vestibulum ante ipsum ...

</div>

### Galleries

Galleries are mainly lists of images, shown one next to another.

The stylesheet is ready to let you show 2, 3 or 4 images side by side.
Whenever you need to show more images altogether, consider breaking them
into groups, with each group in one row.

To code a gallery you will follow these steps:

1.  enclose every row of the gallery inside a **`<div>`**
2.  start each row of the gallery as an unordered list, and assign to it
    the `leftalign` class
3.  each list element will be assigned a class depending on the number
    of images to show in a row:
    - `RPgallery` is the class to assign when there will be 4 images in
      a row
    - `RP3inarow` will be the choice for 3 images
    - `RPside2side` for 2 images, usually big images to compare them
      with enough detail
4.  include in every list element the images as inline images, with the
    options `thumb`, `left`, the image width, and the caption

#### 4 images in a row

With this example code:

<div style="margin-left: 2em;">

    <div><ul class="leftalign">
    <li class="RPgallery"> [[File:wavelet_pic.png|thumb]] </li>
    <li class="RPgallery"> [[File:wavelet_contrast_15C+_WL.png|thumb]] </li>
    <li class="RPgallery"> [[File:wavelet_contrast_15C+_H3S6.png|thumb]] </li>
    <li class="RPgallery"> [[File:wavelet_contrast_15C+_H3S6_Str50.png|thumb]] </li>
    </ul></div>

</div>

the images will render as:

<div>

- <figure>
  <img src="wavelet_pic.png" title="wavelet_pic.png" />
  <figcaption>wavelet_pic.png</figcaption>
  </figure>

- <figure>
  <img src="wavelet_contrast_15C+_WL.png"
  title="wavelet_contrast_15C+_WL.png" />
  <figcaption>wavelet_contrast_15C+_WL.png</figcaption>
  </figure>

- <figure>
  <img src="wavelet_contrast_15C+_H3S6.png"
  title="wavelet_contrast_15C+_H3S6.png" />
  <figcaption>wavelet_contrast_15C+_H3S6.png</figcaption>
  </figure>

- <figure>
  <img src="wavelet_contrast_15C+_H3S6_Str50.png"
  title="wavelet_contrast_15C+_H3S6_Str50.png" />
  <figcaption>wavelet_contrast_15C+_H3S6_Str50.png</figcaption>
  </figure>

</div>

On bigger screens, the images will be shown all in a row, no matter if
the size set as an option is bigger. But when the screen gets smaller,
there will be a breakpoint where those images will be too small, so they
split into a couple of rows, and then the image size set as an option
becomes really important (the image could get four times as big). Thus,
when coding galleries intended for 4 images in a row, it's wise to set
their sizes around 300-400 pixels.

#### 3 images in a row

In this case, with this example code:

<div style="margin-left: 2em;">

    <div><ul class="leftalign">
    <li class="RP3inarow"> [[File:wavelet_chrom_Link_50_Str50.png|thumb]] </li>
    <li class="RP3inarow"> [[File:wavelet_toning_opBYfull.png|thumb]] </li>
    <li class="RP3inarow"> [[File:wavelet_toning_opBYfull_curve.png|thumb]] </li>
    </ul></div>

</div>

the images will render as:

<div>

- <figure>
  <img src="wavelet_chrom_Link_50_Str50.png"
  title="wavelet_chrom_Link_50_Str50.png" />
  <figcaption>wavelet_chrom_Link_50_Str50.png</figcaption>
  </figure>

- <figure>
  <img src="wavelet_toning_opBYfull.png"
  title="wavelet_toning_opBYfull.png" />
  <figcaption>wavelet_toning_opBYfull.png</figcaption>
  </figure>

- <figure>
  <img src="wavelet_toning_opBYfull_curve.png"
  title="wavelet_toning_opBYfull_curve.png" />
  <figcaption>wavelet_toning_opBYfull_curve.png</figcaption>
  </figure>

</div>

Notice that not all images must have the same width set.

#### Images compared side to side

Now we have the chance to show a couple of big images, to appreciate the
differences between them.

If we code like this:

<div style="margin-left: 2em;">

    <div><ul class="leftalign">
    <li class="RPside2side"> [[File:wavelet_smc_original.png|thumb]] </li>
    <li class="RPside2side"> [[File:wavelet_clarity_ML60MC30.png|thumb]] </li>
    </ul></div>

</div>

Will get:

<div>

- <figure>
  <img src="wavelet_smc_original.png" title="wavelet_smc_original.png" />
  <figcaption>wavelet_smc_original.png</figcaption>
  </figure>

- <figure>
  <img src="wavelet_clarity_ML60MC30.png"
  title="wavelet_clarity_ML60MC30.png" />
  <figcaption>wavelet_clarity_ML60MC30.png</figcaption>
  </figure>

</div>

And the images will remain side to side until you look at them in a
small smartphone screen.

Essentially the `RPside2side` class is meant to keep the images side to
side, to reinforce the idea of a comparison.

## Responsive tables

*work in progress*

## Lists

*work in progress*

## Sidebar links

*work in progress*