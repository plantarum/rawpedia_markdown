RawTherapee 4 does all calculations in precise 32-bit [floating
point](https://en.wikipedia.org/wiki/Floating_point) notation (in
contrast to 16-bit integer as used in many other converters like
[dcraw](https://en.wikipedia.org/wiki/Dcraw) and also in RawTherapee up
to version 3.0) so nothing gets rounded off and lost.

Classical converters work with 16-bit integer numbers. A pixel channel
has values ranging from 0-65535 in 16-bit (to increase precision
converters usually multiply the 12-14 bit camera values to fill the
16-bit range). The numbers have no fractions, so for example there is no
value between 102 and 103. In contrast, floating point numbers store a
value at a far wider range with a precision of 6-7 significant digits.
This helps especially in the highlights, where higher ranges can be
recovered. It allows intermediate results in the processing chain to
over- or undershoot temporarily without losing information. The fraction
values possible also help to smooth color transitions to prevent color
banding. And not the least, floating point makes the life easier for
developers which don't need to worry as much about rounding errors or
clipping when developing image algorithms for RawTherapee.

The downside is the RAM space floating point numbers require, which is
exactly twice that of 16-bit integer. Together with the ever-increasing
megapixel count of digital cameras a 32-bit operating system can quite
easily run out of memory and cause RawTherapee to crash. Therefore a
64-bit operating system is highly advised for stability. If you have
problems running RT on a 32-bit system, try the following:

- As a general rule, you should avoid having folders with too many raw
  photos in them as each photo takes up memory when displayed in
  RawTherapee's File Browser tab. Try not to have more than 100 photos
  per folder.
- RawTherapee uses more RAM while you are using the File Browser tab, so
  avoid opening that tab while you are processing photos.
- Use 4-Gigabyte Tuning in Windows. See "[4-Gigabyte Tuning: BCDEdit and
  Boot.ini](http://msdn.microsoft.com/en-us/library/bb613473%28VS.85%29.aspx)"
  for an explanation of what it is, and find out how to do it by reading
  the guide "[How to set the /3GB Startup Switch in Windows XP and
  Vista](http://avatechsupport.blogspot.se/2008/03/how-to-set-3gb-startup-switch-in.html)".
- Close other programs while working in RawTherapee.
- Close the Image Editor tab when you're done editing to free up memory.
- Turn off "auto-start" in the batch queue. Only add photos to the batch
  queue once you are done editing all of them, and then start it. Use
  the batch queue, do not use the immediate save button.
- Change to a directory with few or no photos in it before starting the
  batch queue.
- You can free some memory by deleting (or moving to a different folder,
  or renaming to something like .unusedicc) all the .icc profiles in
  iccprofiles\input for the cameras you do not use.
- Assure that the Dark-frames Directory and the Flat-fields Directory in
  Preferences do not point to folders containing raw-files if you do not
  use Dark-frames or Flat-fields.
- The most memory-intensive tools are [Tone
  Mapping](Tone_Mapping "wikilink"), [Contrast by Detail
  Levels](Contrast_by_Detail_Levels "wikilink") and [Highlight
  Reconstruction](Exposure#Highlight_Reconstruction "wikilink") using
  "Color Propagation", so you might need to avoid using them if your
  machine and operating system are not up to standard.

[Category:General](Category:General "wikilink")