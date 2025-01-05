1.  Tea
2.  Pull and update
3.  Run:
        ./tools/generateTranslationDiffs

    Perform final language file updates, remember to replace ampersands
    and other special HTML chars with HTML character entities where
    needed (not everywhere! always refer to "*default*"), make locale
    versions of translations (currently "*English (UK)*" and "*Polish
    (Latin Characters)*" files are generated automatically by
    *generateTranslationDiffs*). If you made any changes, re-run the
    script.
4.  Run:
        dos2unix rtdata/languages/* and rtdata/profiles/*
5.  Commit language files, profiles, and a new splash screen if needed.
6.  Update the changelog (replace "*4.1*" with whatever the latest tag
    currently is in "*reverse(4.1::tip)*"):
        printf "%-12s\t" "  DATE" "| CHANGESET" "| COMMITTER"; printf "%s\n" "" "  --------------|---------------|-------------------------------------"; hg log --template '> {date|shortdate}\t| {node|short}\t| {author|person}\n  {desc|fill68}\n\n' -b default -r "reverse(4.0.12::tip)" | sed -e 's/^[^> ]/  &/' -e 's/[ ]\{0,1\}<natureh.510>//g; s/natureh.510/Hombre/g; s/natureh/Hombre/g; s/michael/Michael Ezra/g; s/dualon/Dualon/g; s/entertheyoni/DrSlony/g; s/ejmartin/Emil Martinec/g; s/wyatt/TheBigOne/g; s/google/thebluelabel/g; s/ghorvath/Gabor Horvath/g; s/ffsup2/Joker/g; s/jdc$/Jacques Desmis/g; s/jdesmis/Jacques Desmis/g; s/torger/Torger/g'
7.  Update RELEASE_NOTES.txt, merge the changelog into it. To find new
    features from the changelog more easily, use:
        hg log --template '- {desc}\n' -b default -r "reverse(4.0.11::4.0.12)"
8.  Tag the new release:
        hg tag 4.1
9.  Push the tag:
        hg push
10. Make a source tarball and upload it to the website. Running
    *generateSourceTarball* is the preferred method because it results
    in a tarball with metadata:
        ./tools/generateSourceTarball 4.1

    If you need to make a tarball manually, use this, but beware some
    metadata (AboutThisBuild) will be missing:

        tag="4.1"; time { hg archive --time -r ${tag} rawtherapee-${tag}.tar -X ".hg*" && xz -z -9e -T 8 rawtherapee-${tag}.tar; } && ll rawtherapee-*