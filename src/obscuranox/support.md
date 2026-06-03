Nous arrivons sur l’onglet le plus célèbre et le plus copié des profils **ObscuraNox (V2.0)** : l'onglet **Support**.

C'est ici qu'il applique sa fameuse règle de **synchronisation mathématique** entre la hauteur de couche (onglet *Quality*) et l'espace vide sous la figurine. Son objectif est d'obtenir des supports en arbre stables qui enveloppent parfaitement l'infanterie fine, mais qui se détachent d'un simple coup de pince, laissant un dessous de pièce ultra-propre (sans l'effet "spaghetti" habituel du FDM).

Voici le tableau récapitulatif complet au format Markdown pour les deux buses.

---

### 📊 Tableau Récapitulatif : Onglet "Support" (ObscuraNox V2.0)

| Paramètre OrcaSlicer (Field) | Configuration Buse 0.2 mm | Configuration Buse 0.4 mm | Logique et Objectif ObscuraNox                                                                    |
|------------------------------|---------------------------|---------------------------|---------------------------------------------------------------------------------------------------|
| **Enable support**           | `Coché`                   | `Coché`                   | Indispensable pour l'infanterie fine (armes, capes, mentons).                                     |
| **Type**                     | `Tree`                    | `Tree`                    | Les supports en arbre sont obligatoires pour contourner la figurine.                              |
| **Style**                    | `Tree Slim`               | `Tree Strong` / `Organic` | *Slim* pour la buse 0.2 (évite de noyer la pièce). *Strong* pour la buse 0.4 (stabilité).         |
| **Support placement**        | `Everywhere`              | `Everywhere`              | Permet d'aller soutenir les détails hauts (mains, visages) depuis le corps si besoin.             |
| **Top Z distance**           | **`0.12 mm`**             | **`0.20 mm`**             | **CRITIQUE.** Aligné sur la hauteur de couche. Permet un décollage propre sans fusionner.         |
| **Bottom Z distance**        | `0.12 mm`                 | `0.20 mm`                 | Même valeur que le Top Z pour protéger les zones basses de la figurine.                           |
| **Base pattern spacing**     | `2.0 mm`                  | `2.5 mm`                  | Espacement de la structure interne des branches pour économiser du plastique.                     |
| **Top interface layers**     | `3`                       | `3`                       | Crée un "plafond" dense à 3 couches pour que la figurine repose sur un lit plat.                  |
| **Interface pattern**        | `Grid`                    | `Grid`                    | La grille offre le support le plus homogène pour les formes organiques.                           |
| **Top interface spacing**    | **`0.20 mm`**             | **`0.40 mm`**             | **Resserré.** Évite que les micro-membres (doigts, pointes) ne tombent dans les trous du support. |
| **Tree branch diameter**     | **`1.2 mm`**              | **`2.5 mm`**              | Des branches très fines pour la buse 0.2 mm pour un retrait chirurgical.                          |
| **Tree branch angle**        | `45°`                     | `45°`                     | Donne de la souplesse aux branches pour slalomer autour des membres.                              |
| **Support wall loops**       | **`1`**                   | **`1`**                   | **Crucial.** Une seule paroi rend la branche facile à écraser et casser lors du nettoyage.        |

---

### 🧐 Les secrets mathématiques d'ObscuraNox sur les supports

#### 1. La formule magique de la "Top Z distance"

C'est le cœur de sa méthodologie. La distance Z doit être un **multiple exact** de votre hauteur de couche.

* Avec sa configuration à **0.06 mm** de hauteur de couche (buse 0.2), il règle le Top Z sur **0.12 mm** (soit exactement 2 couches vides). Le plastique se dépose délicatement sans coller.
* Si vous décidiez d'imprimer en **0.05 mm**, vous devriez régler ce paramètre sur **0.10 mm** (2 couches vides) ou **0.15 mm** (3 couches vides). Ne laissez jamais une valeur qui n'est pas un multiple exact, sinon le slicer va arrondir et créer des imperfections.

#### 2. Pourquoi le "Top interface spacing" à 0.20 mm change tout ?

Sur les profils standards, l'espacement de l'interface est souvent de 0.5 mm ou plus. Pour une buse de 0.2 mm qui imprime un bras de 0.8 mm d'épaisseur, le bras va "tomber" entre les lignes du support et pendre dans le vide. En resserrant l'interface à **0.20 mm**, ObscuraNox crée un plateau quasi-plein. Le dessous des capes et des aisselles ressort lisse, limitant le travail de ponçage avant la peinture.

#### 3. Support Wall Loops réglé sur 1

Par défaut, les logiciels mettent 2 parois sur les supports pour qu'ils soient solides. ObscuraNox force la valeur à **1**. Associé au style *Tree Slim*, cela donne des branches qui ressemblent à des pailles très fines. Elles ont assez de force verticale pour porter le poids d'un bras en plastique, mais aucune résistance latérale : il vous suffit de pincer le support avec vos doigts pour qu'il s'effondre et libère la figurine sans aucun effort.

---

Prêt à finir cette numérisation de profil avec le dernier onglet, **Others** (Brim de sécurité pour stabiliser ces arbres très fins) ?