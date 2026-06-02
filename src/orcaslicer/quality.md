# 🛠️ Onglet "Quality" (Buse 0.2 mm vs Buse 0.4 mm)

## 1. Layer height (Hauteur de couche)

C'est l'épaisseur de chaque tranche horizontale de plastique.
Plus elle est basse, plus les marches d'escalier visibles sur la figurine disparaissent, mais plus l'impression est longue.

| Paramètre (Field) | Buse 0.2 mm | Buse 0.4 mm | Explication |
|-------------------|-------------|-------------|-------------|
| **Layer height**  | 0.06 mm (Excellent) à 0.08 mm (Standard)     | 0.08 mm (Ultra) à 0.12 mm (Standard)    | Pourquoi ? Pour obtenir une bonne fusion des couches, la hauteur de couche ne doit pas dépasser 75% du diamètre de la buse. Pour les figurines, on descend volontairement très bas. 

## 2. First layer height (Hauteur de la première couche)

L'épaisseur de la toute première couche posée sur le plateau.

- Buse 0.2 mm : 0.10 mm à 0.14 mm.
- Buse 0.4 mm : 0.20 mm.



On cherche ici une valeur légèrement supérieure à la hauteur normale pour écraser correctement le plastique sur le plateau texturé et garantir l'adhérence.

| Paramètre (Field) | Buse 0.2 mm | Buse 0.4 mm | Explication |
|-------------------|-------------|-------------|-------------|
| **First layer height**  | 0.10 mm à 0.14 mm    | 0.20 mm   | Pourquoi ? Une buse de 0.2 mm qui imprime une première couche à 0.2 mm va "écraser" le plastique de manière instable, ou à l'inverse, si on met 0.06 mm, le moindre défaut de planéité fera rater l'impression.

## 3. Line width (Largeur de ligne)

C'est l'épaisseur du boudin de plastique extrudé horizontalement. OrcaSlicer permet de régler cela finement par type de ligne.
Voici les informations formatées dans un tableau Markdown propre et lisible :

| Paramètre (Field) | Buse 0.2 mm | Buse 0.4 mm | Explication                                                                                                                                       |
|-------------------|-------------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| **Default**       | 0.22 mm     | 0.42 mm     | La valeur de base. On choisit souvent un poil plus large que la buse pour que le plastique soit bien compressé.                                   |
| **First layer**   | 0.25 mm     | 0.45 mm     | Plus large pour augmenter la surface de contact avec le plateau (meilleure accroche).                                                             |
| **Outer wall**    | 0.18 mm     | 0.38 mm     | **CRITIQUE :** On sous-extrude légèrement les parois externes. Cela permet de capturer des détails extrêmement fins (pointes d'épées, nez, yeux). |
| **Inner wall**    | 0.22 mm     | 0.42 mm     | Standard, assure la solidité derrière la paroi externe.                                                                                           |
| **Top surface**   | 0.18 mm     | 0.38 mm     | Permet d'avoir un rendu du dessus (épaules, têtes) très lisse en resserrant les lignes.                                                           |

## 4. Seam (Couture de rétraction)

Chaque couche doit commencer et s'arrêter quelque part. Cela crée de petits points ou cicatrices sur la figurine.

- Seam position : À régler sur Aligned ou Back.
- Scarf seam (Optionnel/Avancé) : À Activer (Conditional ou Always).

Pourquoi ? L'option Scarf seam d'OrcaSlicer fait s'engrener les fins de couches en biseau comme une écharpe, rendant la couture presque invisible sur les formes organiques des figurines (muscles, capes). Évitez le mode Random (Aléatoire) qui transformerait votre Space Marine en victime d'une acné foudroyante.

## 5. Precision

Ce paramètre détermine avec quelle précision le logiciel découpe les courbes de la figurine en lignes de code pour l'imprimante.

- Resolution : 0.012 mm (au lieu de 0.015 mm par défaut).

Pourquoi ? Les figurines Warhammer regorgent de visages ronds, d'armures courbes et d'ornements sphériques. Augmenter légèrement la résolution (en baissant la valeur numérique) force OrcaSlicer à générer un code plus dense et précis, permettant à l'A1 Mini de suivre les courbes organiques sans faire de micro-facettes angulaires.

## 6. Ironing (Lissage)

La buse repasse sur les surfaces planes supérieures sans extruder (ou très peu) pour lisser le plastique à chaud, comme un fer à repasser.

- Ironing type : Top surfaces only (ou All top surfaces).
- Ironing flow : 10% à 15%.
- Ironing speed : 30 mm/s.

Pourquoi ? C'est magique pour les socles (bases), les boucliers ou les dessus d'épaulettes. Cela donne un fini plat et brillant. Attention : Ne pas utiliser si la figurine a des cheveux ou des textures complexes sur le dessus, cela écraserait les détails.


## 7. Wall generator (Générateur de parois)

Sélection : Arachne.

Pourquoi ? Le moteur Arachne adapte dynamiquement la largeur de la ligne selon la finesse de la géométrie. Si l'épée de votre figurine devient plus fine que 0.2 mm, Arachne va réduire le flux pour essayer de l'imprimer quand même. Le vieux mode Classic ignorerait simplement le bout de l'épée.