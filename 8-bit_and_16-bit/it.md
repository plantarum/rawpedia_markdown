"8 bit" quando si riferisce a formati di immagine in genere significa
che il programma assegna 8 [bit](https://en.wikipedia.org/wiki/Bit)
(otto valori "1" o "0", che insieme fanno uno \[https :
//en.wikipedia.org/wiki/Byte byte\], in grado di rappresentare un valore
[integer](https://en.wikipedia.org/wiki/Integer) da 0 \[00000000 a 255
\[11111111\]) a ciascun pixel del canalo colore, e ogni pixel nei files
di RawTherapee ha tre canali di colore - rosso, verde e blu.

Le più moderne fotocamere [DSLR](https://en.wikipedia.org/wiki/DSLR)
utilizzano convertitori analogici/digitali a 12 o 14 bit per registrare
i dati del sensore. Ciò significa che quando si sceglie un formato di
uscita a 8 bit per canale nella fotocamera, come JPEG, si perde alcune
informazioni. Non è così semplice come potrebbe sembrare però, le
fotocamere registrano i dati in modo lineare (a causa di limitazioni nel
disegno hardware) mentre i file JPEG, TIFF e PNG [gamma
encode](https://en.wikipedia.org/wiki/Gamma_correction) conengono più
valori nell'ambito dell'ombra e meno nelle luci in modo da corrispondere
meglio alla sensibilità dell'occhio. Ciò significa che un JPEG a 8 bit
può visualizzare come log2 ((1/2 ^ 8) ^ 2.2) = 17.6 stop di gamma
dinamica che in realtà supera i 14 stop delle migliori fotocamere
correnti, e questo spiega perché a volte si può vedere del rumore
nell'ombra della fotocamera anche in un JPEG a 8 bit. Tuttavia a causa
dei minori valori nelle alte luci, perde in precisione rispetto alla
fotocamera. Praticamente questo non è un problema quando il file di
output è quello definitivo e non verrà più elaborato, tuttavia una foto
può essere notevolmente migliorata quando viene salvata come raw e
elaborata utilizzando un programma di elaborazione raw, proprio come il
tuo - RawTherapee.

Una volta che hai elaborato una foto in RawTherapee, ti trovi di fronte
alla stessa scelta: salvare l'immagine con una risoluzione a 8 bit per
canale o 16 bit per canale (solo [1](https://en.wikipedia.org/wiki) /
TIFF TIFF\] e
[PNG](https://en.wikipedia.org/wiki/Portable_Network_Graphics), non
[JPEG](https://en.wikipedia.org/wiki/JPEG)). Se si desidera
post-elaborare le tue foto dopo RawTherapee in un programma di editing
di immagini in formato 16 bit, è meglio salvare in un formato a 16 bit
lossless. TIFF non compresso è suggerito come formato intermedio, in
quanto è facile salvare e memorizzare tutti i metadati
([Exif](https://en.wikipedia.org/wiki/Exif), [/
IPTC_Information_Interchange_Model IPTC](https://en.wikipedia.org/wiki),
[XMP](https://en.wikipedia.org/wiki/Extensible_Metadata_Platform)) del
file originale (PNG in genere scarta metadati!).

C'è qualche confusione per la denominazione di file da 8, 16, 24 e 32
bit. Ecco un chiarimento, ma diventa confuso, quindi metti il tuo casco.
In realtà non è necessario leggere questo per utilizzare RawTherapee, è
solo conoscenza di fondo. Ognuno dei canali rossi, verdi e blu
memorizzati in un file JPEG, PNG o TIFF è in realtà un'immagine
incolore, ma quando combinate queste tre immagini incolori, si ottiene
un'immagine a colori. Così come funziona ogni rappresentazione digitale
delle immagini - le immagini a colori vengono sempre decomposte nei loro
componenti in un modo o nell'altro. Tra i formati di file che
RawTherapee può salvare (JPG, PNG e TIFF), ogni pixel contiene
informazioni per tre canali colore - rosso, verde e blu. Diciamo "8 bit
per canale" per rendere chiaro che questi 8 bit si applicano solo a un
canale a colori. Il motivo è che si potrebbero verificare riferimenti a
"immagini a 8 bit" e qui si confonde perché la persona che ha scritto
potrebbe riferirsi a un formato in scala di grigi che memorizza solo un
canale o un formato di colore che memorizza tre canali, con precisione a
8 bit ciascuno. Un'altra notazione per le stesse immagini "8 bit" che
RawTherapee salva è "24 bit". Che confusione. O è così? Ogni pixel è
composto da 3 canali e ogni canale memorizza 8 bit di dati, per cui
abbiamo complessivamente 24 bit di dati per pixel. La situazione
peggiora. I programmi di editing di immagini possono anche memorizzare
un quarto canale, chiamato "alpha". Per dirla semplicemente, alpha
descrive come è trasparente un pixel. Questi canali alfa hanno anche una
"risoluzione a colori" di 8 bit. Sia i file PNG che TIFF possono gestire
alfa, mentre JPEG non può. Se si dispone di un'immagine a 8 bit per
canale con un canale alfa, può anche essere descritta come un'immagine a
32 bit; R (8) + G (8) + B (8) + alpha (8) = 32. Il problema ultimo è che
puoi anche avere un'immagine che assegna fino a 32 bit per canale di
colore. Queste immagini possono essere descritte come immagini "a 32
bit" e "immagini a 96 bit" (perché R (32) + G (32) + B (32) = 96). Tutti
i file HDR reali vengono memorizzati in formati immagine che assegnano
almeno un numero di punti a virgola mobile a 16 bit per ciascun pixel
per canale di colore, come il formato EXR oi formati a 32 bit, come il
formato RGBE. Per riassumere, un'immagine "8 bit per canale" con tre
canali (RGB) può anche essere chiamata immagine a "24 bit per pixel" e
un'immagine "a 16 bit per canale" con tre canali può anche essere
chiamata Immagine a 48 bit per pixel. In entrambi i casi utilizza il
carattere x (la descrizione completa "x bit per canale", non solo dire
"x bit"!), È più chiaro cosa intendi.