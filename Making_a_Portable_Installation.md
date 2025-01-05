RawTherapee and the cache folder can be stored "self-contained" on a USB
flash drive or any other mass-storage device.

## For Windows

Get the latest build of RawTherapee. Since we want it portable, we don't
want the installer, just the bare, zipped program. If the latest version
on our website is in simple zipped form without an installer, you can
skip this step. However, if it is an installer, you need to first
extract the RawTherapee files.

- If it is an Inno Setup installer (.exe extension, all recent Windows
  installers are Inno Setup ones at the time of writing, summer 2014),
  get [innounp](http://innounp.sourceforge.net/) or
  [innoextract](http://constexpr.org/innoextract/) to unpack it.
- If it is an MSI installer (no recent Windows builds use this at the
  time of writing), fire up a command prompt and type:

      msiexec /a '''RawTherapee.msi''' TARGETDIR="'''C:\TargetDir'''" /qb

  Replace the name of the MSI installer and the target directory as
  appropriate. Spaces in the TargetDir path are allowed, as the path is
  enclosed in quotes.

Let's assume that you've unzipped your archive into **E:\RawTherapee**,
where **E:\\** is the drive letter of your USB flash drive. Now open the
**E:\RawTherapee\options** file, and set the **MultiUser** option to
**false**. That way, the cache directory will be located in a
subdirectory of the installation path.

## For Linux

Getting RawTherapee to run off a portable medium such as a USB flash
drive on various Linux systems is not straightforward due to the nature
of Linux systems. While the Windows version of RawTherapee comes bundled
with all required libraries to run on any Windows version, Linux
distributions differ significantly from each other and as a result a
version of RawTherapee built for one distribution is unlikely to run
under a different distribution. Though it's unlikely that you can have a
portable binary that runs from a USB stick on any distribution, what you
can do is keep your configuration files portable, and then install
RawTherapee on your target machine using that distribution's package
manager, as builds of RawTherapee are available for most distributions.
You could also put it on a live USB image, if you're ambihaxtrous :\]

In order to backup your configuration you will want to copy
RawTherapee's *config* folder onto your USB stick. Specifically, you
want the "*options*" file, your custom "*camconst.json*" if you made
one, and any custom PP3, ICC, DCP and LCP profiles. The [File
Paths](File_Paths "wikilink") article describes where to find these.