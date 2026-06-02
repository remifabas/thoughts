# Orca Slicer

Nous allons configurer OrcaSlicer en suivant l'ordre logique de l'interface, divisé en deux grandes sections : Qualité de fabrication et Gestion des supports.

## 1. Onglet "Quality" (Qualité)

C'est le cœur du sujet pour les figurines. Nous y ajusterons :

* La hauteur de couche (Layer height) – cruciale pour faire disparaître les lignes d'impression.
* La hauteur de la première couche pour l'adhérence.
* La largeur de ligne (Line width) adaptée aux buses de 0.2 et 0.4 mm.
* Le lissage (Ironing) pour les socles ou les surfaces plates (épaulettes, boucliers).

## 2. Onglet "Strength" (Structure & Résistance)

Les figurines sont petites et fragiles. Nous configurerons :

- Le nombre de parois (Wall loops) pour donner de la rigidité aux membres et aux armes fines.
- Le taux et le motif de remplissage (Infill) pour éviter que les détails ne s'effondrent.

## 3. Onglet "Speed" (Vitesse)

Le secret des belles figurines FDM réside dans la lenteur. Nous allons :

- Réduire drastiquement les vitesses d'impression pour laisser le plastique refroidir correctement sur les micro-détails.
- Ajuster les accélérations pour éviter le ghosting (échos sur les surfaces).

## 4. Onglet "Support" (Les fondations)

Probablement l'onglet le plus critique pour Warhammer (armes levées, capes, têtes). Nous configurerons :

- Les Tree Supports (Supports en arbre), indispensables pour les figurines.
- La distance de séparation en Z (pour qu'ils s'enlèvent sans casser la figurine).
- Les motifs d'interface.

## 5. Onglet "Others" (Autres options)

- Ajustement de la bordure (Brim) pour éviter que la figurine ne se décolle du plateau en cours de route.