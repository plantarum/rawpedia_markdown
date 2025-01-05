## Stable Releases

## Development Builds

Development builds can be downloaded from the
[nightly](https://github.com/Beep6581/RawTherapee/releases/tag/nightly)
release on GitHub.

How do development builds compare to stable builds? We make new
"development" builds almost daily, and every few months we release a new
"stable" version, which is nicely packaged with all known important bugs
fixed. Any bugs found in the latest stable version will be subsequently
fixed in the newer development versions, and these will accumulate until
the next stable release several months later, and so on. These
development versions are also where we improve existing tools and add
new ones, though it takes time to polish them and to make sure they work
well out of the box. On the one hand, development versions always have
the highest number of bugs fixed, but on the other hand the new tools in
these versions may be rough and unpolished and new bugs will appear. If
you want to try out new features then get the latest development build -
you get to take advantage of all the latest bug fixes and you get to
test new tools and report problems and ideas back to us at the cost of
discovering new bugs. For general use we recommend the latest stable
release which gives you a generally more polished experience.

How do you read and make sense of the development builds' names? The
filename has roughly this structure:
`RawTherapee_branch_tag_commit_date.extension`
\* Code changes happen several times a day, and each code change is
referenced by a unique hash number in the commit - it looks like this:
`d9ad93c15`.

- Each commit happens on a "branch". The main branch is called `dev`.
  New features are developed on their own branches, and then merged into
  `dev` when ready.
- The "tag" is the human-friendly version of the latest release, e.g.
  `5.7`.