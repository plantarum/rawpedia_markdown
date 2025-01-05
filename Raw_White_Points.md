It is unlikely you will ever need to use the Raw White Points tool other
than for diagnostic purposes.

The white-point correction adjuster scales the current white level for
all channels. It scales the raw samples linearly after black-level
subtraction and can be used to simulate a new white level. This can be
necessary if RawTherapee's raw decoder has an incorrect white level,
which can happen for new or rare cameras. [Flat
Field](Flat_Field "wikilink") correction may also, in some cases, as a
side-effect, scale down raw samples such that blown highlights become
discolored (usually magenta/pink); in this case this setting can be used
to scale up the raw data so it hits the white level again.