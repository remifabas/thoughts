# 🛠️ Onglet "Support" (Buse 0.2 mm vs Buse 0.4 mm)

## 1. Basic (Configuration de base)

Enable support (Activer les supports) : Coché

- Type : Tree (Impératif. Les supports normaux/grilles sont impossibles à retirer sur une figurine sans tout casser).
- Style : Tree Slim ou Tree Hybrid.
    - Tree Slim : Utilise très peu de plastique, se retire comme un charme, parfait pour la buse 0.2 mm.
    - Tree Hybrid : Plus robuste à la base, idéal pour la buse 0.4 mm sur des pièces un peu plus lourdes.
- Support placement (Placement) : On build plate only (De préférence).

Explication : On essaie au maximum de faire partir les arbres du plateau pour éviter qu'ils ne s'appuient sur les pieds ou les jambes de la figurine, ce qui laisserait des marques. Si une zone haute (comme un bras devant le torse) est inaccessible, passez en Everywhere, mais utilisez l'outil "Support Blocker/Enforcer" pour peindre manuellement vos supports.

## 2. Filament / Distance Z (Le secret du retrait facile)

Ces réglages déterminent l'espace vide laissé entre le haut du support et la figurine. Trop proche = collé à vie. Trop loin = la figurine s'effondre.

- Top Z distance (Distance Z supérieure) :
    - Buse 0.2 mm : 0.10 mm à 0.12 mm (environ 1.5 à 2 fois la hauteur de couche).
    - Buse 0.4 mm : 0.16 mm à 0.20 mm (généralement égal à la hauteur de couche ou une couche au-dessus).
- Bottom Z distance (Distance Z inférieure) : Même valeur que le Top Z.

Explication : C'est le paramètre le plus important. Avec une buse de 0.2 mm et une couche fine (0.06 mm), un écart de 0.12 mm permet au plastique de se poser délicatement sur le support sans fusionner avec lui. Les supports se détacheront d'un simple coup de pince.

## 3. Interface (La surface de contact)

L'interface est le petit "coussin" de plastique dense construit tout en haut de l'arbre, juste avant de toucher la figurine.

- Top interface layers (Couches d'interface supérieures) : 3

Interface pattern (Motif d'interface) : Grid (Grille) ou Concentric (Concentrique).

- Top interface spacing (Espacement de l'interface) :
    - Buse 0.2 mm : 0.4 mm
    - Buse 0.4 mm : 0.6 mm

Explication : En créant une grille dense à 3 couches sous la figurine, on s'assure que le dessous des bras ou des capes soit parfaitement lisse et plat, plutôt que flasque ou "gribouillé".

## 4. Tree Support Settings (Géométrie des arbres)

Pour éviter que les branches de l'arbre ne soient trop épaisses et n'englobent toute la figurine.

Tree branch diameter (Diamètre des branches) :
    Buse 0.2 mm : 1.5 mm à 2.0 mm (les branches seront très fines et précises).
    Buse 0.4 mm : 2.5 mm à 3.0 mm.

Tree branch angle (Angle des branches) : 45° (permet aux arbres de contourner la figurine avec de belles courbes pour aller chercher les détails).

Voici le tableau récapitulatif pour les paramètres de support au format Markdown :

| Paramètre (Field)        | Buse 0.2 mm | Buse 0.4 mm   | Objectif principal                              |
|--------------------------|-------------|---------------|-------------------------------------------------|
| **Type / Style**         | Tree (Slim) | Tree (Hybrid) | Supports organiques faciles à détacher.         |
| **Top Z distance**       | 0.12 mm     | 0.18 mm       | Permet de détacher le support sans outil lourd. |
| **Top interface layers** | 3           | 3             | Assure un dessous de pièce propre et net.       |
| **Branch diameter**      | 1.8 mm      | 2.8 mm        | Évite que le support ne noie la figurine.       |
