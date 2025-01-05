The "*Edit current image in external editor*" feature allows you to have
RawTherapee fully process the current image and immediately open it in
any external program. You can use this feature to easily send the image
to an image editor such as GIMP or Photoshop for further processing, or
you can set it up to send the image to an image viewer so that with a
single click of a button you get to see the final high quality image.

The button to send the image to an external application
[image:Image-editor.png](image:Image-editor.png "wikilink") is located
at the bottom-left of the preview panel. When using this feature,
RawTherapee processes your image and saves it as a gamma-encoded 16-bit
integer TIFF to the [temporary
folder](File_Paths#Temporary_Folder "wikilink"). These intermediate
files, due to being outside of RawTherapee's control, do not get
automatically deleted when you close RawTherapee, so you should keep
this in mind and clean them out manually.

You should be aware that GIMP-2.8 and below cannot handle 16-bit images,
so it will down-sample them to 8-bit. You should also be aware that
GIMP-2.8 and below discards all Exif data from TIFF files! This is a
GIMP bug, not a RawTherapee one. GIMP 2.9 and above handle high bit
depth images (up to 64-bit per channel!), retain all metadata, and are
quite stable, so you are advised to [get GIMP 2.9 or
higher](http://www.gimp.org/downloads/).

You can specify your external editor of choice in "*[Preferences \>
General \> External Editor](Preferences#External_Editor "wikilink")*".
Click the link for more information on specifying an external editor.