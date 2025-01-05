Bugs must be reported in our [RawTherapee GitHub issue
tracker](https://github.com/Beep6581/RawTherapee), not in the forum and
not in IRC.

We use the term "bug report" in the broadest sense - any issue you have
must include the information detailed below.

## Requirements of a good bug report

You must always provide the following information:

- **Complete version information** of the RawTherapee build you're using
  (e.g. "RawTherapee 4.2.678 gtk3"). RawTherapee version information is
  available by clicking on
  "*[image:Gtk-preferences.png](image:Gtk-preferences.png "wikilink")
  Preferences \> About \> Version*" - in most cases that tab will be
  full of information, all of which you should copy and paste into your
  bug report. If that tab is empty, then you can get the RawTherapee
  version from the RawTherapee window's titlebar.
- System information: your operating system name and version, your CPU
  type and speed, and how much RAM you have. Windows users can find this
  information by pressing the + keyboard shortcut.
- Tell us where you downloaded the RawTherapee build from. Be specific,
  don't just say "your website"; provide the URL if you can by
  right-clicking on the link which downloads the build and selecting
  "copy address" or something similar to that, depending on your web
  browser.
- Explain the **exact steps** to reproduce the problem. Apply the
  "Neutral" processing profile to your photo and then explain what needs
  to be done to trigger the problem from there.
- **Make your raw file and PP3 file available to us** by uploading them
  to a file sharing service such as
  [www.filebin.net](http://filebin.net/) if your bug involves a
  particular raw file, a particular setting, or lack of support for your
  raw file..
- **Show a screenshot of the problem**, you can upload them to
  [www.imgur.com](http://www.imgur.com)
- **Search the forum and our issue tracker before filing a new report**
  as chances are that someone has already reported the problem before
  you, and duplication wastes time.
- Make sure you **use the latest version of RawTherapee** as it's likely
  that a bug in an old version has been fixed in the latest one.
- If your issue involves a crash, provide a stack backtrace if you can.
  How to get one is explained below. If you're not capable of getting
  one, then make sure you have at least provided the information above,
  otherwise your bug report is useless.

For more information on how to report bugs, read this:
<http://www.chiark.greenend.org.uk/~sgtatham/bugs.html>

## When RawTherapee crashes - An introduction to stack backtraces

A stack backtrace is a log of the steps a program took up to a point in
time. For our needs, that point will be the crashing of RawTherapee, and
we will use it for debugging RawTherapee, to fix the crash. We release
builds of RawTherapee which are stable for us. If they crash for you,
then you need to supply us with useful information so that we can either
reproduce the crash ourselves, or fix the bug without being able to
reproduce the crash. The stack backtrace is extremely useful.

Programs need to be compiled to run, and generally speaking they can be
compiled in one of two ways:

- The "release" way, which optimized the program for speed but doesn't
  offer any useful information if it crashes,
- The "debug" way, which provides plenty of useful information when it
  crashes but runs considerably more slowly.

While it is possible to get some information out of a *release* build,
the information is far more precise if you use a *debug* one. You will
find both "release" and "debug" builds of RawTherapee on the [official
downloads page](http://rawtherapee.com/downloads) as well as in [the
forum](https://discuss.pixls.us/c/software/rawtherapee). For day-to-day
use, use a release type build because it runs much faster. If you
encounter a crash, use a debug type build to provide us with useful
information so that we can fix the crash.

### How can you tell whether a build has debug flags or not?

Two ways:

- In the download section of our website, click on the *Details* button
  of one of the builds and look for *Build Type:*. If the word *release*
  follows, then its a build optimized for speed without any debug flags.
  If the word *debug* follows, then it is a build with debug flags,
  which is what you need to download and use to get a meaningful stack
  backtrace. You might also find a debug version of rawtherapee.exe
  available in the [forum](http://rawtherapee.com/forum) but it has to
  match the version of the rawtherapee.exe you're replacing.
- Fire up RawTherapee, click on *Preferences*, then *About* and
  *Version*, and look for *Build type:* as above. If *release* follows
  then it has no debug flags, if *debug* follows then it has debug flags
  which is what you need.

### How to get a debug version?

Check [our download page](http://rawtherapee.com/downloads) or your
package manager for a *debug* build of the latest version of
RawTherapee. If there is none, then either ask us for one, or make one
yourself. If you use Linux, making one is very easy, just follow the
[Compiling in Linux](Linux "wikilink") guide.

Software can (and often does) behave differently running under a
debugger than it normally would, due to the inevitable changes the
presence of a debugger will make to a program's internal timing. This
means that you might encounter bugs (crashes) during your day-to-day use
which will not occur when you run RawTherapee from GDB (GDB is the
debugger)! This is an unfortunate fact, but luckily it's a rare one, so
go ahead, get a debug build, and try to reproduce the crash, this time
getting a juicy stack backtrace.

**ALWAYS** download and try the latest version of RawTherapee before
reporting a bug! Reporting based on an old version is a waste of time.

## Step by step

1.  Get GDB. How you do this will depend on your operating
    system/distribution.
    - **Linux** - Use your package manager.

      In Ubuntu you would open a terminal and write:

          sudo apt-get install gdb

      In Gentoo you would write:

          sudo emerge gdb
    - **Windows** - Our debug Windows builds usually include `gdb.exe`,
      so you don't need to do anything to get it. If they don't, install
      [TDM-GCC](http://tdm-gcc.tdragon.net/) making sure to install the
      GDB package as well. Copy the `gdb.exe` to your RawTherapee
      directory, so it sits alongside `rawtherapee.exe`
    - **Mac OS X** - if you know how to install GDB under OS X, please
      help write this section.
2.  Run RawTherapee from within GDB.
    - In **Linux**, assuming you used [compiled RawTherapee
      yourself](Linux#Compiling:_The_Manual_Way "wikilink"), open up a
      terminal and, assuming your debug build was compiled to
      `~/rt_debug/` then type:
          gdb ~/rt_debug/rawtherapee
    - In **Windows**, open up the command prompt, navigate to your
      RawTherapee directory and assuming that the filename of the
      RawTherapee debug executable is `rawtherapee-DEBUG.exe` then type:
          gdb rawtherapee-DEBUG.exe
3.  GDB starts up and is ready to run RawTherapee. To run it, type:

        r
4.  RawTherapee runs, and you will notice a flood of information in GDB.
    Most of it will look like this:

    `[New Thread 0x7fffa7b2e700 (LWP 11532)]`

    `[New Thread 0x7fffa9b32700 (LWP 11533)]`

    `[Thread 0x7fffaab34700 (LWP 11528) exited]`

    `[Thread 0x7fff97dfd700 (LWP 11507) exited]`

    Do what you did to trigger the crash, and when RawTherapee does
    crash, its window will just freeze, it won't close. You can tell
    that it crashed by the fact that everything in that window will have
    stopped responding. Alt+Tab back to the GDB terminal window.
5.  We want a detailed stack backtrace, and to make sending it to us
    easier in the next three commands you will tell GDB to save it to a
    text file called `log.txt` (or anything, the name doesn't matter).
    Type:

        set pagination off

        set logging file log.txt

        set logging on
6.  Now to have GDB print the actual stack backtrace, type:

        thread apply all bt full

    You should see a screen full of text, numbers, code and magical
    spells. These were automatically saved to the `log.txt` file.
7.  You may now quit GDB. To do so, type:

        q

    and confirm it with a

        y
8.  Now it is time to send us the bug report. Open a new issue in our
    [GitHub bug
    tracker](https://github.com/Beep6581/RawTherapee/issues/new),
    explain the steps you performed which lead to the crash, **attach
    the `log.txt` file**, and provide all the information we asked for
    above.

Nicely formatted text is easier to read. If you are pasting code into
GitHub, use backticks or indent the code - read [the
guide](https://guides.github.com/features/mastering-markdown/). If you
want to paste code into the
[forum](https://discuss.pixls.us/c/software/rawtherapee), you can also
use backticks or indent the code - read [the Forum code formatting
guide](Forum "wikilink").

Remember to include the contents of
"*[image:Gtk-preferences.png](image:Gtk-preferences.png "wikilink")
Preferences \> About \> Version*", a sample raw and PP3 file, along with
full version information of your operating system, your CPU type and
speed, and how much RAM you have, what you had for lunch, etc.