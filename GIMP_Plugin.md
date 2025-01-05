This article describes how to make it possible to have GIMP open raw
images by using RawTherapee.

# Requirements

- RawTherapee 5.2
- GIMP 2.9.5
- The "`file-rawtherapee`" plugin

# Installation

1.  Perhaps in the future the RawTherapee installer or even GIMP itself
    will contain the plugin. For now you must compile it yourself.
    - If you already have [the source
      code](Linux#Clone_the_source "wikilink"), go into the
      `tools/gimp-plugin` folder.
    - If you do not have the source code, just download these files:
      [`file-formats.h`](https://raw.githubusercontent.com/Beep6581/RawTherapee/dev/tools/gimp-plugin/file-formats.h)
      and
      [`file-rawtherapee.c`](https://github.com/Beep6581/RawTherapee/raw/dev/tools/gimp-plugin/file-rawtherapee.c)
2.  Compile the plugin:

`gimptool-2.0 --build file-rawtherapee.c`