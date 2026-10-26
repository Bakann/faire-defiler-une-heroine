# 8. Les pieds qui glissent : le défaut le plus subtil

[← Chapitre précédent](07-le-decor.md) · [Sommaire](../README.md) · [Chapitre suivant →](09-ta-methode.md)

## Le symptôme

La séquence complète était terminée, avec 87 dessins dans leur décor. En la regardant, la DA a dit : **« les pieds glissent trop »**. Le pied posé au sol semblait patiner légèrement, comme sur de la glace.

## Pourquoi ça glisse

Deux choses bougent indépendamment l'une de l'autre :
- **l'Héroïne**, collée exactement à la position de ses dessins Flow ;
- **le sol**, qui défile selon le mouvement de caméra que Codex avait calculé à partir de l'**arche**.

Or la vidéo Flow n'est pas une vraie scène filmée : ses pieds et son décor ne sont pas parfaitement cohérents entre eux. Résultat : sous le pied posé, le papier du sol avançait **environ 6 pixels par dessin** de trop ou de pas assez.

## Deux options

Contrainte : **ne pas toucher à l'Héroïne**, dont les 87 dessins étaient validés. Il faut donc que ce soit le sol qui s'adapte.

```mermaid
flowchart TD
    P["Le pied glisse sur le sol"] --> A["Option A<br/>caler le sol sur le pied d'appui"]
    P --> B["Option B<br/>recalculer toute la caméra<br/>à partir des pieds"]
    A --> A1["Simple et rapide<br/>l'arche ne bouge pas"]
    B --> B1["Plus cohérent<br/>mais l'arche change de rythme<br/>et le logo peut toucher l'Héroïne"]
    A1 --> C["Choix de la DA : option A"]
```

**L'idée de l'option A :** on repère le point où la chaussure touche le sol (le point le plus bas de la chaussure). Pendant que le pied est posé, ce point ne doit pas bouger *par rapport au papier du sol*. On fait donc glisser la texture du sol, image par image, juste ce qu'il faut pour qu'elle suive le pied.

## Premier essai : ça marche… avec un effet secondaire

Sur les 14 premiers dessins, le glissement est tombé à **0,4 pixel**. Mais en lisant les chiffres image par image, Claude a vu un problème : aux dessins 11 à 13, le point de contact **sautait de 34 pixels sur le côté**.

Le pied ne bougeait pas. C'est le **point le plus bas** qui changeait : le talon d'abord, puis la pointe, quand le pied se déroule. Le sol suivait ce saut à la lettre et faisait une petite **embardée** de côté : 11 pixels à droite, puis 9 à gauche.

## Deuxième essai : séparer les directions

Le glissement que la DA voyait était un glissement **avant / arrière**. Aucune raison, donc, de caler aussi le mouvement de côté. Nouvelle règle :
- **avant / arrière** : calage strict sur le pied d'appui ;
- **de côté** : une courbe lisse sur toute la séquence, sans aller-retour ;
- **passage du talon à la pointe** : transition douce sur 2 à 3 dessins, au lieu de suivre le point le plus bas à la lettre.

Résultat : glissement toujours sous 1 pixel, et plus d'embardée.

![Zoom sur les pieds : production, essai 1, essai 2](../images/pieds_calage_zoom.jpg)

## Le bonus : un liseré vert repéré par Claude

En vérifiant les pieds, Claude a remarqué un **fin liseré vert-olive** tout autour de l'Héroïne, le long des jambes et des bras. C'est un reste du fond vert de l'incrustation, présent sur les 87 images.

Le contrôle automatique de Codex ne le voyait pas : il ne cherchait que du vert **franc**, alors que ce liseré était **jaune-vert**. Codex a ensuite remplacé la couleur de ces pixels de bord par celle de la peau ou de la robe voisine, sans toucher à la forme de l'Héroïne.

![Liseré vert avant / après](../images/lisere_vert.jpg)

> **Leçon :** **un contrôle automatique ne trouve que ce qu'on lui a demandé de chercher.** Si le seuil est mal choisi, il affiche « 0 défaut » alors que le défaut est bien là. Regarde toujours aussi les images en gros plan.

## Sur les 87 images : un compromis à trancher

En appliquant la méthode aux 87 dessins, Codex a rencontré un **conflit**. Pour certains pas, garder le glissement avant / arrière sous 1 pixel **obligeait** le bord du sol à bouger de plus d'1 pixel de côté. Il l'a démontré par le calcul et a posé la question : quelle règle privilégier ?

Claude a conseillé de **privilégier l'avant / arrière**, puisque c'est le défaut que la DA voyait, et la DA a suivi ce conseil.

![Glissement avant et après](../images/graphique_glissement.png)

**Résultat :**
- glissement du pied d'appui : de **5,5 px** en moyenne (12,1 au pire) à **moins de 0,6 px**, sur les 34 moments où le pied est bien posé ;
- en contrepartie, le bord du sol fait parfois de petits pas de côté, jusqu'à 4,8 pixels, loin des pieds ;
- le grain du sol glisse un peu par rapport au pied du mur, comme un tapis roulant. Sur ce papier uni, c'est presque invisible.

> **Leçon :** **on ne peut pas toujours tout avoir.** Quand deux objectifs s'opposent, il faut choisir lequel compte le plus pour le résultat, et l'écrire. Ici, la règle était : « ce que l'œil remarque passe en premier ».

## Fin de l'aventure

La DA a validé cette version. C'est la vidéo en tête du [README](../README.md).

[Chapitre suivant : à toi de jouer, la méthode →](09-ta-methode.md)
