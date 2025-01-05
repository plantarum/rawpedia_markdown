# Ajouter la prise en charge de nouveaux formats raw

Il est facile d'ajouter dans RawTherapee la prise en charge parfaite de
nouveaux formats raw. Vous pouvez le faire vous-même, ou bien vous
pouvez nous envoyer les photos nécessaires afin que nous puissions faire
nous mêmes les mesures et ajouter la prise en charge de votre appareil
photo.

## Introduction

La lecture correcte d'un fichier raw nécessite la connaissance de
certaines choses à son sujet et RawTherapee recherche cette information
à trois endroits :

- Dans le code intégré de dcraw,
- Dans le fichier raw lui-même,
- Dans un fichier texte appelé camconst.json

L'information collectée est regroupée depuis les trois endroits, et
camconst.json en est le plus important pourvoyeur. En cas de
contradiction dans les informations, camconst.json est prioritaire.

camconst.json nous permet d'indiquer les éléments suivants :

- Les matrices de couleur pour [Illuminant
  D65](http://en.wikipedia.org/wiki/Illuminant_D65), au format dcraw,
- Les niveaux blanc et noir,
- Masque de recadrage pour enlever les lignes et colonnes non valides,

pour chaque combinaison de canal de couleur, ISO et ouverture d'un
appareil photo de fabricant et modèle donnés. Pour cette raison
camconst.json est à la fois l'endroit pour ajouter rapidement la prise
en charge détaillée des nouveaux formats raw ainsi que l'endroit pour
améliorer la prise en charge d'appareils photo déjà pris en compte par
dcraw mais de façon imparfaite.

## Photos requises

Pour réaliser les mesures nécessaires à une prise en compte parfaite,
vous aurez besoin de prendre plusieurs séries de photos avec des
réglages spécifiques :

- Chaque photo doit être complètement sur-exposée partout ! Réalisez
  cela en orientant votre appareil vers une lumière intense (par ex. le
  ciel, une lampe), zoomer plus grand si nécessaire, et augmenter le
  temps d'exposition jusqu'à ce que tout soit complètement hors domaine
  d'exposition. Bien sur déclencher en mode raw. Si votre appareil
  dispose de plusieurs modes raw, utiliser le total, si possible sans
  recadrage et compression sans pertes

1.  Si votre appareil dispose d'un dispositif intégré de réduction du
    bruit, le désactiver. Prendre une série de photos telles que
    décrites ci-dessus, une photo pour chaque valeur ISO dont votre
    appareil dispose (intervalle de 1 pas), en vous assurant de ne pas
    dépasser un temps d'exposition de 0.5s, en utilisant une ouverture
    de f/8. Par exemple, pour un appareil typique moderne, vous arrivez
    à environ 8 photos : ISO100, ISO200, ISO400, ISO800, ISO1600,
    ISO3200, ISO6400, ISO12800.
2.  Si votre appareil dispose d'un dispositif intégré de réduction du
    bruit, l'activer. Prendre une seconde série de photos telles que
    décrites ci-dessus, une photo pour chaque valeur ISO dont votre
    appareil dispose (intervalle de 1 pas), en vous assurant que le
    temps d'exposition est d'au moins 2 secondes dans tous les cas, pas
    moins, en utilisant une ouverture de f/5,6. Ce qui fait à nouveau 8
    photos.
3.  Certains appareils changent les valeurs raw d'échelle pour les plus
    grandes ouvertures, particulièrement les modèles Canon et Nikon. La
    seule façon de savoir avec certitude si votre appareil procède ainsi
    est de prendre une photo et de la mesurer. Prendre une photo en
    utilisant la plus grande ouverture possible de l'objectif, par ex.
    f/1.7, avec un ISO de 100, une longue pause, la réduction du bruit
    activée, et nous l'envoyer avec les autres photos. Si nous détectons
    un changement d'échelle des valeurs raw (ou si vous le détectez
    vous-même en réalisant vos propres mesures), alors nous vous
    demanderons de faire une nouvelle série de photos pour chaque valeur
    ISO (intervalle de 1 pas), avec un temps d'exposition inférieur à
    0.5 s, depuis l'ouverture la plus grande supportée par votre
    objectif, en diminuant à chaque fois de 1/3 de pas jusqu'à atteindre
    une ouverture pour laquelle le changement d'échelle des valeurs raw
    n'est plus appliqué. Cela peut entraîner beaucoup de photos. Gérer
    le changement d'échelle des valeurs raw causé par les grandes
    ouvertures n'est pas très important, aussi ne vous sentez pas
    découragé par cela, il n'est pas indispensable de le faire même si
    votre appareil y a recours, mais si vous avez le temps et la bande
    passante, alors c'est mieux de le vérifier.

Au final, vous vous retrouvez avec une série de 8 photos du point 1, ou
mieux une série du point 1 et du point 2, soit 16 photos, plus celle
concernant le changement d'échelle des valeurs raw du point 3. Si votre
appareil pratique le changement d'échelle des valeurs raw, vous devriez
ajouter les séries décrites au point 3 (soit environ 50 photos ou plus),
mais comme cela est beaucoup, on ne les exigent pas.

Compresser toutes ces photos et les téléverser à
[filebin.net](http://filebin.net/), nous envoyer le lien soit sur notre
page [GitHub](https://github.com/Beep6581/RawTherapee/issues/new) soit
sur le [Forum](http://rawtherapee.com/forum).

## Details

Pour une meilleure information, précisant les photos requises et les
instructions pour prendre les mesures, lire les commentaires inclus dans
le fichier camconst.json.
<https://github.com/Beep6581/RawTherapee/blob/master/rtengine/camconst.json>