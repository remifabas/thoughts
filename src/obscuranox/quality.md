

Ce format intègre les valeurs pour la buse de **0.2 mm** (détail chirurgical) et la buse de **0.4 mm** (décors et monstres), avec l'activation du mode *Advanced*.

---

| Paramètre OrcaSlicer (Field)    | Configuration Buse 0.2 mm | Configuration Buse 0.4 mm | Logique et Objectif ObscuraNox                                                   |
|---------------------------------|---------------------------|---------------------------|----------------------------------------------------------------------------------|
| **Layer height**                | `0.06 mm` *(ou 0.05)*     | `0.10 mm` *(ou 0.12)*     | Fait disparaître les lignes d'impression. Cadencé pour l'écart des supports.     |
| **First layer height**          | `0.20 mm`                 | `0.20 mm`                 | **Fixe.** Écrase parfaitement le plastique pour ancrer la pièce sur le PEI.      |
| **Line width - Default**        | `0.20 mm`                 | `0.40 mm`                 | Aligné strictement sur le diamètre physique de la buse.                          |
| **Line width - First layer**    | `0.25 mm`                 | `0.45 mm`                 | Plus large pour maximiser l'adhérence de la base de la figurine.                 |
| **Line width - Outer wall**     | `0.16 mm`                 | `0.36 mm`                 | **Sous-extrusion volontaire** pour capturer les micro-détails (yeux, runes).     |
| **Line width - Inner wall**     | `0.22 mm`                 | `0.42 mm`                 | Plus épais pour assurer la rigidité derrière la paroi externe.                   |
| **Line width - Top surface**    | `0.16 mm`                 | `0.36 mm`                 | Resserré pour un fini lisse et parfait sur le dessus des crânes/épaules.         |
| **Seam position**               | `Aligned` ou `Back`       | `Aligned` ou `Back`       | Aligne les points de départ dans les coins ou à l'arrière pour les cacher.       |
| **Scarf seam**                  | `Enabled (Always)`        | `Enabled (Always)`        | Crée un fondu en biseau des couches. Indispensable sur les capes et les muscles. |
| **Wall generator**              | `Arachne`                 | `Arachne`                 | Adapte dynamiquement la largeur de ligne pour les éléments fins (épées).         |
| **Arachne filtering threshold** | `0.2`                     | `0.2`                     | Force le slicer à imprimer les géométries minuscules au lieu de les ignorer.     |
| **Slice gap closing radius**    | `0.01 mm`                 | `0.01 mm`                 | Ferme les micro-vides des fichiers STL conçus à l'origine pour la résine.        |
| **Resolution**                  | `0.008 mm`                | `0.012 mm`                | Densifie le code pour des courbes fluides et organiques sans facettes.           |
| **Elephant foot compensation**  | `0.15 mm`                 | `0.15 mm`                 | Corrige le gonflement des pieds dû à la première couche épaisse à 0.20 mm.       |

---

Souhaitez-vous que nous passions à la synthèse de l'onglet suivant selon ObscuraNox ?