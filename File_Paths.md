RawTherapee makes use of a "cache" folder to store temporary files which
are safe to delete, and a "config" folder which stores your RawTherapee
settings and saved custom processing profiles. These folders reside in a
special place, described below, and have a name that begins with the
word "RawTherapee" optionally followed by a suffix. This suffix is set
by the person who made the build of RawTherapee you're using. Some
examples of what it can look like:

- RawTherapee
- RawTherapee**4**
- RawTherapee**4.0.12**
- RawTherapee**4.2**
- RawTherapee**_test**

The first part, "RawTherapee", is hard-coded. The second part, the
suffix, is up to the person who made the build. It might be specific,
like "4.0.12", it could be general, like "4", it could be anything else,
like "_test", or it could be not set. Take this into account when
looking in the locations specified below.

## Config

The "config" folder contains the "options" file which contains all of
your settings from [Preferences](Preferences "wikilink"), the "batch"
folder which stores temporary [processing
profiles](Sidecar_Files_-_Processing_Profiles "wikilink") of the photos
you sent to the [Queue](The_Batch_Queue "wikilink"), and the "profiles"
folder where you can save your custom [processing
profiles](Sidecar_Files_-_Processing_Profiles "wikilink") to if you want
them to appear in RawTherapee's drop-down list. You could include this
folder in your backups so that you can regain all of your settings and
custom processing profiles if you install RawTherapee on a new system.

Default locations for this folder (look for the "RawTherapee\*" prefix
as described above):

"*Config*" in Windows XP
`%USERPROFILE%\Local Settings\Application Data\`

"*Config*" in Windows 7, 8 and 10
`%LOCALAPPDATA%\`

"*Config*" in Linux
`~/.config/`

"*Config*" in OS X
`~/.config/`

Under the Finder's 'Go' menu click 'Go to Folder' (shortcut
Command+Shift+g), you can then type/paste any path you want to navigate
to, even if it's hidden.

## Cache

The "*cache*" folder contains cached thumbnails, processing profiles,
metadata and histograms.

Keep an eye on the "cache" folder as over time it may grow considerably
in size! This is mostly due to the cached thumbnails which are stored in
the "images" sub-folder. Deleting the "images" sub-folder is safe, you
will not lose any image settings, RawTherapee will just have to
regenerate the thumbnails.

Default locations for this folder (look for the "RawTherapee\*" prefix
as described above):

"*Cache*" in Windows XP
`%USERPROFILE%\Local Settings\Application Data\`

"*Cache*" in Windows 7, 8 and 10
`%LOCALAPPDATA%\`

"*Cache*" in Linux
`~/.cache/`

"*Cache*" in OS X
`~/.cache/`

Under the Finder's 'Go' menu click 'Go to Folder' (shortcut
Command+Shift+g), you can then type/paste any path you want to navigate
to, even if it's hidden.

## Custom config and cache folders

Even though the path and name of the cache and config folders is
hard-coded into RawTherapee, as of version 4.0.12.33 you can change them
to any **absolute** path by using the `RT_SETTINGS` and `RT_CACHE`
environment variables. How you do that depends on your operating system,
so just search on the internet for "how to set environment variables in
*<your operating system>*".

Some examples:

Windows
`RT_SETTINGS=%LOCALAPPDATA%\rawtherapee\4.2`

`RT_CACHE=C:\Users\Bob\AppData\Local\rtcache`

Linux and OS X
`RT_SETTINGS=/home/bob/.config/rawtherapee/4.2`

`RT_CACHE=/home/bob/junk/rtcache`

## Processing Profiles

If you create your own [processing
profiles](Sidecar_Files_-_Processing_Profiles "wikilink"), to have them
appear in RawTherapee's "Processing Profiles" list you should save them
to the "profiles" folder which you will find inside the "config" folder
as described above.

## Temporary Folder

The "[Edit Current Image in External
Editor](Edit_Current_Image_in_External_Editor "wikilink")" tool stores
intermediate image files in a temporary folder:

Windows
The default location is the one stored in the `$TEMP` environment
variable, which is usually `%LOCALAPPDATA%/Temp`

If you do not have the `$TEMP` environment variable set, `C:\` is used.

Linux and OS X
The default location is the one stored in the `$TMPDIR` environment
variable, which is usually `/tmp`

If you do not have the `$TMPDIR` environment variable set, `/tmp` is
used.