Par J.Desmis

## A propos de CIECAM02

### Introduction - historique

Depuis de nombreuses années l'homme essaie de modéliser la couleur, sa
perception par les individus.

De nombreux travaux ont été réalisés dès le moyen-âge, mais concrètement
c'est au 19ème siècle, puis au 20ème qu'ont été faites les principales
avancées.

Je ne suis pas un spécialiste de la physiologie du système visuel
humain, pas plus qu'un chercheur dans le domaine complexe de la
colorimétrie. J'ai repris quelques informations minimales qui me
semblent indispensable à la compréhension, au lecteur intéressé
d'approfondir s'il le souhaite ces données par l'utilisation du Web ou
des quelques liens que je joins.

Couramment en photographie, on se sert de modèles qui ont 50 ans ou plus
: RGB et ses dérivés (HSV, HSL, CMJN,...), XYZ, et Lab et ses dérivés
(Luv, Lch).

Je ne reviendrais pas sur le modèle RGB qui est connu de tous, il est
dépendant du périphérique et ne prend en compte aucun CAM (color
appearance model).

La définition du CIE XYZ (1931) a constitué le premier pas de la
commission internationale de l'éclairage(CIE) vers une description des
couleurs conforme à la vision humaine. Sommairement, une couleur peut
être caractérisée par 3 valeurs X,Y,Z obtenues par combinaison de «
tristrimulus values », « CIE standard observer » et la « spectral power
distribution » de la couleur de base. Ce modèle est repris dans RT
notamment au niveau de la balance des blancs...Ce modèle ne prend en
compte aucun CAM, mais c'est une avancée extraordinaire, car on peut
dorénavant modéliser la couleur en termes cognitifs.

Le modèle Lab a été mis au point en 1976 par la CIE en le dérivant du
modèle XYZ, il caractérise une couleur à l'aide d'un paramètre
d'intensité correspondant à la luminance et de deux paramètres de
chrominance qui décrivent la couleur. Il a été spécialement étudié pour
que les distances calculées entre couleurs correspondent aux différences
perçues par l’œil humain. Le modèle Lab est très implanté dans RT, il
sert de base à une majorité de fonctionnalités : renforcement
(sharpening), bruit (denoise), tone mapping, Lab adjustements, etc.. Le
modèle Lab possède quelques caractéristiques d'un CAM, mais les
prestations sont sommaires. Le modèle CIECAM02, dérivé du CIECAM97 et
s'appuyant sur les travaux de G.Hunt, est le premier modèle utilisable
couramment en photographie, car il est inversible...et relativement «
simple », il permet de prendre en compte d'autres aspects que ceux
purement cognitifs et est fondé sur les travaux de nombreux chercheurs
sur la base d'échantillon de personnes qui évaluent différents
paramètres comme :

- le contraste simultané : variation de l’apparence colorée d’un objet
  en fonction des caractéristiques colorimétriques de son environnement
  proche. Par exemple une même couleur sera perçue différemment sur un
  fond clair ou sombre, plus le fond sera sombre plus il va être
  nécessaire de renforcer la couleur...

<!-- -->

- l'effet de Hunt :augmentation de la coloration perçue (colorfulness)
  avec la luminance.Un objet apparaît plus vif et contrasté en pleine
  lumière qu’à l’ombre.
- Effet de Stevens : augmentation du contraste perçu avec la luminance.
  Quand la luminance augmente, les couleurs sombres apparaissent encore
  plus sombres et les couleurs lumineuses apparaissent encore plus
  lumineuses.
- Effet de Helmholtz-Kohlrausch : dépendance de la brillance
  (brightness) par rapport à la luminance et à la chromaticité. Les
  objets de couleur apparaissent plus clairs que les objets
  achromatiques ayant la même luminance. Les couleurs les plus saturées
  apparaissent les plus brillantes.
- Adaptation chromatique:ajustement par le système de vision de l'homme
  de certains stimuli couleur. L’adaptation chromatique nous permet
  d’interpréter une couleur selon son environnement spatio-temporel.
  C’est un effet essentiel à prendre en compte par un CAM.
- L'adaptation chromatique est la capacité du système visuel humain à
  s'ajuster aux changements de conditions d'illuminant. Autrement dit,
  nous nous adaptons à la couleur de la source lumineuse pour mieux
  préserver la couleur des objets. Par exemple, sous une lumière
  incandescente, un livre blanc apparaît jaune. Cependant, nous avons la
  capacité automatiquement de modéliser la lumière jaunâtre et nous
  voyons donc le papier comme blanc. Le monde qui nous entoure serait en
  effet très compliqué si les objets changeaient de couleur chaque fois
  que la source de lumière change même légèrement. Depuis la nuit des
  temps, nous devons être capable de savoir si un fruit est mûr que ce
  soit le matin, le midi, ou le soir. L'adaptation chromatique nous rend
  cela possible. Mais elle peut être aussi la source de nombreuses
  illusions d’optique. Je pense que la majorité des utilisateurs de RT
  connaissent au moins de nom, le précédent modèle d'adaptation
  chromatique « Bradford »
- etc.

Remarque : il ne sera pas ici question de « Munsell Correction », car
par principe CIECAM02 est construit autour des tables de Munsell...cette
correction est donc prise en compte, même si le modèle présente des
lacunes !

Mes premières réflexions à propos de CIECAM02 remontent à 2007, et à
l'élaboration d'une feuille de calcul, pour obtenir les meilleurs
résultats lors de l'élaboration de profils « ICC input ».

Début 2012, je me suis penché sur une demande des utilisateurs : «
peut-on avoir des références de couleurs – palette de couleur – (peau,
ciel,..) qui permettraient par comparaison/itération une meilleure
balance des blancs ». J'ai également travaillé sur la notion de « CRI
-Color rendering Index » qui traduit l'écart d'un illuminant par rapport
aux illuminants de base...plus le CRI est bas, plus le rendu sera
mauvais à température de couleur
identique[Color_Management/fr](Color_Management/fr "wikilink")

Le patch s'appuyant sur CIECAM02, contient les éléments nécessaires de
base pour travailler ces 2 points, mais il manque un élément essentiel,
pas évident à élaborer..une pipette...

J'ai longtemps considéré CIECAM02, non pas comme un gadget, mais comme
quelque chose de difficile à mettre en œuvre...et avec un bonus assez
faible par rapport à Lab. La demande de Michael Ezra qui m'a d'abord
surpris, m'a amené à ré ouvrir le dossier ; le plug-in pour Photoshop a
été pour moi une découverte par l’exemple, de CIECAM02. Je suis
aujourd'hui convaincu que même si le modèle n'est pas parfait (pour
certaines photos l'utilisation est quasi impossible!), c'est à ce jour
un plus indéniable en termes de gestion des couleurs. Le module que je
propose est une « initiation », il est possible de développer à partir
des données CIECAM02, une série de fonctionnalités similaire à celles
développées dans RT (Lab adjustements avec divers courbes, tone-mapping,
etc.) avec probablement des avancées significatives en termes de
qualité.

L'absence de véritable documentation ajoute à la complexité...Certains
point de vue sont personnels (peut être entachés d'erreur ?). Si un
spécialiste lit ces lignes je serai heureux de modifier mon texte et mes
algorithmes !)

### Quelques définitions

1.  Brigthness \[brillance\](CIECAM02) : La quantité de lumière perçue
    émanant d’un stimulus = Indicateur qu’un stimulus apparaît comme
    plus ou moins lumineux, clair.
2.  Ligthness \[luminosité, luminance, clarté\](Lab, CIECAM02):

    La clarté d’un stimulus relativement à la clarté d’un stimulus qui
    apparaît blanc sous des conditions similaires de visualisation.

    A noter que dans RT, le terme « brightness » s'applique à «
    Lightness » ! Il sera nécessaire de réaliser un patch pour renommer
    « brightness » en « lightness » dans les modules « exposition », «
    Lab adjustements », etc.
3.  Hue (teinte) et angle de teinte (partiellement dans Lab , CIECAM02)
    : Le degré auquel un stimulus peut être décrit comme similaire à une
    couleur décrite comme rouge, vert, bleu et jaune.
4.  Colorfulness (CIECAM02): La quantité perçue de teinte par rapport au
    gris,= indicateur qu’un stimulus apparaît comme plus ou moins
    coloré.
5.  Chroma (Lab, CIECAM02) : La « coloration» d’un stimulus relativement
    à la clarté d’un stimulus qui apparaît blanc sous des conditions
    identiques.
6.  Saturation (CIECAM02): La coloration d’un stimulus par rapport à sa
    propre bril"lance

En résumé :

1.  Chroma = (Colorfulness) / (Brightness of White)
2.  Saturation = (Colorfulness) / (Brightness)
3.  Lightness = (Brightness) / (Brightness of White)
4.  Saturation = (Chroma) / (Lightness)

    = \[(Colorfulness) / (Brightness of White)\]\* \[(Brightness of
    White) / (Brightness)\]

    = (Colorfulness) / (Brightness)

CIECAM02 élabore et utilise plusieurs type de variables corrélées qui
permettent d'utiliser ces concepts :

J: lightness ou clarté, proche de L (Lab)

C: Chroma, proche de C (Lab)

h : angle de teinte, proche de H (Lab)

H: teinte. Une teinte peut être décrite par la composition de 2 couleurs
de base parmi 4 (rouge, jaune, vert, bleu), par exemple 30B70G ou encore
40R60Y.

Q: brightness

M : colorfullness

ac, bc : proches de a et b (Lab)

Alors ! Pourquoi la saturation en plus d'autres variables proches ? Je
cite un texte de Robert Hunt (2001)


*Of the three basic color perceptions, hue, brightness, and
colorfulness, hue has no relative version, but brightness has lightness,
and colorfulness has chroma and saturation. Correlates of chroma are
widely used in color difference formulae, but saturation currently plays
little part in color science and technology. This is perhaps because in
many industries flat samples are viewed in uniform lighting for the
evaluation of color differences, and in this case chroma is the
appropriate contributor for samples of small angular subtense. For
samples of large angular subtense, however, a correlate of saturation
may be more appropriate to use. In the real world, it is common for
solid objects to be seen in directional lighting; in these circumstances
saturation is a more useful percept than chroma because saturation
remains constant in shadows. In imaging, artists and computer-graphics
operators make extensive use of series of colors of constant saturation.
In optical imaging, saturation can be an important percept in large dark
areas. Recent experimental work has provided a much improved correlate
of saturation.*

## Les 3 processus

Trois processus permettent l'utilisation de CIECAM, leurs appellations
dépend de chaque concepteur...J'en fait une synthèse (rappel : ce
document n'est pas un cours, ni une thèse sur CIECAM...mais une aide à
la compréhension et à l'utilisation).

### Processus 1

On trouve les appellations de « origin », « forward », « input », «
source »... Finalement j'ai choisi « source » qui correspond aux
conditions de prise de vue et à la manière de ramener les conditions et
les données, vers une zone « normale ». Il faut entendre par « normale
», des conditions et des données moyennes ou standard, c'est à dire sans
prise en compte des corrections CIECAM, par exemple « surround=average
», balance des blancs D50 !

### Processus 2

Il correspond au traitement des variables corrélées (J C h H Q M s a b)
à diverses fins : action sur la clarté (lightness J), la brillance
(brightness Q), la chroma (C), la saturation (s), le niveau de couleur
(colorfullness M), l'angle de teinte h, ainsi que sur ac et bc. Il est
tout à fait possible de construire un logiciel graphique autour de ses
variables...

Dans le cas de ce patch pour RT, j'ai choisi arbitrairement 4
regroupements d'algorithmes :

1.  JC en lui adjoignant une fonction contraste ;
2.  Js, comme ci-dessus
3.  QM
4.  Tout : ensemble des paramètres y compris h.

Ces modules sont simples, plus à caractère pédagogique que de chercher à
résoudre les problèmes de colorimétrie, même si les résultats obtenus
sont de mon point de vue excellents.

J'ai complété ce processus par :

1.  des « curves » (double...) agissant sur les contrastes J (lightness)
    ou Q (brightness) dont le principe est similaire aux courbes doubles
    de « exposition » ;
2.  un choix pour des courbes de couleur entre chroma, saturation et
    colorfullness (niveau de couleurs) .

On pourrait ajouter d'autres algorithmes s'appuyant sur la transformée
de Fourrier, ou remplaçant les fonctions équivalentes de RT...

### Processus 3

On trouve les appellations de « inverse », « reverse », « ouput », ou
encore « viewing conditions ».

J'ai choisi « viewing conditions » qui traduit le support sur lequel
sera visionnée l'image finale (moniteur, TV, projecteur,...), ainsi que
son environnement. Ce processus va prendre les données venant du
processus 2 et les « amener » au support de telle manière que les
conditions de visualisation et de son environnement soient prise en
compte.

Nota : c'est ici qu'on trouve l'explication sur la différence de rendu
entre une photo imprimée et une photo examinée sur un moniteur – même si
l'imprimante est haut de gamme et bien étalonnée : les conditions
d'observation ! Une photo imprimée sera souvent regardée dans un album
(souvent sur un fond noir), dans un environnement peu lumineux...et
souvent en éclairage tungstène. L'originale sera vue sur un moniteur
avec un fond clair...et un illuminant D50...Il n'est pas question de
modifier la sortie « impression », mais d'adapter la sortie « moniteur,
TV... »

Ceci revient à dire, mais là s'arrête la comparaison, qu'on réalise
quelque chose qui ressemble à un épreuvage, mais ce n'en est pas un
puisque c'est la finalité de CIECAM, On prend en compte les réglages
prévus dans « préférences » (point blanc du périphérique de sortie
\[écran TV, projecteur...\], ainsi que sa luminance moyenne \[% gris\].
On prend également en compte la luminance de la pièce dans laquelle se
fait l'observation, ainsi que la luminance relative de l'entourage du
périphérique de visualisation (plus ou moins noir).

Synthèse simplifiée ce que permet RT avec le patch actuel :

1.  cas général de l'utilisateur qui utilise RT pour visualiser son
    développement...ce doit être 95% des cas. Dans ce cas « viewing
    conditions » correspond à l'environnement de travail de RT, par
    exemple :
    - point blanc du moniteur réglé sur 6000K
    - moniteur étalonné : donc Yb=18
    - mais selon :
      - le « theme » choisi dans « Preferences / General» (presque noir
        ou gris), il faut changer « surround »
      - l'emplacement du moniteur (sur fond neutre ou foncé), il faut
        changer « surround »
      - l'éclairage de la pièce, qui va changer avec l'heure , il va
        falloir changer « adaptation luminosity viewing La »: par
        exemple la nuit sans éclairage d'appoint « La » sera proche de 0
        ou de 1, et à l'inverse le jour dans une pièce très lumineuse, «
        La » sera proche de 1000
2.  Cas moins fréquent, mais possible, car je l'ai déjà fait, je me sers
    de RT et du téléviseur familial pour montrer des photos et aussi les
    possibilités de RT. Les « viewing conditions » seront différentes et
    à adapter à chaque cas ; il faut reprendre chacun des points
    ci-dessus avec probablement des réglages différents : point blanc
    TV, Yb TV (empirique) ?, « surround » différent car en général on
    regarde la TV sur un fond tamisé, et on réduit l'éclairage de la
    pièce
3.  on souhaite préparer une série de photos, pour une exposition : dans
    ce cas en bon professionnel on va « voir » les conditions de
    visionnement sur place et on pose des questions sur le projecteur :
    point blanc, étalonnage (??), luminosité de la salle le jour de
    l'expo, etc. Avec RT l'utilisateur va régler « viewing conditions »
    pour les adapter aux conditions de l'exposition, et sortir X jpeg
    (ou TIFF) correspondants
4.  etc.
5.  C'est pourquoi, j'ai mis la plupart des réglages du processus \#3
    dans "Préférences", ce n'est pas une erreur, mais apparaît similaire
    à mettre le profil du moniteur qui dépend du moniteur

## Données

Quelles sont les données prises en compte et quelle simplifications
ai-je (arbitrairement?) opérées ? Comment les ajuster ?:

- **Yb** : Yb est la luminance relative de l'arrière plan ! Avec cela on
  a beaucoup avancé ! Concrètement elle s'exprime en % de gris. Un gris
  à 18% correspond à une luminance du fond exprimée en CIE L de 50%.

:\*pour le processus 3), si votre moniteur est étalonné vous devez sans
problème avoir une valeur de Yb proche de 18 ou 20. Si le téléviseur ou
le projecteur, qu'il semble difficile d'étalonner, vous paraît sombre,
ou clair vous pouvez ajuster empiriquement cette valeur. Elle dépend du
support de visualisation et peut donc être considérée comme constante
pour un ensemble de photos dans une condition d'observation. Si vous
souhaitez changer cette valeur allez dans « Preferences », « Color
Management » : « Yb luminance output device (%) »

:\*pour le processus 1) c'est nettement plus complexe, car :

::\*une image est rarement avec une exposition constante et peu de
variations de luminance ;

::\*j'ai placé le module CIECAM en fin du processus Lab, juste avant la
conversion RGB et l'envoie sur des périphériques de sortie ; on peut
donc penser que l'utilisateur aura utilisé les divers outils (de
qualité) de RT pour rendre l'image avec un histogramme « moyen ».



J'ai donc arbitrairement rendu inaccessible cette donnée en la calculant
à partir de la luminance moyenne de l'image. Bien sûr si dans l'avenir
RT était capable à l'aide de pipettes de séparer l'images en zones
(sombres, normales, lumineuses...) il serait possible d'entrer plusieurs
valeurs Yb. Par exemple sur une image on pourrait voir trois zones :

- standard qui correspond à la luminance moyenne de l'image avec un Yb
  réglé à 20% ;
- sous exposée (contours approximatifs délimités à la pipette...) où la
  luminance serait calculée et aboutirait par exemple à un Yb de 5% ;
- surexposée où on arriverait à un Yb de 70%...

- **La** : La est la luminance absolue du champ d'adaptation ! Là encore
  on a beaucoup avancé !

:\*Dans le processus 1) elle correspond à la luminance lors de la prise
de vue, si par exemple vous faites une photo à l'ombre, « La » sera
proche de 2000cd/m2 ; si vous faites des prises de vues intérieur, « La
» variera en fonction de l'éclairage de 20 à 300cd/m2...En reproduction,
ces valeurs pourront être plus faibles encore

:\***”Luminosité de la Scène” et le bouton“Auto”** (processus \#1):

:\*\* Si activée, La est calculée avec les données Exif (vitesse
d'exposition, ISO, Diaphragme, compensation d'exposition de l'appareil)
et aussi le point blanc Raw et le curseur de compensation d'exposition

:\*pour le processus \#3, cette donnée traduit l'entourage de l'image
lors de la visualisation. Plus l'entourage sera sombre, plus il faudra
accroître le contraste de l'image. La variable « surround » n'agit pas
comme un D-lighting ou une courbe de tons, elle modifie également les
couleurs dans les axes rouge-vert et bleu-jaune. Si la luminance de
l'entourage est supérieure à 20% choisissez « average », sinon adaptez à
vos conditions, par exemple les réglages de RT (Preferences / General /
Select theme) auront une incidence sur le rendu final. Ce réglage est
accessible par « Surround(viewing) ». plus l'entourage sera sombre, plus
l'image verra son contraste simultané accentué.

:\*Ces 2 valeurs de “La" sont paramétrable dans RT, dans le module“CIE
Color Appearance Model 2002”

- **Surround** (Entourage)

:\*ici encore j'ai procédé à des simplifications...

:\*pour le processus 1) cette donnée traduit certaines conditions de
prise de vue, par exemple photos dans un musée avec un fond sombre, ou
encore réalisation d'un portrait sur un fond noir. Généralement
l'utilisateur de RT aura corrigé avec les nombreux outils, les écarts
par rapport à sa perception. Néanmoins j'ai ajouté une case à cocher «
Surround (scene) dark » (entourage sombre), qui peut être activée si
nécessaire. Son utilisation aura pour effet d'éclaircir l'image (rappel
le processus « ramène » les données pour les amener « normales »

:\*pour le processus 3), cette donnée traduit l'entourage de l'image
lors de la visualisation. Plus l'entourage sera sombre, plus il faudra
accroître le contraste de l'image. La variable « surround » n'agit pas
comme un D-lighting ou une courbe de tons, elle modifie également les
couleurs dans les axes rouge-vert et bleu-jaune. Si la luminance de
l'entourage est supérieure à 20% choisissez « average » (moyen), sinon
adaptez à vos conditions, par exemple les réglages de RT (Preferences /
General / Select theme) auront une incidence sur le rendu final. Ce
réglage est accessible par « Surround(viewing) ». plus l'entourage sera
sombre, plus l'image verra son contraste simultané accentué.

- **White-points model** (modèle de point blanc)

:\*2 possibilités s'offrent à vous, là encore j'ai tenu à simplifier au
maximum.

:\*« WB RT + output » : ici on fait confiance à la balance des blancs de
RT pour le processus 1) ; CIECAM utilise D50 comme référence : la
balance des blancs de RT ramène les conditions à un équivalent D50 ; par
contre pour le processus 3), il va être nécessaire – selon le besoin –
de régler le point blanc du périphérique de sortie. Allez dans «
Preference / Color Management / Settings white output device (monitor,
TV, projector) et choisissez un illuminant parmi la liste (est-elle
suffisante ? Je n'ai aucune idée sur les caractéristiques des
projecteurs , lampe, température...

:\*« WB RT+CAT02 + output » ; pour le processus 3) on se retrouve comme
ci-dessus ; pour le processus 1) un mix est réalisé entre la balance des
blancs de RT et CAT02 qui utilise ses réglages, ce qui fait qu'on a une
solution où les 2 effets (RT et CAT02) se combinent). Vous pouvez
moduler l'action de CAT02, en agissant sur le curseur « CAT02 adaptation
». Vous serez probablement amenés à changer le réglage de la balance des
blancs de RT, afin de bénéficier des avantages du « mix », sinon les
effets s'ajoutent.

:\*CAT02 est une adaptation chromatique, elle convertit les valeurs XYZ
d'une image dont le point blanc est Xw0,Yw0, Zw0, en de nouvelles
valeurs XYZ dont le point blanc devient Xw1,Yw1,Zw1 ; l'algorithme
utilisé est proche de celui de Von Kries, donc différent de la
correction de RT qui prend en compte les multiplicateurs de canaux !

- **«CAT02 adaptation et case à cocher « auto »**

:\*voir ci-dessus pour l'utilisation « WB CAT02 + output »

:\*cependant même lorsque « white point model » est sur « equal », ce
curseur peut être utile. Normalement la cas « auto » doit être cochée et
CIECAM calcule lui même un coefficient interne « D » qui sert ailleurs
qu'à l'adaptation chromatique. Le résultat se traduit par une valeur
supérieure à 0.65 (65%), ; vous pouvez décocher la case ce qui aura pour
effet de modifier le processus 1), les effets peuvent être inattendus...

## Algorithmes

Choisissez JC, JS, QM (bien sûr il y a d'autres combinaisons
possibles!), ou « Tout » qui reprend l'ensemble des paramètres possibles
(j'ai arbitrairement exclu « h » ainsi que « ac » et « bc » des 3
algorithmes JC, JS, QM).L'utilisation la plus courante (si on peut
utiliser ce terme pour CIECAM) est JC. Agissez ensuite sur les curseurs
pour obtenir le rendu souhaité...qui je le rappelle dépend du
périphérique de visualisation, de son environnement, de ses réglages et
de la luminance de la pièce.

- **Algorithme JC**

:\*J simule la luminosité (lightness) – proche de L (Lab) et C simule la
chroma, proche de la chromaticité c (Lch). Mais, différence importante,
J et C prennent en compte les « effets » (contraste simultané, Hunt,
Stevens, etc.) ce que ne fait pas Lab et encore moins RGB.

:\*J varie dans l'intervalle \[0..100\] et correspond à une valeur
relative de la luminosité (comme L, ou Value...) et en théorie C dans
l'intervalle \[0..180\] (il peut être plus élevé)

:\*Les 2 curseurs qui utilisent J et C peuvent varier de -100, à +100
avec des actions semblables aux curseurs « Brightness » (qu'il faut
rebaptiser Lightness) et « Chromaticity » de « Lab adjstements »

:\*avec l'algorithme « JC », un contrôle des tons chairs est possible,
l'action est semblable au curseur similaire de « Lab adjustements »

:\*Le curseur « contrast » module l'action de « J » avec une courbe en «
S », qui prend en compte la luminosité moyenne « J » de l'histogramme.

- **Algorithme « Js »**

:\*il est similaire à JC sinon :

:\*la chroma est remplacée par la saturation (CIECAM). Mais pour quel
usage ? Je cite à nouveau un extrait du texte de G.Hunt : *For samples
of large angular subtense, however, a correlate of saturation may be
more appropriate to use. In the real world, it is common for solid
objects to be seen in directional lighting; in these circumstances
saturation is a more useful percept than chroma because saturation
remains constant in shadows. In imaging, artists and computer-graphics
operators make extensive use of series of colors of constant saturation.
In optical imaging, saturation can be an important percept in large dark
areas. Recent experimental work has provided a much improved correlate
of saturation.*

:\*Le contrôle des tons chairs est moins « fin » que avec « JC » plus
étendu globalement aux rouges

- **Algorithme QM**

:\*ici on utilise 2 variables Q (« brightness ») et M (« Colorfullness
») qui ne sont pas des données relatives, mais absolues. On prend en
compte la luminosité du blanc. Il est facile de se rendre compte qu'un
même blanc « J=100 » paraîtra plus lumineux au soleil que dans une pièce
sombre...

:\*la luminosité du blanc prend en compte les paramètres suivant (scène)
: « adaptation luminosity La », « CAT02 adaptation »,ainsi que « Yb »
(non réglable actuellement)

:\*le contrôle en usage courant est plus délicat que avec « JC »,
néanmoins il donne des possibilités pour les images à haut contraste et
ouvre la porte au traitement HDR

:\*Le contrôle des tons chairs est moins « fin » que avec « JC » plus
étendu globalement aux rouges

:\*Le « contraste » agit évidemment différemment...puisqu'il prend en
compte Q différent de J.

- **Algorithme « Tout »**

:\*vous pouvez agir sur l'ensemble des variables CIECAM : J, Q, chroma
C, saturation s, niveau de couleur M, contraste J, contraste Q, angle de
teinte h, protection des tons chair et rouges .

## Courbes tonales et couleur

### Courbes

- vous disposez – comme dans le module «exposition » de deux jeux de
  courbes tonales, qui agissent sur la luminosité J (lightness) et la
  brillance Q (brightness). Vous pouvez n'utiliser qu'une courbe, ou
  deux en mariant ou non « lightness » et « brightness ». Attention, les
  courbes « brightness » peuvent facilement aboutir à des résultats hors
  limites ! « Brightness » est une échelle absolue, alors que «
  Lightness » est une échelle relative, un même blanc « J » paraîtra
  plus blanc au soleil qu'à l'ombre, ce que prend en compte « brightness
  » (Q). De ce fait les courbes, « lightness » et « brightness » auront
  un rendu différent dans les ombres et les lumières élevées.
- vous disposez également d'un jeu de courbe « chroma » avec 3 choix :
  chroma (le plus courant), saturation, colorfullness. Ces 3 courbes
  permettent d'ajuster le paramètre choisi en fonction de lui même, par
  exemple moduler la saturation afin d'éviter que les couleurs déjà
  saturées soient hors gamut. Pour ces 3 courbes, le curseur «
  protection des tons chairs et rouge » est opérationnel, il est plus
  approprié aux tons chairs dans le mode « chroma ». Je recommande
  d'utiliser le mode « parametric » qui permet de différencier selon le
  niveau de sautration des couleurs. Nota : toutes les combinaisons «
  curves chroma» (chroma, saturation, colorfullness) et curseurs
  (chroma, saturation, colorfullness) ne sont pas possible sans
  complexifier par trop le code, d'où quelques cas, où certains curseurs
  peuvent être grisés.

### Histogramme et courbes tonales

L'histogramme des courbes tonales, dans le *CIE Color Appearance Model
2002*, peut montrer les valeurs avant ou après que CIECAM02 est
appliqué. Pour voir les valeurs après l'action de CIECAM02, activer
l'option "*Show CIECAM02 output histograms in curves*". Si désactivé
l'histogramme affiche les valeurs avant CIECAM02

### Histogramme et courbe couleur

L'histogramme de la courbe couleur montre la distribution de la chroma
(saturation/colorfullness) en fonction de l'intensité de la chroma
(saturation / colorfullness) ou de la chromaticité en mode Lab. Plus
l'histogramme est décalé à droite, plus les couleurs saturées sont
proches des limites du gamut. Plus l'histogramme est décalé vers la
gauche plus les couleurs seront ternes.

L'absciise représente la valeur de la chroma (saturation/colorfullnees)
ou de la chromaticité en mode Lab. Cette échelle est "ouverte"

Comme d'habitude, l'ordonnée représente le nombre de pixels concernés.

## Gamut control (Lab + CIECAM)

Cette case à cocher va faire rentrer les données dans l'espace de
travail, j'aurais pu réaliser cette action en mode CIECAM (processus 3)
mais cela aurait considérablement ralenti le système.

L'algorithme utilisé est le même que dans « Lab adjustements », il
travaille en colorimétrie relative. Les écarts avec ce qui pourrait se
faire en mode CIECAM sont je pense minimes.

Quelques ajustements du code de CIECAM sont réalisés lorsqu'on coche la
case « Gamut control »...

## Code, précision des calculs et temps de traitement

Le code pour les processus 1 et 3 est strictement celui de CIECAM02
(M.Fairchild, Billy Biggs,...) que j'ai adapté à RT et optimisé, ainsi
que des améliorations apportées à la correction du gamut par Changjun
Li, Esther Perales, M Ronnier Luo and Francisco Martínez-Verdú

Les 2 processus de traitement 1) et 3) sont symétriques et empilent de
nombreux calculs en virgule flottante. Le recours à « double » est
indispensable. D'où des temps de traitement assez importants de l'ordre
de 1 seconde par Mpix.. Après des tests intensifs nous avons montré que
l'utilisation de la précision "float" au leiu de "double" n'avait pas de
grosses conséquences en termes de rendu d'image.. Vous pouvez changer ce
réglage dans "Preferences / Color Management"

En termes de précision j'ai tenu à vérifier « à blanc », en comparant
une série de données avant et après CIECAM ; les écarts sont très
faibles , par exemple une valeur XYZ au démarrage de 6432,456 se
retrouve en sortie à 6432,388, ce qui est correct.

## Limitations de CIECAM02

Ce modèle n'est pas parfait et les limitations ci-après sont
identifiées, elles peuvent aboutir pour certaines images à
l'impossibilité d'un traitement correct :

- on a déjà pu le voir pour les réglages de Yb.
- CIECAM02 n'est pas un espace de travail comme sRGB ou Prophoto ou même
  Lab ; en ce sens il est difficile de contrôler le gamut, CIECAM est
  même connu pour ses problèmes de gamut étroit, ainsi des effets
  inattendus peuvent survenir aux limites si vous agissez trop sur les
  curseurs (J, C, s...) ; ceci peut amener dans les cas critiques
  (hautes lumières,...) des points noirs dans ces zones, ou des points
  blancs,...n'hésitez pas à utiliser les outils de RT (highlight
  recovery, highlight reconstruction, impulse noise reduction,...), ou
  des zones brûlées ou noires (raw white and black point, avoid color
  shift,...)
- les grands espaces de travail (widegamut, Prophoto...) pourront amener
  dans certains cas, des zones noires alors qu'elles n'apparaîtront pas
  en sRGB (étroitesse du gamut de CIECAM).
- Les images bruitées vont influer CIECAM, celui-ci pensant que les
  points colorés sont des réalités ; c'est pourquoi j'ai placé CIECAM
  après « denoise »
- le modèle CIECAM privilégie les « cônes » et prend peu en compte les «
  bâtonnets » ..ce qui revient à dire que la vision périphérique est peu
  prise en compte.
- Donc n'espérez pas avec CIECAM02 trouver un remède aux images «
  difficiles » (surexposition, saturation du capteur, etc.) ; par contre
  pour des images « normales » (ce qui est la majorité), les avancées me
  semblent plus que significatives.
- Etc.

Peut-être verra-t-on apparaître CIECAMxx qui pourrait palier les manques
de CIECAM02 ?

## Les 12 principes d'un CAM par R.Hunt

1.  The model should be as comprehensive as possible, so that it can be
    used in a variety of applications; but at this stage, only static
    states of adaptation should be included, because of the great
    complexity of dynamic effects.
2.  The model should cover a wide range of stimulus intensities, from
    very dark object colors to very bright self-luminous color. This
    means that the dynamic response function must have a maximum, and
    cannot be a simple logarithmic or power function.
3.  The model should cover a wide range of adapting intensities, from
    very low scotopic levels, such as occur in starlight, to very high
    photopic levels, such as occur in sunlight. This means that rod
    vision should be included in the model; but because many
    applications will be such that rod vision is negligible, the model
    should be usable in a mode that does not include rod vision.
4.  The model should cover a wide range of viewing conditions, including
    backgrounds of different luminance factors, and dark, dim, and
    average surrounds. It is necessary to cover the different surrounds
    because of their widespread use in projected and self-luminous
    displays.
5.  For ease of use, the spectral sensitivities of the cones should be a
    linear transformation of the CIE x , y , z or x 10 , y 10 , z 10
    functions, and the V’() function should be used for the spectral
    sensitivity of the rods. Because scotopic photometric data is often
    unknown, methods of providing approximate scotopic values should be
    provided.
6.  The model should be able to provide for any degree of adaptation
    between complete and none, for cognitive factors, and for the
    Helson- Judd effect, as options.
7.  The model should give predictions of hue (both as hue-angle, and as
    hue-quadrature), brightness, lightness, saturation, chroma, and
    colorfulness.
8.  The model should be capable of being operated in a reverse mode.
9.  The model should be no more complicated than is necessary to meet
    the above requirements.
10. Any simplified version of the model, intended for particular
    applications, should give the same predictions as the complete model
    for some specified set of conditions.
11. The model should give predictions of color appearance that are not
    appreciably worse than those given by the model that is best in each
    application.
12. A version of the model should be available for application to
    unrelated colors (those seen in dark surrounds in isolation from
    other colors).

## Quelques liens

CIECAM02 Wikipedia [1](http://en.wikipedia.org/wiki/CIECAM02)

Color Appearance Model - Fairchild
[2](http://www.cis.rit.edu/fairchild/PDFs/AppearanceLec.pdf)

Mémoire Laborie ENS Louis Lumière
[3](http://www.ens-louis-lumiere.fr/fileadmin/recherche/Laborie-photo-2007-mem.pdf)