Open a photo for editing, tweak it, click on *Save current image*
![Image:gtk-save-large.png](gtk-save-large.png "Image:gtk-save-large.png"),
add it to the tail of the processing queue and click *OK*. Go to the
*Queue* tab. You will see your photo there, waiting to be processed.

The *File format* panel resides in the top-right side of the *Queue*
tab. You can save to JPG (8 bits per channel), TIFF (8 or 16 bits per
channel) and to PNG (also 8 or 16 bits per channel). You can also select
*Save processing parameters with image* - this options writes a sidecar
file with all your adjustments made to that photo in a plain text file.
This file will have the same filename as your photo, but it will have a
".pp3" extension.

You can set where you want the resulting JPG, PNG or TIFF image saved to
by entering an appropriate template in the *Use template* field in the
*Output Directory* panel. To find out how to create a template, hover
your mouse over the *Use template* input box and a tooltip with an
explanation will pop up:

<code>

`You can use the following formatting strings:`
<b>`%f`</b>`, `<b>`%d1`</b>`, `<b>`%d2`</b>`, ..., `<b>`%p1`</b>`, `<b>`%p2`</b>`, ..., `<b>`%r`</b>`, `<b>`%s1`</b>`, `<b>`%s2`</b>`, ...`

`These formatting strings refer to the different parts of the photo's pathname, some attributes of the photo or an arbitrary sequence index in the batch job. For example, if the photo being processed has the following pathname:`
<b><i>`/home/tom/photos/2010-10-31/dsc0042.nef`</i></b>
`the meaning of the formatting strings are:`
<b>`%d4`</b>` = `<i>`home`</i>
<b>`%d3`</b>` = `<i>`tom`</i>
<b>`%d2`</b>` = `<i>`photos`</i>
<b>`%d1`</b>` = `<i>`2010-10-31`</i>
<b>`%f`</b>`  = `<i>`dsc0042`</i>
<b>`%p1`</b>` = `<i>`/home/tom/photos/2010-10-31/`</i>
<b>`%p2`</b>` = `<i>`/home/tom/photos/`</i>
<b>`%p3`</b>` = `<i>`/home/tom/`</i>
<b>`%p4`</b>` = `<i>`/home/`</i>

<b>`%r`</b>` will be replaced by the rank of the photo. If the photo is unranked, %r will be replaced by '0'. If the photo is in the trash bin, %r will be replaced by 'x'.`
<b>`%s1`</b>`, `<b>`%s2`</b>`, etc. will be replaced by a sequence index which is padded to between 1 and 9 digits. The sequence index will start at one each time the queue processing is started and is incremented by one for each image processed.`

`If you want to save the output image where the original is, write:`
<b>`%p1/%f`</b>

`If you want to save the output image in a directory named "`<i>`converted`</i>`" located in the directory of the opened image, write:`
<b>`%p1/converted/%f`</b>

`If you want to save the output image in a directory named "`<i>`/home/tom/photos/converted/2010-10-31`</i>`", write:`
<b>`%p2/converted/%d1/%f`</b>

</code>

Alternatively, you can save directly to a specific directory, but in the
long run it is much easier to use a template.

On the left you see a *Start/Stop* processing button, and an *Auto
start* checkbox. If *Auto start* is enabled, every time a raw is sent to
the queue, processing will start immediately. Usually you will not want
this, as this will use up your CPU on developing the photos in the
queue, and as a result all adjustments you do while the queue is running
will take much longer to get applied so that you can see their effect in
the preview - RT will become sluggish. If *Auto start* is unchecked, you
will have to activate the queue manually by clicking the *Start
processing* button once ready to do so. You can pause the queue by
pressing the *Stop processing* button, but RawTherapee will first finish
processing the current photo.

You can delete the contents of the processing queue by right-clicking on
a thumbnail and choosing "*Select all \> Cancel job*".

You can exit the program and restart it later; the batch queue will
still be there. The queue can even survive a crash of RawTherapee, as
the batch queue info is written to disk each time you add a photo to it,
each time a photo is done processing and each time you delete a photo
from it.