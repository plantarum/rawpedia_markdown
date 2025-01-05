# 8 bits et 16 bits

Lorsqu'on parle de « 8-bits » en matière de formats d'image, signifie
que le programme attribue 8 [bits](https://fr.wikipedia.org/wiki/Bit) (8
valeurs égales à "1" ou "0" qui ensemble forment un
[octet](https://fr.wikipedia.org/wiki/Octet) capable de représenter tout
nombre [entier](https://fr.wikipedia.org/wiki/Entier_relatif) depuis 0
\[00000000\] jusqu'à 255 \[11111111\]) à chaque canal de couleur du
pixel, et dans les fichiers enregistrés par RawTherapee, chaque pixel
possède trois canaux : rouge, vert et bleu.

La plupart des appareils photo
[réflexes](https://fr.wikipedia.org/wiki/Appareil_photographique_reflex_num%C3%A9rique)
(ou [DSLR](https://en.wikipedia.org/wiki/DSLR) en anglais) modernes
proposant le format raw utilisent un convertisseur analogique /
numérique de 12 ou 14 bits pour enregistrer les données du capteur. Cela
signifie que choisir pour votre appareil photo un format de sortie de 8
bits par canal, comme JPEG, provoque une perte d'informations. Cela
n'est pas aussi simple qu'il y parait, les appareils enregistrent les
données linéairement (en raison de limitations dans la conception du
matériel) alors que les formats JPEG, TIFF et PNG [encodent leur données
selon le gamma](https://fr.wikipedia.org/wiki/Correction_gamma) ce qui
signifie qu'ils attribuent plus de valeurs dans les ombres et moins dans
les hautes lumières, car cela correspond mieux à la sensibilité de
l’œil. Cela signifie aussi qu'une image JPEG 8 bits peut afficher un
nombre de pas de la gamme dynamique égal à log2((1/2^8)^2.2) = 17.6; ce
qui dépasse les 14 pas des meilleurs appareils actuels. Cela explique
pourquoi vous pouvez quelquefois apercevoir le bruit de l'appareil dans
les ombres même dans une image JPEG de 8 bits. Cependant, en raison du
moindre nombre de valeurs dans les hautes lumières nous perdons de la
précision à ce niveau comparé au potentiel de l'appareil. En pratique,
cela n'est pas un problème quand le fichier de sortie est le fichier
définitif sans traitement ultérieur. Cependant, une photo peut-être
considérablement améliorée si elle est enregistrée au format raw puis
traitée à l'aide d'un programme de développement numérique dernier cri
tel que votre fidèle serviteur : RawTherapee.

Une fois la photo développée par RawTherapee, vous êtes confronté au
même choix, enregistrer l'image avec une résolution de couleur de 8 bits
ou de 16 bits par canal (seuls
[TIFF](https://fr.wikipedia.org/wiki/Tagged_Image_File_Format) et
[PNG](https://fr.wikipedia.org/wiki/Portable_Network_Graphics), pas
[JPEG](https://fr.wikipedia.org/wiki/JPEG)). Si après développement par
RawTherapee vous envisagez de retoucher vos photos dans un éditeur
d'image en 16 bits, c'est mieux de les enregistrer dans un format 16
bits non destructif. Le TIFF non compressé est considéré comme un format
intermédiaire, vu qu'il est rapide à l'enregistrement et conserve toutes
les métadonnées
([EXIF](https://fr.wikipedia.org/wiki/Exchangeable_image_file_format),
[IPTC](https://fr.wikipedia.org/wiki/IPTC_Information_Interchange_Model),
[XMP](https://fr.wikipedia.org/wiki/Extensible_Metadata_Platform)) du
fichier original, (généralement, PNG élimine les métadonnées).

Il existe une certaine confusion a propos de la désignation 8, 16, 24 ou
32 bits. Voici une clarification, du moins espérons-le, accrochez-vous.
En fait, vous n'avez pas besoin de lire cela pour utiliser RawTherapee,
c'est juste pour votre connaissance générale. Chacun des canaux rouge,
vert et bleu enregistrés dans un fichier JPEG, PNG ou TIFF est en fait
une image sans couleur, mais lorsque vous combinez ensemble ces trois
images sans couleur, vous obtenez une image en couleur. C'est de cette
façon que fonctionnent toutes les représentations numériques d'images,
les couleurs sont toujours décomposées suivant leurs composantes d'une
façon ou d'une autre. Dans tous les formats de fichier vers lesquels
RawTherapee peut enregistrer (JPG, PNG et TIFF), chaque pixel possède
les informations concernant les trois canaux de couleur, rouge vert et
bleu. Nous disons « 8 bits par canal » pour signifier clairement que ces
8 bits ne concernent qu'un seul canal de couleur. La raison en est que
vous pouvez rencontrer des références à des « images 8 bits » et c'est
équivoque car celui qui écrit cela peut vouloir faire référence à des
formats d'images capables de n'enregistrer que des images en échelle de
gris, qui n'enregistrent qu'un seul canal ou bien à des formats d'images
qui enregistrent trois canaux avec une précision de 8 bits pour chaque.
Une autre notation possible pour exactement les mêmes images « 8 bits »
que RawTherapee enregistre, est « 24 bits ». Waouh ! Perturbant.
Vraiment ? Chaque pixel comprend trois canaux, et chaque canal est formé
de 8 bits de données, on a donc bien un total de 24 bits de données par
pixel. Et cela empire. Les programmes d'édition des images peuvent aussi
enregistrer un quatrième canal, appelé alpha. Pour faire simple, alpha
indique le niveau de transparence du pixel. Ces canaux alpha possèdent
aussi une « résolution de couleur » sur 8 bits. PNG et TIFF peuvent tous
les deux gérer l'alpha, pas JPG. Si vous avez une image de 8 bits par
canal plus un canal alpha, elle peut aussi être désignée comme étant une
image 32 bits ; R (8) + V(8) + B(8) + alpha(8) = 32. L'ultime problème
est que vous pouvez aussi avoir une image qui attribue 32 bits par canal
de couleur. Ces images peuvent être aussi bien désignées comme des
images « 32 bits » que comme des images « 96 bits » (car R (32) +
V(32) + B(32) = 96). Tous les fichiers d'image en véritable HDR sont
enregistrés dans un format qui attribue au moins 16 bits en virgule
flottante par canal de couleur, comme le format EXR ; ou 32 bits, comme
le format RGBE. Pour résumer, une image « 8 bits par canal » avec trois
canaux (RVB) peut aussi être appelée une image « 24 bits par pixel ».
Une image « 16 bits par canal » avec trois canaux peut aussi être
appelée une image « 48 bits par pixel ». Dans les 2 cas, utilisez la
première appellation, (la description complète « x bits par canal » et
ne dite pas seulement « x bits »), ce que vous dites est plus clair.