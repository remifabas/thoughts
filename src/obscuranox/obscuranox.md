**ObscuraNox** (qui gère aussi la chaîne YouTube *Dungeons and Derps*) est la référence incontournable au sein de la communauté pour l'impression FDM de miniatures de haute qualité, en particulier pour l'écosystème Bambu Lab (A1, A1 Mini, X1C).

Si vous cherchez à pousser votre machine dans ses derniers retranchements pour du Warhammer, c'est vers ses profils qu'il faut vous tourner. Ses profils (notamment la **Version 2.0**) surpassent de loin les profils "High Quality" par défaut fournis par Bambu.

---

## 🚀 La philosophie d'ObscuraNox

Contrairement à d'autres créateurs qui se contentent de baisser la vitesse globale, ObscuraNox a passé des centaines d'heures à calibrer scientifiquement les interactions entre les slicers (Bambu Studio et OrcaSlicer), le flux des filaments, et la géométrie des supports en arbre.

Ses profils permettent de descendre à des hauteurs de couche extrêmes (**0.06 mm et même 0.04 mm**) sur l'A1 Mini, donnant des résultats qui se rapprochent de manière bluffante de la résine.

---

## 🛠️ Ce qui fait la force de ses réglages (V2.0)

### 1. La refonte totale des supports en arbre (*Overhauled Supports*)

C’est sa marque de fabrique. Il a configuré les Tree Supports de manière à ce qu'ils créent des branches extrêmement stables à la base, mais avec un diamètre de pointe (*Tip diameter*) ultra-précis.

* Il utilise une logique mathématique stricte pour la distance en Z : l'écart entre le support et la figurine doit toujours être un multiple exact de la hauteur de couche (ex: si vous imprimez en 0.05 mm, l'écart sera exactement de 0.15 mm). Les supports enveloppent la pièce mais se détachent comme un charme.

### 2. Le contrôle du flux et des vibrations

Ses profils brident de manière drastique les accélérations et imposent des vitesses d'impression minimales très basses (jusqu'à 10-15 mm/s) sur les couches courtes (les têtes, les pointes d'épées). Cela évite le *curling* (le plastique chaud qui rebique vers le haut) et le *stringing* (les cheveux d'ange).

### 3. L'optimisation pour OrcaSlicer

Bien que ses profils fonctionnent sur Bambu Studio, ObscuraNox recommande chaudement **OrcaSlicer**. Des options avancées spécifiques à OrcaSlicer (comme la gestion fine du diamètre des pointes de supports, le calibrage du débit ou le *Scarf Seam* pour cacher les coutures) sont au cœur de l'excellence de ses résultats.

---

## ⚠️ Les points de vigilance avec ses profils

Ses réglages sont considérés comme de la "Fformule 1" : ils exigent que tout le reste soit parfait.

* **Zéro tolérance pour l'humidité :** Si vous utilisez son profil avec un filament qui a pris l'air (non séché), vous obtiendrez énormément de cheveux d'ange (*stringing*) ou de micro-bouchons.
* **L'adhérence du plateau doit être maximale :** Comme il réduit la surface de contact de la base des supports pour qu'ils soient faciles à enlever, le moindre défaut de propreté sur votre plateau PEI de l'A1 Mini fera basculer le support à mi-impression. Nettoyage à l'eau chaude et liquide vaisselle obligatoire.
* **Le temps d'impression :** C'est de l'ultra-détail. Des impressions d'escouades ou de grosses pièces peuvent rapidement prendre des dizaines d'heures (il a documenté un projet massif ayant tourné pendant près de 400 heures).

---
