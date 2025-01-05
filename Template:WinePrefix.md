When you run Wine it will create a basic Windows system by default in
`$HOME/.wine`. That is called a "Wine prefix". While it's fine to leave
it like that, you can run each Windows program in its own Wine prefix,
so that you can easily and cleanly remove all traces of one program
without affecting the others. For example you might keep Adobe DNG
Converter in its own Wine prefix in `$HOME/wine-dng` and decide to try
out some proprietary Windows HDR program. You might find out that you
don't like this program, or that the trial period has expired, or that
it simply doesn't work. Uninstalling it, if the uninstaller even works,
is known to leave things behind. If, on the other hand, you installed
this program to its own Wine prefix, say `$HOME/wine-hdr`, you could
simply delete that folder and that program would be gone without a
trace, without affecting Adobe DNG Converter. Creating a new Wine prefix
is very simple. All you have to do is to prepend
`WINEPREFIX=$HOME/some-folder` before the "`wine`" command. If that
folder does not exist, Wine will create it for you.