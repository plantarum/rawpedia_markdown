## Benvingut

El RawTherapee és un programa de processament d'imatges en cru (raw)
multiplataforma, publicat sota una llicència GNU GPL v3. Va ser escrit
originalment per en Gábor Horváth de Budapest, i el desenvolupament es
va dur a terme durant el 2010 per un equip de gent d'arreu del món.
Enlloc de ser un editor de gràfics de trama com el Photoshop o el GIMP,
o un programa de gestió de recursos digitals com el digiKam, està
específicament enfocat en la postproducció de fotografies en cru (raw,
d'ara en endavant). I ho fa molt bé; com a mínim, el RawTherapee és un
dels programes de processament d'imatges raw més potent.

## Instal·lació del RawTherapee

Els usuaris poden baixar l'instal·lador del RawTherapee de
<http://rawtherapee.com/downloads> o del seu gestor de paquets. De totes
maneres també és possible compilar-se'l un mateix, si ho voleu o ho
necessiteu. A la [pàgina principal de la
RawPedia](Main_Page#Compiling "wikilink") trobareu enllaços a
instruccions de com fer-ho.

Hi ha disponibles moltes versions per baixar, i aquest paràgraf intenta
explicar la diferència entre elles a persones que no estan
familiaritzades en com funciona un sistema de versions
«rolling-release». Creem noves versions de «desenvolupament» gairebé
diariament, i un o dos cops l'any publiquem una nova versió «estable»,
que va molt ben empaquetada amb tots els errors importants coneguts
solucionats. Tots els errors que es trobin a la versió estable seran
subseqüentment solucionats a les noves versions de desenvolupament, i
s'aniran acumulant fins la següent publicació estable uns mesos després,
i així successivament. Aquestes versions de desenvolupament també són
les que s'utilitzen per millorar eines existents i afegir-ne de noves,
tot i que això requereix temps per polir-les i assegurar-se que
funcionin bé des d'un principi. Per una banda, les versions de
desenvolupament tenen el nombre més alt d'errors solucionats, però per
l'altra les noves eines d'aquestes versions poden funcionar malament o
no estar del tot polides i poden aparèixer nous errors. Si voleu provar
les noves funcions, opteu per l'última versió de desenvolupament;
obtindreu l'avantatge de tenir tots els últims errors solucionats i
podreu provar les noves eines i informar-nos de problemes i idees que
tingueu, amb el cost de descobrir nous errors. Per un ús general us
recomanem l'última versió estable que us donarà una experiència general
més polida.

## Inici del RawTherapee

![](Rt_setm_fb.png "Rt_setm_fb.png") El primer cop que inicieu el
RawTherapee veureu la [pestanya del navegador de
fitxers](The_File_Browser_Tab "wikilink"), i pot estar buida. Cal que
indiqueu al RawTherapee on estan les vostres fotos raw. Utilitzeu
l'arbre de directoris a l'esquerra de la pestanya del *Navegador de
fitxers* per trobar l'emmagatzematge de les vostres fotos raw i feu
doble clic a la carpeta per obrir-la. Després feu doble clic en una foto
raw per començar a editar-la.

## Edit your first image

Once you've opened a raw photo for editing, you will notice that the
preview does not look the same as your out-of-camera JPEG did. The
article "[Eek! My Raw Photo Looks Different than the Camera
JPEG](The_Image_Editor_Tab#Eek.21_My_Raw_Photo_Looks_Different_than_the_Camera_JPEG "wikilink")"
explains why.

Editing is done in the [Image Editor](The_Image_Editor_Tab "wikilink")
tab. This is where you work with RawTherapee to create stunning works of
art - or perhaps just apply first aid to your snapshots.
![](Rt_setm_editor.png "Rt_setm_editor.png") Take a moment to look
around this main Editor tab. Notice that there are tabs within this
tab - on the right of screen towards the top. These tabs and the
controls under them are the Toolbox. You probably have the first tab
open and, if you hover your mouse over it, you'll find that it's called
the Exposure tab. Below the choice of tabs are the tools the chosen tab
contains – Exposure, Shadows/Highlights, Tone Mapping etc. If you click
on one of them it will expand so that you can see its contents. Click
again and it will collapse. Right-click on one and that one will expand
while all others will collapse - a time-saving shortcut. To the left of
each tool's label is a power button which lets you turn it on or off, or
in some cases instead of a power button there is a triangular expander.
Read the [Tools section of the General Comments About Some Toolbox
Widgets](General_Comments_About_Some_Toolbox_Widgets#Tools "wikilink")
article for a detailed explanation. Browse through the tabs and panels
until you feel totally overwhelmed by all that's available.

Before you start working on an image, here is some important advice –
**Don't Panic!** You are in no danger of destroying any of your prized
images if you make a mistake. RawTherapee has some features which help
you protect your images:

- RawTherapee does non-destructive editing of your raw files. This means
  that RawTherapee will never, ever change the raw file itself. All
  changes are stored in sidecar files. You can find out more about them
  in the [Sidecar Files - Processing
  Profiles](Sidecar_Files_-_Processing_Profiles "wikilink") article.
- When using the Image Editor, you'll see the
  [History](The_Image_Editor_Tab#History "wikilink") panel on the left.
  This panel shows a history stack of every change you have made to your
  image. To go back to any step (including when the image was first
  loaded), just click on the relevant line in the History panel.
- Under the History panel you'll see a
  [Snapshots](The_Image_Editor_Tab#Snapshots "wikilink") panel. You can
  skip it for now, but you'll find it handy when you gain experience
  with RawTherapee. This panel stores the state of all the tools as a
  "snapshot". This allows you to easily, for example, tweak your photo
  to a nice and colorful look and take a snapshot, then tweak it again
  to a lovely black-and-white look and take a snapshot, and then compare
  the two just by clicking on either snapshot. (Note: RawTherapee does
  not save snapshots to the PP3 file yet, it will do so in the future.
  If you have three snapshots which you want to retain, you will need to
  click through them and save a PP3 file each time under a unique name).
- As you might expect, Control-z will undo the previous change. (OK,
  it's not rocket science but it's still handy!)

### Basics

1.  Start off by clicking on the
    ![<File:Colour.png>](Colour.png "File:Colour.png") Color tab and
    expanding the [White Balance](White_Balance "wikilink") tool by
    right-clicking on it. RawTherapee will start with the white balance
    used by your camera. Most white balance adjustments involve moving
    the Temperature and Tint sliders, or using the
    ![<File:Gtk-color-picker.png>](Gtk-color-picker.png "File:Gtk-color-picker.png")
    Spot White-Balance Picker on a colorless (neutral gray) patch.
    Adjust to taste.
2.  Next, fix the exposure by going to the
    ![<File:Exposure.png>](Exposure.png "File:Exposure.png") Exposure
    tab, expanding the [Exposure](Exposure "wikilink") tool and
    adjusting it to taste. For now, just use the Exposure Compensation
    and Saturation sliders.
3.  If your image is noisy, switch to the
    ![<File:Detail.png>](Detail.png "File:Detail.png") Detail tab, zoom
    to 100% either using the
    ![<File:Gtk-zoom-100.png>](Gtk-zoom-100.png "File:Gtk-zoom-100.png")
    button or using the "z" keyboard shortcut key, because the effects
    of the tools in this tab are only visible in the zoomed-to-100%
    preview (and of course in the saved image), and enable the [Noise
    Reduction](Noise_Reduction "wikilink") tool using the default
    settings for now. RawTherapee has automatically removed color
    (chrominance) noise. Luminance noise is removed
    [manually](Noise_Reduction#Usage "wikilink"), though leave it for
    now as luminance noise generally lends a pleasing, grainy, film-like
    look. As a general rule, when using noise reduction don't use
    sharpening. Zoom back out to see the whole image either using the
    ![<File:Gtk-zoom-fit.png>](Gtk-zoom-fit.png "File:Gtk-zoom-fit.png")
    button or using the "f" keyboard shortcut key.
4.  Now you decided you want to fix the
    [geometry](Lens/Geometry "wikilink") and composition of your photo.
    - First make the horizon level, or correct the things which should
      be vertical such as street lamps or building edges. To easily do
      this, press the "s" key on your keyboard (the same as clicking the
      ![<File:Straighten.png>](Straighten.png "File:Straighten.png")
      button), and click-and-drag a line along the horizon or along the
      edge of a building over the preview. Your image will rotate
      accordingly and you will automatically be taken into the
      ![<File:Transform.png>](Transform.png "File:Transform.png")
      Transform tab.
    - To crop the photo, press the "c" shortcut key on your keyboard (or
      use the ![<File:Crop.png>](Crop.png "File:Crop.png") button) and
      click-and-drag a crop over the preview; you will notice that the
      [Crop](Crop "wikilink") tool becomes automatically enabled. There
      is no need to "apply" a crop - it takes effect the moment you draw
      it. You may want to set the Crop "Guide type" to "none" if it's a
      problem.
    - Finally, you want to downscale the photo, because who wants to
      upload a 10MB JPEG to your social network. Enable the
      [Resize](Resize "wikilink") tool and leave it at the default
      settings. Notice that the resizing effect is only applied to the
      saved image, not to the preview.
5.  You're all set, let's [save](Saving "wikilink") it straight away.
    Click the
    ![<File:Gtk-save-large.png>](Gtk-save-large.png "File:Gtk-save-large.png")
    Save Current Image button, or use the keyboard shortcut Ctrl+s. Save
    it as a JPG file, quality at "92", subsampling at "balanced". These
    are good all-round settings. Choose a folder where you want it saved
    to, and after a few seconds your file will be ready in the folder
    you selected. If you close RawTherapee, the settings you used will
    be stored in a [PP3 sidecar
    file](Sidecar_Files_-_Processing_Profiles "wikilink") next to the
    raw file, so that you can re-open the raw photo in the future and
    retain the tool settings you used.

Now that you went through basic photo adjustment and are familiar with
the steps, let's recap the steps but with more advanced details.

### Advanced

Always read each tool's article here on RawPedia before using it, to get
a firm understanding of what it does. The articles explain how the tools
work in RawTherapee, while the general concepts unspecific to
RawTherapee are left to the user to find on Wikipedia or elsewhere.

Be sure to see the [Keyboard Shortcuts](Keyboard_Shortcuts "wikilink").

The order of the tools inside RawTherapee's engine pipeline is
hard-coded, so from that point of view it does not matter when you
enable or disable a tool. However some tools can make a large impact on
other tools, e.g. changing exposure may require you to re-adjust color
toning, and some tools may require plenty of CPU power to calculate the
preview making updates of the preview from then on slow, so it is for
this reason we suggest you stick to this general order of operations:

1.  Start off by making sure that RawTherapee's environment is set up
    correctly, meaning:
    - Make sure that RawTherapee is using your monitor's color profile
      if you use a color-managed workflow. Check Preferences \> Color
      Management. You may also need to load the appropriate calibration
      curves into your graphics card if you built your monitor color
      profile on top of them, though how you do that is outside the
      scope of RawTherapee.
    - Make sure that the Color Management tool is configured correctly.
      Usually the defaults are best. Read the [Color
      Management](Color_Management "wikilink") and [Color Management
      addon](Color_Management_addon "wikilink") articles. If instead of
      using the color matrix or DCP or ICC profiles shipped with
      RawTherapee you decide to use an external one, for example a
      self-made DCP or one from Adobe, load it as the first thing you
      do, otherwise you may need to re-adjust some of the color tools.
      Always use an output profile - in most cases the default one,
      RT_sRGB. If you think you're being smart by selecting "No ICM:
      sRGB Output", you're mistaken.
2.  If you want to use a [Flat-Field](Flat_Field "wikilink") and/or
    [Dark-Frame](Dark_Frame "wikilink") image, do so now, to avoid
    re-adjustment.
3.  Now set the correct [White Balance](White_Balance "wikilink"). You
    may fix the exposure first if the image is too dark (or too bright)
    to see white balance changes.
4.  Next, adjust the [Exposure](Exposure "wikilink"), using the Exposure
    Compensation and Black sliders to get the image into the right
    ballpark. Once in the right ballpark, continue with using both tone
    curves. Be sure to read the [Tone Curve
    section](Exposure#Tone_Curves "wikilink") in the Exposure article to
    learn why there are two of them and how best to use them - they are
    a very powerful tool!
5.  In the Basics section above we suggested that you use the
    [Saturation](Exposure#Saturation "wikilink") slider (in the Exposure
    tool). Now that you've learned the basics and are exploring more
    advanced techniques, we suggest you not use the Saturation slider
    anymore, and instead use the more powerful [CC
    curve](Lab_Adjustments#CC_Curve "wikilink") in the [Lab
    Adjustments](Lab_Adjustments "wikilink") tool, as it gives you finer
    control.
6.  The order of the rest gets fuzzy. Some tools will unavoidably
    influence others. Carry on with the [Lab
    Adjustments](Lab_Adjustments "wikilink") tool and then the rest of
    the tools in the Exposure tab.
7.  Then use the [Wavelet](Wavelet "wikilink") tool in the
    ![<File:wavelet.png>](wavelet.png "File:wavelet.png") Wavelet tab.
8.  Then use the tools in the
    ![<File:Colour.png>](Colour.png "File:Colour.png") Color tab. The
    [Color Toning](Color_Toning "wikilink") tool specifically is very
    sensitive to exposure changes, so leave it for last.
9.  Then zoom to 100% and use the tools in the
    ![<File:Detail.png>](Detail.png "File:Detail.png") Detail tab.
    Generally, don't sharpen if you're using noise reduction.
10. Finally, zoom out again and use the tools in the
    ![<File:Transform.png>](Transform.png "File:Transform.png")
    Transform tab. The reason you left these for last is that they may
    make the preview image appear blurry, because in order for the
    preview to be responsive, RawTherapee uses that very preview image
    you see at the very resolution you see - small - to show what the
    tools do, and when you rotate or otherwise change the geometry of a
    small image, there is a clear softening. This is not a problem when
    saving as by that point RawTherapee does its processing on the
    full-sized image, which is slow but of high quality.
11. Save, either directly when you want to save a single photo, or via
    the [Batch Queue](The_Batch_Queue "wikilink") when you want to
    process many photos.

You can edit metadata in the
![<File:Meta.png>](Meta.png "File:Meta.png") Meta tab at any time. For
the changes you make in the Meta tab to take effect in the saved image,
make sure "Preferences \> Image Processing \> Copy Exif/IPTC/XMP
unchanged to output file" is unchecked. If it is checked, the changes
you make in the Meta tab will be ignored in the saved image.