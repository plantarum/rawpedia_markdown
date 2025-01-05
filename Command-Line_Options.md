## Explanation


`<`Chevrons`>` indicate parameters you can change.

`[`Square brackets`]` mean the parameter is not mandatory.

The pipe symbol `|` indicates a choice of one or the other.

The dash symbol `-` denotes a range of possible values from one to the
other.

Usage:


`rawtherapee `<selected dir>


Start [File Browser](The_File_Browser_Tab "wikilink") inside directory.

`rawtherapee `<file>


Start [Image Editor](The_Image_Editor_Tab "wikilink") with file.

<code>rawtherapee <options> -c

<dir>

\|<files></code>


Convert files in batch with default parameters if no <options>
specified.

<!-- -->


`-w`


Do not open the Windows console. This option is available in Windows
only. If you pass parameters to the RawTherapee executable it spawns a
console window so that you can see the verbose output of your
processing. Normally Windows closes this console directly after
RawTherapee is terminated. To let you see the output we added a prompt
which waits for you to hit a key before closing the console. By
specifying `-w` no console will be opened and therefore no key press is
needed. Useful if you want to invoke rawtherapee.exe in batch, e.g. from
a PowerShell script.

Other options used with `-c` (`-c` must be the last option):


<code>rawtherapee \[-o

<output>

\|-O

<output>

\] \[-s\|-S\] \[-p <files>\] \[-d\] \[-j\[1-100\]
\[-js\<1-3\>\]\|\[-b\<8\|16\>\] \<\[-t\[z\] \| \[-n\]\]\] \[-Y\] -c
<input></code>

<code>-o <file>\|

<dir>

</code>


Select output file or directory.

<code>-O <file>\|

<dir>

</code>


Select output file or directory and copy PP3 file into it.

`-s`


Include the PP3 file next to the input file (with the same name) to
build the image parameters, e.g. for photo.raw there should be a
photo.raw.pp3 file in the same directory. If the file does not exist,
internal default (neutral) values (not those in "Default.pp3") will be
used.

`-S`


Like `-s` but skip if the PP3 file does not exist.

`-p <file.pp3>`


Specify PP3 file to be used for all conversions. You can specify as many
`-p` options as you like (see description below).

`-d`


Use the default raw or non-raw PP3 file as set in
"[Preferences](Main_Page#Preferences "wikilink") \> [Image
Processing](Image_Processing_Tab "wikilink") \> [Default Processing
Profile](Image_Processing_Tab#Default_Processing_Profile "wikilink")"

`-j[1-100]`


Specify output to be JPEG (on by default). Optionally add compression
1-100 (default value: 92).

`-js<1-3>`


Specify the JPEG [chroma
subsampling](http://en.wikipedia.org/wiki/Chroma_subsampling) parameter,
where:


1 = Best compression: 2x2, 1x1, 1x1 (4:2:0)


Chroma halved vertically and horizontally.

2 = Balanced: 2x1, 1x1, 1x1 (4:2:2)


Chroma halved horizontally.

3 = Best quality: 1x1, 1x1, 1x1 (4:4:4)


No chroma subsampling.

`-b<8|16>`


Specify bit depth per channel (only applies to TIFF and PNG output).

`-t[z]`


Specify output to be TIFF (16-bit if `-b8` is not set).

Uncompressed by default, or ZIP compression with 'z'.

`-n`


Specify output to be compressed PNG (16-bit if `-b8` is not set).

`-Y`


Overwrite output if present.

Your PP3 files can be incomplete, RawTherapee will set the values as
follows:

1.  A new profile is created using internal default (neutral) values
    (hard-coded into RawTherapee),
2.  then overridden by those found in the default raw or non-raw PP3
    file (if `-d` has been set),
3.  then overridden by those found in the PP3 files provided by `-p`,
    each one overriding the previous values,
4.  then overridden by the sidecar file if `-s` is set and if the file
    exists; the time where the sidecar file is used depends on the
    position of the `-s` switch in the command line relative to the `-p`
    parameters, e.g.

    `-p first.pp3 -p second.pp3 -s -p fourth.pp3`

## Redirect Output

To redirect RawTherapee's output to a text file, you have to start it
from a console and append the redirection code as follows:

Windows (cmd.exe)
`rawtherapee.exe > rtlog.txt 2>&1`

Linux
`rawtherapee &> rtlog.txt`

## Examples

### Example 1

In Linux, process a single raw which resides in /tmp and is called
"photo.raw", use its sidecar file "photo.raw.pp3" during conversion,
save it in the same directory as "foo.tif", and overwrite the file
"foo.tif" if it exists:

`rawtherapee -o /tmp/foo.tif -s -t -Y -c /tmp/photo.raw`

### Example 2

In the next example, we'll assume that you want to quickly process all
your raw photos from the /tmp/jane01 directory to a web sub-directory by
using the default profile as a basis, using the sidecar profile if it
exist, but with removing some Exif tags (e.g. the camera's serial
number) and adding some IPTC tags (e.g. your usual copyright
parameters), plus resize and sharpen the image for the web (spread over
multiple lines for clarity):

`rawtherapee -o /tmp/Jane01/web -p ~/profiles/iptc.pp3 -s -p ~/profiles/exif.pp3 -p ~/profiles/web.pp3 -t -Y -d -c /tmp/Jane01/`

The processing profile will be built as follows:

1.  A new profile is created using internal default values (hard-coded
    into RawTherapee),
2.  then overridden by those from the default raw profile (`-d`),
3.  then overridden by those found in iptc.pp3,
4.  then overridden by those found in the sidecar file (`-s`) if it
    exists, so you can force some IPTC tags even if already set by
    iptc.pp3,
5.  then overridden by those found in exif.pp3, so you can force the
    profile to erase some tags,
6.  then overridden by those found in web.pp3, to resize and sharpen the
    image, and make sure that the output colorspace is sRGB.

As you can see, the position of the `-s` switch tells when to load the
sidecar profile relative to the other `-p` parameters. That is not the
case for the `-d` switch.

### Example 3

In the third example, we will see how long it takes to process every raw
file in a directory, assuming that each raw photo has a corresponding
processing profile, and discard each output file:

`time { for f in /home/user/photos/2011-11-11/*.raw; do rawtherapee -o /dev/null -S -t -Y -c "$f"; done }`