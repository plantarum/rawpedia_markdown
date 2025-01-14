Processing profiles ([sidecar
files](https://en.wikipedia.org/wiki/Sidecar_file) with a PP3 extension
for version 3, or PP2 for the older version 2) are text files which
contain all of the tools and their settings that RawTherapee will apply
to an image. Processing profiles come from two quite different sources,
though they work in exactly the same way:

- Bundled profiles come with RawTherapee. Their purpose is to give you a
  good starting point when you first open an image for editing. They are
  the ones you see in the [Processing Profile
  Selector](The_Image_Editor_Tab#Processing_Profile_Selector "wikilink")
  drop-down list in the [Image Editor](The_Image_Editor_Tab "wikilink").
  If you are familiar with other raw processors, you may know their
  equivalent as "presets".
- Whenever you edit an image, the tool settings you want applied to that
  image are stored in a processing profile that is particular to that
  image (ranking information, the history panel contents and snapshots
  are not stored in these files yet, see [issue
  473](https://code.google.com/p/rawtherapee/issues/detail?id=473)). The
  rest of this section deals with this type of processing profile though
  many of the comments also apply to the first.

By default, the processing profile for an image is stored alongside the
input image (if you open "*kitty.raw*", a new file "*kitty.raw.pp3*"
will be created next to it), but they can also be stored in a [central
cache](File_Paths "wikilink"). You can choose whether RawTherapee should
use the cache, write the processing profile alongside the image, or
both, from "*Preferences \> Image Processing*". We suggest you store
these files alongside your input image files so that if you decide to
move the images you can move the processing profiles easily along with
them.

Processing profiles evolve from one version of RawTherapee to the next.
We strive to ensure backward compatibility, but this is not always
possible. Processing profiles can gain new parameters or lose the ones
that became obsolete. Tool behavior can also evolve, wherein default
values change or in extreme cases the meaning of a value is interpreted
differently; an example of this is the noise reduction tool, where a
luminance noise reduction value of 10 in RawTherapee-3.0 would lead to a
different result in RawTherapee-4.0.10 where the whole noise reduction
engine has been greatly improved.

Consolidating processing profiles into a cache allows one to store
isolated copies of the processing profiles per specific version of
RawTherapee. In such a case, the cache can be used to re-process photos
in order to get the same output as originally intended (but e.g. with a
new size or output color space) using the same version of RawTherapee in
which the image was originally edited. Whether this is desirable is
debatable. Consider that you want to squeeze as much out of your raw
files as possible. If a year later you want to go back to an old raw
file, perhaps getting the same result as you did a year ago is not the
best idea, because RawTherapee's capabilities would have greatly
improved in that year, and your taste and skill would also have evolved.
Nevertheless, by backing up whole cache directories when installing a
new version of RawTherapee you retain the option of going back to an
older version of RawTherapee in order to get the exact same result.

The [File Paths](File_Paths "wikilink") article describes where you can
find the "*cache*" and "*config*" folders on your system.

When releasing a major new version of RawTherapee, it may happen that we
use a new suffix for the "*cache*" and "*config*" folders. This means
that the new version of RawTherapee will not see your old configuration
or processing profiles. Though this sounds undesirable, there are good
reasons we may (rarely) choose to do that.

- Backward-compatibility. There may be changes in behavior between old
  and new versions of a specific tool. For instance, the effects of the
  Auto Levels tool have changed (for the better) between versions 4.0.11
  and 4.0.12, so if your old processing profiles had it enabled, the
  results in 4.0.12 will be a little different and may require tuning
  your old profiles. We tried to preserve backwards-compatibility where
  possible, but it was not possible to do that everywhere. This should
  not be a problem, because should you require an identical result you
  can simply keep using the old version of RawTherapee and use the new
  one for future work, and, more importantly, your skills and taste have
  evolved over time, so why would you want the exact same results you
  had years ago when you can do better now?
- Some users have not checked "[Preferences](Preferences "wikilink")" in
  a long time, and their program is tuned for what worked best long ago,
  not for what works best now. Our defaults are good ones, we keep them
  up to date to make RawTherapee look and function well out-of-the-box,
  so sometimes having RawTherapee start with fresh defaults is a good
  thing, and it will motivate users to look into
  "[Preferences](Preferences "wikilink")" again.
- Some users have never looked inside
  "[Preferences](Preferences "wikilink")" in the first place, and are
  unaware of some of the features that can be unlocked there. As above,
  fresh defaults will activate these things.
- Some old cache and config files can cause RawTherapee to crash. While
  we patch the specific cases made known to us, it is safe to assume
  there will always be cases unknown to us which will still cause
  instability. Starting with clean cache and config folders mitigates
  this problem.

Do note that if you process thousands of photos, this cache can grow
quite large and possibly slow down RT loading times, so this is another
argument for choosing "*Save processing profile next to the input file*"
over "*Save processing profile to the cache*". If you do use the cache,
keep an eye on it's size after a few months.