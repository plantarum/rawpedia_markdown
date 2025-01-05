Sometimes a single, "static" default processing profile is not enough to
cover all use cases. For example, the amount of noise reduction to apply
varies according to the Camera and ISO setting used. Another example is
the kind and amount of lens corrections needed, which is obviously
dependent on the lens used.

In order to handle such cases, RawTherapee provides a feature that
allows to create a default processing profile "dynamically", based on
the metadata of the image being processed (such as camera and lens name,
shutter speed, ISO value, and so on).

This is done by defining a set of "Dynamic profile rules". Each rule has
a (partial) processing profile attached to it, plus some conditions on
the image metadata that define whether the rule is applicable. When a
picture is edited for the first time, the list of rules is scanned, and
all the profiles that match are combined (in the order given, so later
rules can override earlier ones) to build the initial processing
profile.

In order to activate the functionality, the default processing profile
(in Preferences -\> Image Processing) must be set to "(Dynamic)". Rules
are defined in the "Dynamic Profile Rules" section of the preferences
window.

A screenshot is shown below.

<figure>
<img src="dynamic-profile-rules-screenshot.png"
title="File:dynamic-profile-rules-screenshot.png" />
<figcaption><a
href="File:dynamic-profile-rules-screenshot.png">File:dynamic-profile-rules-screenshot.png</a></figcaption>
</figure>