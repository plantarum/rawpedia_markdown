The most likely reason RawTherapee might crash immediately after
starting is because it loads a problematic processing profile (PP3, they
store all the tweaks you make in RawTherapee, one PP3 per photo) or a
problematic photo. The reason one of those could be problematic might be
because it is corrupt, but it could also be that the file in itself is
fine but triggers a bug in RawTherapee, or some aspect of it is
unsupported, such as character encoding of the metadata, multiple layers
in an image, more or less than three color channels, etc.

**Note:** RawTherapee only supports images with three color channels -
RGB (or possibly CMY). If you try opening a directory which contains
grayscale image files, or ones with four color channels (e.g. CMYK)
RawTherapee will throw up an error popup window. Move these out from the
startup directory elsewhere, as described below. Of course it might be a
valid RGB photo or processing profile that crashes RawTherapee, but
first check for non-RGB ones, as these are quite common causes of
crashes.

To find the cause of the problem, we will begin with the least invasive
and most informative steps, and escalate up to the most destructive
steps if the informative ones do not help.

1.  First, have RawTherapee use a different startup folder:
    1.  Find the "options" file as described in the [File
        paths](File_paths "wikilink") page.
    2.  Open the "options" file in a text editor like
        [Notepad++](http://notepad-plus-plus.org/) and see what these
        two lines are:

        `StartupDirectory=last`

        `StartupPath=C:\\Documents and Settings\\Administrator`
    3.  Make sure the first one is

        `StartupDirectory=last`
    4.  Create a new empty directory somewhere on your disk,

        Windows: `C:\\foo`

        Linux: `/home/bob/foo`
    5.  Change the `StartupPath=` argument to the directory you just
        created (it must be an **existing** directory which does not
        contain any photos or PP3 files, and you have to type the whole,
        absolute path, no shortcuts, with double back-slashes if you use
        Windows) e.g.

        Windows: `StartupPath=C:\\foo`

        Linux: `StartupPath=/home/bob/foo`
    6.  Now try starting RawTherapee again. If it works, then you know
        that one of the photos or PP3 files in the original
        `StartupPath` is faulty, so skip step 2 and jump straight to
        step 3. However, if RawTherapee still crashes right after
        starting, proceed to the next step.
2.  Delete the `batch` folder:
    1.  Find the "batch" folder as described in the [File
        paths](File_paths "wikilink") page, and delete it.
    2.  Now try starting RawTherapee again. If it works, then you know
        that one of the processing profiles of the photos you sent to
        the Queue is faulty. Finding which one would be a pain in the
        ass and I wouldn't bother, but if you really want to, then the
        next main point section "Nail it down" applies. If it doesn't
        work, then the problem is not a faulty photo or PP3, the problem
        lies elsewhere, outside the scope of this guide.
3.  Delete the `cache` folder:
    1.  Find the "cache" folder as described in the [File
        paths](File_paths "wikilink") page.
    2.  Move (cut) the `cache` directory elsewhere, somewhere where
        RawTherapee will not look. Instead of moving it you can just
        delete this `cache` directory, but be warned: if you set
        RawTherapee to only store processing profiles (PP3) in the
        cache, then you will lose your tweaks. You will not lose any
        photos. If you do not know whether you did, then you did not,
        because by default RT stores processing profiles alongside the
        raw files, not in the cache.
    3.  Now try starting RawTherapee again. If it works, then you know
        that one of the processing profiles files in the cache is
        faulty. Finding which one would be a pain in the ass and I
        wouldn't bother, but if you really want to, then the next main
        point section "Nail it down" applies. If it doesn't work, then
        the problem is not a faulty photo or PP3, the problem lies
        elsewhere, outside the scope of this guide.
4.  Nail it down

    You've established that either a processing profile or photo is to
    blame for the crash. It would be most helpful if you could nail the
    problem down to a specific file, so that we can analyze it and
    develop techniques for dealing with such an enemy. See the [guide to
    stack-backtraces](How_to_write_useful_bug_reports#When_RawTherapee_crashes_-_An_introduction_to_stack_backtraces "wikilink").
    If you can follow those instructions, a backtrace would be of great
    value, yet even a backtrace might not expose the problematic file,
    so read on. By now you should know which directory contains the
    faulty file(s) and you should have either set RawTherapee to start
    up using a different directory, or you have moved the cache out
    somewhere else. To make it clear, let us assume three things:

    - That the directory which contains a file that crashes RawTherapee
      is `C:\photos\bugs` and that your options file had
      `StartupPath=C:\\photos\\bugs`
    - That you changed `StartupPath=C:\\photos\\bugs` in the "options"
      file to the existing and empty `StartupPath=C:\\foo`
    - That there are 100 photos in the faulty directory, `001.raw` -
      `100.raw`


    Let's find the faulty file:

    1.  This is grunt work. I use raw files as examples, but in your
        case it might be the processing profiles, not the raw files. Or
        it might be JPEG files, PNG files, or any other file in the
        faulty dir. What we're going to do is to keep halving the pool
        of possibilities until we find the problem. This is the fastest
        way.
    2.  If RawTherapee is running, close it.
    3.  Move half of the files (`001.raw` - `050.raw`) from this
        problematic directory (`C:\photos\bugs`) back into a directory
        that RawTherapee reads (`C:\foo`)
    4.  Start RawTherapee.
    5.  If it crashed, go to the next step. If it did not crash, then go
        back to step 4.3, but move the other half (`051.raw` -
        `100.raw`).
    6.  Move half of the files you just moved (`001.raw` - `025.raw` or
        `051.raw` - `075.raw`) out from `C:\foo` and back into the
        directory which RawTherapee doesn't read (`C:\photos\bugs`).
    7.  Jump back to step 4.4. Repeat until you find the faulty file.

Zip this faulty file (even if it's a text PP3 file, because zipping it
will prevent any website from touching it and possibly removing the
cause of the crash \[it could be something you can't see\]), upload it
to [FileBin](http://filebin.net/) and link us to it in the
[Forum](http://rawtherapee.com/forum/).