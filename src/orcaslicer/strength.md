# Orca Slicer

## 🛠️ Onglet "Strength" (Buse 0.2 mm vs Buse 0.4 mm)

## 1. Walls (Parois)

Ce paramètre définit le nombre de lignes de plastique qui forment la "coque" extérieure de la figurine avant de commencer à remplir l'intérieur.

- Wall loops (Nombre de contours) :
    - Buse 0.2 mm : 4 à 5
    - Buse 0.4 mm : 3 à 4

Explication : Pour les figurines, on veut que les parties fines (les bras, les épées, les lances) soient 100% pleines de parois. Si vous mettez seulement 2 parois avec une buse de 0.2 mm, l'épaisseur de la coque ne fera que 0.4mm, rendant l'arme cassante comme du verre. Augmenter le nombre de parois force OrcaSlicer à remplir entièrement ces petits membres avec des lignes continues, ce qui décuple leur solidité.

- Print order (Ordre d'impression) :
    - Réglage : Inner/Outer/Inner ou Inner/Outer

Explication : Imprimer les parois intérieures avant la paroi extérieure (Outer) garantit une meilleure précision dimensionnelle et évite que le plastique de la surface visible ne "bave" vers l'extérieur. C'est essentiel pour la netteté des détails du visage ou des armures.

## 2. Top/Bottom shells (Surfaces supérieures et inférieures)

Ce sont les "couvercles" et les "planchers" de vos volumes fermés.

- Top shell layers (Couches supérieures) :
    - Buse 0.2 mm : 7 à 9
    - Buse 0.4 mm : 5 à 6

- Bottom shell layers (Couches inférieures) :
    - Buse 0.2 mm : 6
    - Buse 0.4 mm : 4

Explication : Vu que nos hauteurs de couches sont extrêmement fines (ex: 0.06 mm avec la buse 0.2), il faut empiler beaucoup de couches pour obtenir une épaisseur réelle suffisante (9 couches de 0.06 mm font à peine 0.54 mm de plastique). Si vous n'en mettez pas assez, vous verrez des trous apparaître sur le dessus des crânes ou des épaules des figurines (phénomène de pillowing).

## 3. Infill (Remplissage)

Le remplissage structure l'intérieur des zones épaisses (le torse, les grosses montures, les socles).

- Sparse infill density (Densité de remplissage) :
    - Réglage : 25% à 40%

Explication : Contrairement aux grosses pièces mécaniques où 15% suffisent, les figurines ont besoin d'un taux plus élevé pour offrir une base solide sur laquelle les couches supérieures (comme les épaules) vont pouvoir se poser sans s'effondrer.

- Sparse infill pattern (Motif de remplissage) :
    - Réglage : Gyroid (Géroïde) ou Adaptive Cubic (Cubique adaptatif)

Explication : Le motif Gyroid est le grand favori. Il change de direction à chaque couche sans jamais se croiser sur le même plan, ce qui évite que la buse ne vienne percuter le remplissage pendant les déplacements rapides (ce qui ferait bouger la figurine et rater l'impression). L'Adaptive Cubic, quant à lui, réduit la densité au cœur de la figurine et l'augmente près des parois, ce qui est excellent pour gagner du temps sur les grosses figurines (monstres, tanks).



Voici le tableau récapitulatif pour les paramètres de solidité ("Strength") au format Markdown :

| Paramètre (Field)       | Buse 0.2 mm | Buse 0.4 mm | Objectif principal                           |   |
|-------------------------|-------------|-------------|----------------------------------------------|---|
| **Wall loops**          | 4 ou 5      | 3 ou 4      | Solidité des armes et membres fins.          |   |
| **Print order**         | Inner/Outer | Inner/Outer | Précision des détails extérieurs.            |   |
| **Top shell layers**    | 8           | 6           | Éviter les trous sur le haut de la figurine. |   |
| **Bottom shell layers** | 6           | 4           | Assurer une base plate et solide.            |   |
| **Infill density**      | 30%         | 25%         | Support interne suffisant pour les détails.  |   |
| **Infill pattern**      | Gyroid      | Gyroid      | Éviter les collisions de la buse.            | . |