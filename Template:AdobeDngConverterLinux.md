1.  Install [Wine](http://www.winehq.org/), preferably using your
    package manager.
2.  [Download Adobe DNG Converter for
    Windows](http://supportdownloads.adobe.com/product.jsp?product=106&platform=Windows).
3.  Install Adobe DNG Converter:

        WINEPREFIX="$HOME/wine-dng" wine /path/to/DNGConverter_version.exe

    It will install to
    `"$HOME/wine-dng/drive_c/Program Files (x86)/Adobe/Adobe DNG Converter.exe"`
4.  Run Adobe DNG Converter:

        WINEPREFIX="$HOME/wine-dng" wine "$HOME/wine-dng/drive_c/Program Files (x86)/Adobe/Adobe DNG Converter.exe"
5.  Add an alias so that you can run Adobe DNG Converter from a console
    with ease:

        echo "alias dng='WINEPREFIX=\"\$HOME/wine-dng\" wine \"\$HOME/wine-dng/drive_c/Program Files (x86)/Adobe/Adobe DNG Converter.exe\"'" >> ~/.bashrc && exec bash
6.  To run Adobe DNG Converter, just type `dng` in a console.