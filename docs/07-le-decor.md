# 7. Le décor : six problèmes, six solutions

[← Chapitre précédent](06-heroine-en-kirigami.md) · [Sommaire](../README.md) · [Chapitre suivant →](08-les-pieds-qui-glissent.md)

C'est l'étape qui a demandé le plus de versions : cinq en tout. Chaque problème est raconté ici avec sa solution. Ils sont regroupés par thème, pas tout à fait dans l'ordre où ils sont arrivés. Dans l'ordre réel : décor redessiné image par image, puis plaque unique (versions 1 à 3, avec la porte, la forme du bloc et le liseré crème), aperçus sans boucle, et enfin sol élargi (version 4).

## Le point de départ : une vidéo de décor vide

La DA a fourni deux photos du vrai décor : une arche couverte d'orchidées blanches et le monogramme de la Maison au milieu. Claude a découpé dans ces photos uniquement le décor, sans la mannequin ni la mention de l'agence photo, puis a demandé à Flow :

> *Une vidéo de ce décor de défilé **vide**, sans personne. La caméra recule doucement au rythme d'une marche, comme si elle suivait une mannequin qui avance vers elle.*

Flow a produit 8 secondes de travelling arrière, avec l'arche qui rapetisse et le sol qui défile. Claude en a extrait **87 images**, synchronisées avec les 87 dessins de l'Héroïne.

Un défaut : à partir de 5 secondes, Flow a ajouté **des jambes de spectateurs** au bord de l'image, et un projecteur en haut. Il faudra les effacer.

## Problème 1 : le décor qui scintille

Première idée : faire redessiner chaque image du décor en kirigami par GPT Image, comme pour l'Héroïne. Le résultat était joli image par image, mais **en animation, le décor tremblait** : à chaque image, les fleurs changeaient de forme et de place.

![Deux images consécutives du décor redessiné](../images/decor_scintillement.jpg)

Codex a **mesuré** ce scintillement : l'écart moyen de luminosité de la zone de l'arche entre deux images voisines, une fois le mouvement de la caméra [compensé](10-glossaire.md). La mesure porte sur l'essai de 14 images, soit 13 transitions.

![Mesure du scintillement](../images/graphique_scintillement.png)

Le décor redessiné changeait **5,6 fois plus** que la vidéo Flow d'origine.

**Pourquoi :** chaque génération est indépendante. L'IA ne se souvient pas de la position exacte de chaque fleur dans l'image précédente.

**Solution (proposée par Codex) :** ne dessiner le décor **qu'une seule fois**, sous forme d'une grande **plaque** en haute définition, puis la **déplacer et la réduire** image par image pour imiter le recul de la caméra. Les fleurs ne sont plus régénérées, et l'écart mesuré tombe à **1,01 %**, encore moins que la vidéo Flow. Il n'est pas nul : de petites différences de rendu subsistent. (Le sol, lui, est une seconde plaque, animée en perspective.)

> **Leçon :** **un élément fixe dans la scène n'a pas besoin d'être régénéré à chaque dessin.** Une IA de génération recrée tout à chaque fois. On peut fabriquer l'élément une fois, sous forme de plaque, puis animer sa position et sa taille avec un programme.

## Problème 2 : le logo caché derrière l'Héroïne

Le monogramme de la Maison est au centre de l'arche… exactement derrière l'Héroïne, qui en cachait 70 à 85 %. Or sur la vidéo du défilé, on le voyait bien à côté de la mannequin.

**Solution :** décaler **tout le décor** vers la droite, sans bouger l'Héroïne : 360 pixels dans l'export 1 080 × 1 920, soit 240 pixels dans les images de travail 720 × 1 280. Le monogramme passe alors à sa droite. Codex vérifie sur chaque image qu'il n'est **jamais caché** : la marge minimale mesurée est de 43 pixels dans l'export, pour un seuil fixé à 22,5.

![Logo caché, puis visible (masqué ici par un cache gris)](../images/logo_decale.jpg)

## Problème 3 : une porte sortie de nulle part

En décalant le décor, il fallait inventer la partie gauche, qui n'existait pas dans la vidéo Flow. Claude a écrit dans le brief : *« mur, coulisse noire et suite du podium »*. Codex a pris « coulisse noire » au pied de la lettre et a dessiné **une porte noire isolée** au milieu du mur (image A ci-dessous).

**Solution :** Claude a reconnu son erreur, corrigé le brief (« un simple prolongement du mur, sans porte ni ouverture ») et Codex a retiré la porte.

> **Leçon :** **chaque mot d'une consigne compte.** Décris d'abord ce qui doit être visible, par exemple « un mur blanc continu jusqu'au sol ». Une interdiction ciblée (« sans porte ni ouverture ») peut compléter la consigne, mais seul un essai vérifié montre si elle a été comprise.

## Problème 4 : un décor qui ne ressemble pas au vrai

La DA a fourni deux nouvelles photos du décor, prises de plus loin. On y voyait que l'arche était posée dans un **bloc de murs blancs**, avec des **rideaux bleu nuit** de chaque côté. Codex a fait une nouvelle plaque… et la DA a répondu : **« ça ne ressemble pas du tout aux deux images »**.

![Les plaques successives](../images/plaques_decor.jpg)

En comparant, Claude a vu que l'image montrée était un **brouillon** (B) que Codex avait déjà écarté. Mais la plaque retenue (C) n'était pas juste non plus : le bloc avait une forme de **cheminée**, le mur au-dessus de l'arche était trop haut, et la couleur trop crème.

**Solution :** au lieu de redécrire le décor avec des mots, Claude a **mesuré les proportions** sur les photos : largeur du bloc par rapport à l'arche, hauteur du mur, position des panneaux. Il a ensuite dessiné un **guide de disposition**, un simple schéma en aplats avec l'arche au bon endroit. Codex a reconstruit la plaque en suivant ce schéma (D).

![Guide de disposition mesuré](../images/guide_disposition.jpg)

> **Leçon :** **un schéma vaut mieux qu'un long texte.** Pour une question de proportions, donne des mesures et un dessin, pas des adjectifs.

## Problème 5 : les finitions, liseré crème et triangle noir

En regardant de près, deux défauts restaient :

**Un liseré crème autour des fleurs.** Les fleurs avaient été découpées dans l'ancienne version, au fond crème, et en gardaient un contour, comme un autocollant sur le mur blanc. Codex l'a remplacé par le papier du mur. Dans une bande de 12 pixels autour du contour extérieur de l'arche, le nombre de pixels crème est passé de 6 480 à **0**. Les fleurs, les feuilles et l'ouverture éclairée étaient exclues de ce comptage.

![Liseré crème avant / après](../images/lisere_creme.jpg)

**Un triangle noir sur le sol**, repéré par la DA. Le podium de Flow était plus étroit que l'image et laissait voir la salle sombre. Codex a élargi le sol pour qu'il couvre toute la largeur, sur les 87 positions de la caméra.

![Triangle noir avant / après](../images/triangle_noir.jpg)

## Problème 6 : le décor qui « revient en arrière »

En regardant l'essai en boucle, la DA a vu le décor **reculer, puis revenir d'un coup** à sa position de départ.

Ce n'était pas un défaut des images. La caméra recule pendant tout le plan sans jamais revenir, donc quand l'aperçu reprend au début, l'arche retrouve d'un coup sa taille. Deux options :
1. **un plan continu** de 7,25 secondes, sans boucle, qui garde le recul de la caméra ;
2. **une boucle parfaite** avec un décor immobile, mais il faudrait alors refaire l'Héroïne sur une seule foulée répétée.

La DA a choisi le **plan continu**, et plus aucun aperçu ne boucle.

## Une erreur de plus de Claude

Pendant la fabrication du sol, Codex a posé une question : *« Le sol de Flow remonte d'environ 5 pixels par dessin, alors que le brief demande un défilement vers le bas. Lequel retenir ? »*

C'est Codex qui avait raison. Quand la caméra recule, le sol **s'éloigne et remonte** vers l'horizon. Claude s'était trompé de sens dans le brief.

> **Leçon :** **encourage les IA à poser des questions** quand une consigne contredit ce qu'elles observent. Une IA qui obéit aveuglément aurait fabriqué un sol qui défile à l'envers.

[Chapitre suivant : les pieds qui glissent →](08-les-pieds-qui-glissent.md)
