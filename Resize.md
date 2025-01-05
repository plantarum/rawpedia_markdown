Resizing can be applied to the cropped area or to the whole image.

Choose your preferred resizing algorithm:

- Nearest
- Lanczos


Lanczos results in the highest quality sampling and is therefore the
recommended and default option.

Versions of RawTherapee prior to 4.2.152 also have these additional
resizing algorithms, but their use is discouraged as "Lanczos" produces
the best results, which is why they were removed in newer versions:

- Bilinear
- Bicubic
- Bicubic (Softer)
- Bicubic (Sharper)

You can resize according to:

- Scale


e.g. have the resulting image 0.5 times the size of the full one,

- Width


by specifying the desired width so that the height is automatically and
proportionally scaled,

- Height


by specifying the desired height so that the width is automatically and
proportionally scaled,

- Bounding Box


by specifying the maximum width and height you want your image to have,
and leave it up to RawTherapee to figure out how to proportionally fit
your image into this box.

The effects of the *Resize* tool will not be shown in the preview. This
is a limitation of RawTherapee's current engine. Resizing is done at the
end of the processing pipeline. The output image will of course be
resized.

## Post-Resize Sharpening

![](Rt-4.2.235_postresizesharpening.png "Rt-4.2.235_postresizesharpening.png")
Resizing an image often leads to a loss of sharpness, so it is common
practice to sharpen the image again after having resized it. With the
Post-Resize Sharpening tool you can save crystal-clear images straight
away with no further hassle. Because this tool works on the image after
it is resized, you cannot use the preview to see what it will do, though
this is not a problem because the procedure for finding the right values
is straightforward.

The default values work great, but if you want to change them, here's
how:

1.  Tweak your image as you usually would and enable resizing (e.g.
    downscale using the Lanczos method to a 900px bounding box),
2.  Save the image to a lossless format such as TIFF,
3.  Open that saved TIFF, apply the (Neutral) processing profile if that
    wasn't done automatically, and enable the Sharpening tool in the
    Detail tab,
4.  Zoom to 100% (1:1) and tweak the Sharpening tool's parameters until
    you get a result that satisfies you. These are the values you should
    use in the Post-Resize Sharpening tool.
5.  Go back to the raw image, enable the Post-Resize Sharpening tool and
    set it up with the values from the previous step.

In most cases the default values in the Post-Resize Sharpening tool work
great, so give them a try before fiddling.

For technical reasons, the Post-Resize Sharpening tool is only available
when you use the "Lanczos" resizing method.