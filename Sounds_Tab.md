The "Sounds" tab lets you set an audible notification when a lengthy
operation ends. It is currently only supported on Windows and Linux.

The "Queue processing done" sound is played after the last
[Queue](The_Batch_Queue "wikilink") image finishes processing. The
"Editor processing done" sound is played after a lengthy
in-[editor](The_Image_Editor_Tab "wikilink") operation that took longer
than the specified number of seconds is complete.

Sounds can be muted either by disabling the "Enabled" checkbox or by
setting fields with sound file references to blank values.

The "Queue" and "Editor processing done" text boxes can either point to
wave (.wav) files, or can specify one of the following values:

Windows:

- SystemAsterisk
- SystemDefault
- SystemExclamation
- SystemExit
- SystemHand
- SystemQuestion
- SystemStart
- SystemWelcome

Linux

- bell
- camera-shutter
- complete
- dialog-warning
- dialog-information
- message
- service-login
- service-logout
- suspend-error
- trash-empty
- possibly the name of any file in
  `/usr/share/sounds/freedesktop/stereo/`