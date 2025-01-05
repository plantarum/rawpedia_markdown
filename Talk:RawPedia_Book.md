This is a first stab at manually organizing content for a printable
book.

I'm doing it this way because then we can use a headless Chrom(e\|ium)
to fetch a single page and print to PDF automatically.

I'm doing it on my side with:

    chromium-browser --headless -disable-gpu --print-to-pdf="/home/pat/Documents/RawPedia.pdf" 'http://rawpedia.rawtherapee.com/index.php?title=Rawpedia_Book&printable=yes'

I'll then scp this file up to the base of rawpedia:
<https://rawpedia.rawtherapee.com/RawPedia.pdf>