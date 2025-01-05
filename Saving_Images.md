Your original raw file will never be altered by RawTherapee.

There are several ways of saving an image from the [Image
Editor](The_Image_Editor_Tab "wikilink") tab:

- ![Image:gtk-save-large.png](gtk-save-large.png "Image:gtk-save-large.png")
  Save immediately from the Editor tab,
- ![Image:processing.png](processing.png "Image:processing.png") Save
  via the [Batch Queue](The_Batch_Queue "wikilink"),
- ![<File:Image-editor.png>](Image-editor.png "File:Image-editor.png")
  "[Edit Current Image in External
  Editor](Edit_Current_Image_in_External_Editor "wikilink")" (described
  in its own article).

## Save Immediately

In the Editor tab, if you click on the little hard disk icon
![Image:gtk-save-large.png](gtk-save-large.png "Image:gtk-save-large.png")
at the bottom-left of the preview image, or hit the **Ctrl+s** shortcut,
you can "*Save immediately*". This works as a standard "Save As" dialog.
You can select the name and location for the output file (RawTherapee
will automatically add the extension based on the chosen format), choose
a JPEG, TIFF or PNG format ([8-bit and
16-bit](8-bit_and_16-bit "wikilink") for TIFF and PNG), set the
compression ratio, choose whether you want the processing profile saved
alongside the output image, etc. The last option lets you choose whether
you want to "*Save immediately*" or "*Put to the head/tail of the
processing queue*". A shortcut for *OK* is **Ctrl+Enter**. If you choose
to "*Save immediately*", RawTherapee will be busy saving your photo as
soon as you click "*OK*", so it will be less responsive to any
adjustments you might try doing while it's busy saving, and it will also
take longer to open other images as long as it's busy saving this one.
It is generally recommended that you use the queue if you're working on
more than one image.

## Put to the Head / Tail of the Processing Queue

If you click on the gears icon
![Image:processing.png](processing.png "Image:processing.png") or in the
"*Save*" window choose "*Put to head or tail of the processing queue*",
your image will be kept in a queue of files to be processed, so
RawTherapee can make the most of your CPU and be responsive while you
tweak your photos. Once you're done tweaking and adding them to the
queue, you can have RawTherapee start processing the queue while you go
and enjoy some tea. The benefit of putting it to the queue using the
"*Save*" window is that you can individually change the file format,
name and destination of each image, whereas putting images to the queue
without using the "*Save*" window will use the settings from the "[Batch
Queue](The_Batch_Queue "wikilink")" tab.

## Naming

If your original raw file was called "photo_1000.raw", the default
processed file name will be "photo_1000.jpg" (or .tif or .png). There is
an option in the "*Save current image*" window: "*Automatically add a
suffix if the file already exists*". When checked, you can make
different versions of one raw, which will be saved as "photo_1000.jpg",
"photo_1000**-1**.jpg", "photo_1000**-2**.jpg", etc. The same applies
when you send different versions of the same image to the [batch
queue](The_Batch_Queue "wikilink").