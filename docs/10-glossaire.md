# 10. Petit glossaire

[← Chapitre précédent](09-ta-methode.md) · [Sommaire](../README.md)

**Agent de code** : une IA qui ne se contente pas de répondre. Elle écrit des programmes, les lance, lit des fichiers et en crée. Codex est un agent de code.

**Alpha (transparence)** : une information ajoutée à chaque pixel, qui dit s'il est opaque, transparent ou entre les deux. Elle permet de poser l'Héroïne sur n'importe quel décor.

**Amplitude** : l'importance maximale d'un mouvement autour de sa position de repos. Par exemple, l'ourlet qui s'incline jusqu'à 30° d'un côté puis de l'autre.

**Brief** : le document de consignes donné à une IA (ou à une personne) avant un travail. Ici, des fichiers `BRIEF_*.md`.

**Cadrage** : la portion de la scène visible dans l'image. Garder le même cadrage, c'est conserver les marges et la taille du sujet dans le cadre.

**Calage** : faire en sorte que deux éléments bougent ensemble. Ici, le sol est calé sur le pied d'appui pour que le pied ne glisse pas.

**Compenser le mouvement de caméra** : recaler deux images pour comparer ce qui change vraiment dans la scène, sans confondre ce changement avec le déplacement dû à la caméra.

**Crédits** : la « monnaie » de certains outils d'IA. Chaque génération en consomme.

**Cycle de marche (foulée)** : deux pas consécutifs. Après un cycle, le mouvement recommence.

**Décalage (du décor)** : ici, déplacer tout le décor vers la droite (360 pixels dans l'export 1 080 × 1 920) pour que le monogramme soit visible à côté de l'Héroïne.

**Despill** : retirer la couleur du fond vert qui a « déteint » sur les bords d'un personnage incrusté.

**Dessins par seconde** : le nombre de dessins différents utilisés par seconde. L'animation finale en a 12, chacun montré deux fois dans une vidéo à 24 images par seconde.

**ffmpeg** : un logiciel gratuit en ligne de commande pour découper, convertir, accélérer et assembler des vidéos.

**Fond vert (incrustation)** : on fabrique un personnage devant un fond vert uni, puis l'ordinateur retire ce vert pour le poser sur un autre décor. C'est la technique de la météo à la télévision.

**Génération** : la fabrication d'une image ou d'une vidéo par une IA. Chaque génération est un peu différente, même avec la même consigne.

**Guide au trait** : un schéma simplifié (contours, squelette, repères) qui indique la pose à l'IA de dessin sans lui montrer la photo d'origine.

**Images par seconde (i/s)** : le nombre d'images affichées chaque seconde par une vidéo ; certaines peuvent être identiques. La vidéo du défilé en a 25 ; la vidéo finale en a 24.

**JSON** : un fichier texte qui range des données, par exemple les coordonnées des articulations et l'angle de la robe pour chaque dessin.

**Kirigami** : art japonais du papier découpé et plié.

**Liseré** : une fine bordure de couleur indésirable autour d'un objet découpé.

**MediaPipe** : un outil gratuit de Google qui repère automatiquement le squelette d'une personne (épaules, coudes, hanches, genoux…) sur une image.

**Monogramme** : un logo fait de lettres entrelacées. Celui de la Maison est masqué par un cache gris dans ce dépôt.

**Noms de code (pseudonymes)** : des noms inventés qui remplacent les vrais noms de marques ou de personnages dans un document public.

**Ourlet** : le bas de la robe. Ici, une bande jaune très facile à repérer, qui a servi de repère pour mesurer la marche.

**Pied d'appui** : le pied posé au sol, qui porte le poids du corps pendant un pas.

**Pixel (px)** : un point d'une image numérique. Une image 1080 × 1920 fait 1 080 pixels de large et 1 920 de haut.

**Plaque (de décor)** : une grande image du décor, fabriquée une seule fois, puis déplacée et réduite pour imiter un mouvement de caméra.

**Planche-contact** : une seule image qui regroupe beaucoup de petites images, pour tout voir d'un coup.

**Prompt** : le texte qu'on écrit à une IA pour lui demander quelque chose.

**Référence (image ou vidéo de référence)** : un fichier donné à l'IA comme modèle. Il faut toujours préciser son rôle : pose, apparence, mouvement, style…

**Scintillement** : quand un élément qui devrait rester fixe change légèrement d'une image à l'autre, ce qui fait trembler l'animation.

**Seuil** : la valeur limite d'un contrôle (voir aussi « tolérance »). Par exemple, « l'ourlet doit être à moins de 5° de la référence ».

**Squelette** : les points des articulations d'une personne (épaules, coudes, poignets, hanches, genoux, chevilles), reliés par des traits.

**Synchroniser** : faire correspondre les images qui représentent le même instant, grâce à leur numéro ou à leur temps.

**Texture** : les petits détails d'une surface, comme le grain du papier. On peut animer séparément la forme d'un objet et sa texture.

**Tolérance** : l'écart maximal qu'on décide d'accepter pour une mesure ; voir aussi « seuil ».

**Transition** : le passage d'un dessin au suivant. 87 dessins donnent 86 transitions.

**Travelling arrière** : un mouvement de caméra qui recule. Ici, la caméra recule pendant que l'Héroïne avance.

**Version (v1, v2…)** : chaque nouvelle tentative, gardée à côté des précédentes au lieu de les écraser.

[← Retour au sommaire](../README.md)
