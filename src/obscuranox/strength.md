

Pour l’infanterie fine, la philosophie d’ObscuraNox dans cet onglet est simple : **rendre les figurines virtuellement pleines sur les zones critiques**. À l'échelle Warhammer (28-32mm), les membres, les lances ou les fusils sont si fins que si vous laissez du vide ou un remplissage classique à l'intérieur, la figurine cassera dès que vous retirerez les supports ou pendant une partie.

Voici le tableau récapitulatif au format Markdown, suivi des explications techniques de ses choix.

---

### 📊 Tableau Récapitulatif : Onglet "Strength" (ObscuraNox V2.0)

| Paramètre OrcaSlicer (Field) | Configuration Buse 0.2 mm | Configuration Buse 0.4 mm | Logique et Objectif ObscuraNox                                                                                      |
|------------------------------|---------------------------|---------------------------|---------------------------------------------------------------------------------------------------------------------|
| **Wall loops**               | `5`                       | `4`                       | **Crucial.** Force les armes, jambes et bras fins à être imprimés à 100% en parois solides (zéro vide).             |
| **Wall infilled surface**    | `0%`                      | `0%`                      | Désactivé. On préfère contrôler le remplissage manuellement avec la densité.                                        |
| **Print order**              | `Inner/Outer`             | `Inner/Outer`             | Imprime l'intérieur d'abord pour ancrer la paroi externe (`Outer`) avec une précision chirurgicale.                 |
| **Top shell layers**         | `9`                       | `6`                       | Compense l'extrême finesse des couches (0.06mm). Évite les trous sur le dessus des crânes.                          |
| **Top shell thickness**      | `0.54 mm`                 | `0.60 mm`                 | Épaisseur réelle minimale pour garantir un "toit" opaque et solide pour la peinture.                                |
| **Bottom shell layers**      | `7`                       | `5`                       | Assure une base lourde et plate pour stabiliser le centre de gravité de la figurine.                                |
| **Sparse infill density**    | `30%` à `40%`             | `25%` à `35%`             | Offre une assise interne dense pour soutenir les couches supérieures complexes (épaules, têtes).                    |
| **Sparse infill pattern**    | `Gyroid`                  | `Gyroid`                  | **Obligatoire.** Ne croise jamais sa propre ligne, évitant que la buse ne percute la figurine pendant l'impression. |
| **Infill/wall overlap**      | `25%`                     | `25%`                     | Augmente l'imbrication du remplissage dans les parois pour fusionner les deux structures.                           |

---

### 🧐 Les secrets techniques d'ObscuraNox sur cet onglet

#### 1. Le "Piège" des Wall Loops (Boucles de parois)

En configurant **5 parois** avec une buse de 0.2 mm, l'épaisseur de la coque totale est de $5 \times 0.20\text{ mm} = 1.0\text{ mm}$ (ou $5 \times 0.16\text{ mm} = 0.8\text{ mm}$ sur la paroi externe).
Sur un bras d'Elfe ou un fusil de Space Marine qui mesure moins de 1.5 mm d'épaisseur sur le fichier 3D, le slicer va automatiquement remplir tout l'espace uniquement avec des parois concentriques. C'est l'équivalent d'une injection plastique d'usine : la pièce devient extrêmement robuste et flexible, parfaite pour survivre au nettoyage.

#### 2. L'importance du ratio Top Shell Layers (Couches supérieures)

Si vous imprimez avec une hauteur de couche fine de **0.06 mm** (buse 0.2), mettre seulement 4 ou 5 couches supérieures comme dans les profils standards ne représente que 0.24 mm de plastique. C'est tellement fin que la lumière passe au travers et que le plastique s'affaisse entre les lignes de remplissage (phénomène de *pillowing*). En montant à **9 couches**, ObscuraNox garantit une surface lisse, dense, qui ne s'effondrera pas et qui absorbera parfaitement la peinture.

#### 3. Pourquoi le motif Gyroid est indiscutable ?

Les motifs comme le *Grid* (Grille) ou le *Cubic* font croiser les lignes de plastique sur le même plan. À chaque croisement, une micro-goutte se forme. Sur une petite figurine d'infanterie ultra-légère fixée sur des supports fins, si la buse de l'A1 Mini percute une de ces micro-gouttes à haute vitesse, la figurine se détache instantanément de ses supports et l'impression échoue. Le **Gyroid** ondule de manière fluide en trois dimensions sans jamais créer de points de collision.

---