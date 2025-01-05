<span style="color: #000000; background: none; overflow: hidden; page-break-after: avoid; font-size: 2.0em; font-family: Georgia,Times,serif; margin-top: 1em; margin-bottom: 0.25em; line-height: 1.3; padding: 0; border-bottom: 1px solid #AAAAAA;">Aberration
Chromatique</span>

<img src="chromatic_aberration_auto1.jpg"
title="chromatic_aberration_auto1.jpg" width="900"
alt="chromatic_aberration_auto1.jpg" />
<img src="chromatic_aberration_auto2.jpg"
title="chromatic_aberration_auto2.jpg" width="900"
alt="chromatic_aberration_auto2.jpg" /> Cet outil "Aberration
Chromatique" traite l'image **avant** le dématriçage, c'est la raison
pour laquelle il est placé dans l'onglet "raw". L'outil [Aberration
chromatique](Lens/Geometry/fr#Aberration_chromatique "wikilink") dans
l'onglet *Transformation* traite l'image **après** le dématriçage.

La correction de l'aberration chromatique au niveau du raw n'est
actuellement supportée que pour les fichiers raw en provenance
d'appareils photo équipés d'un [Filtre
Bayer](https://en.wikipedia.org/wiki/Bayer_filter). Si vous avez besoin
de corriger l'aberration chromatique sur des photos produites par des
appareils équipés de capteurs X-Trans (Fuji), utilisez alors l'outil
[Aberration
chromatique](Lens/Geometry/fr#Aberration_chromatique "wikilink") dans
l'onglet *Transformation*.

L'aberration chromatique peut être corrigée en utilisant les curseurs
"Rouge" et "Bleu". Normalement, vous ne verrez pas d'aberration
chromatique dans l'aperçu réglé sur "Ajuster à la fenêtre", il est donc
recommandé d'ouvrir une vue détaillée
[image:New-detail-window.png](image:New-detail-window.png "wikilink") ou
de zoomer l'aperçu principal à 100%
[image:Gtk-zoom-100.png](image:Gtk-zoom-100.png "wikilink") ou plus pour
procéder à ce type de correction.

Cet outil corrige les franges vertes-bleuâtres et magenta dues à
l'aberration chromatique latérale de l'objectif qui apparaît
principalement sur les bords de l'image. Cette correction est réalisée
avant le dématriçage et peut quelquefois en améliorer la qualité.

## Correction automatique

Si "Correction automatique" est coché, les curseurs "Rouge" et "Bleu"
sont désactivés et une détection et un correction automatiques de
l'aberration chromatique est réalisée. Alors que la correction manuelle
applique une valeur constante sur toute l'image, la Correction
automatique divise l'image en de nombreux blocs et adapte les valeurs
requises pour éliminer l'aberration chromatique dans chaque bloc. Pour
cette raison, la correction automatique est généralement plus
performante que la correction manuelle, et les valeurs de la correction
automatique ne peuvent pas être affichées par les curseurs.

## Rouge/Bleu

Si les curseurs "Rouge" et "Bleu" ne sont pas à zéro, les valeurs
affichées sont utilisées pour corriger l'aberration chromatique. Ils ne
peuvent être utilisés pour la Correction automatique.