Nous arrivons sur l'onglet **Speed** (Vitesse) selon la logique **ObscuraNox (V2.0)**.

La philosophie d'ObscuraNox ici est radicale : **l'A1 Mini est une machine ultra-rapide, mais pour des miniatures de 32 mm, la vitesse détruit le détail**. Plus la buse va vite, plus elle tire sur le plastique chaud, ce qui arrondit les angles (nez, doigts, épées) et crée des vibrations (*ghosting*). Son profil applique un freinage ciblé sur les parois visibles tout en optimisant le temps sur les structures cachées.

Voici le tableau récapitulatif au format Markdown pour les buses de **0.2 mm** et **0.4 mm**.

---

### 📊 Tableau Récapitulatif : Onglet "Speed" (ObscuraNox V2.0)

| Paramètre OrcaSlicer (Field) | Configuration Buse 0.2 mm | Configuration Buse 0.4 mm | Logique et Objectif ObscuraNox                                                                                        |
|------------------------------|---------------------------|---------------------------|-----------------------------------------------------------------------------------------------------------------------|
| **Outer wall**               | **`20 - 30 mm/s`**        | **`35 - 45 mm/s`**        | **CRITIQUE.** Vitesse extrêmement basse pour laisser le plastique figer précisément sur les micro-détails extérieurs. |
| **Inner wall**               | `50 - 65 mm/s`            | `70 - 90 mm/s`            | On accélère pour les parois internes cachées afin de maintenir un temps d'impression raisonnable.                     |
| **Top surface**              | **`25 - 35 mm/s`**        | **`40 - 50 mm/s`**        | Lent pour maximiser la netteté et la planéité du dessus des crânes, des épaules et des socles.                        |
| **Sparse infill**            | `70 - 90 mm/s`            | `90 - 120 mm/s`           | Le remplissage Gyroid encaisse très bien la vitesse sans impacter l'aspect visuel extérieur.                          |
| **First layer**              | **`15 mm/s`**             | **`20 mm/s`**             | Sécurité totale. Le plastique doit littéralement ramper pour fusionner parfaitement avec le plateau PEI.              |
| **First layer infill**       | `20 mm/s`                 | `25 mm/s`                 | Lent pour garantir une base de socle parfaitement pleine et lourde.                                                   |
| **Travel speed**             | `150 mm/s`                | `180 mm/s`                | Brise la vitesse par défaut (500 mm/s). Évite que le déplacement d'air ou une micro-secousse ne décroche la figurine. |
| **Normal acceleration**      | `1500 mm/s²`              | `2000 mm/s²`              | Réduit l'inertie globale de la tête d'impression de l'A1 Mini pour stabiliser les couches fines.                      |
| **Outer wall acceleration**  | **`500 mm/s²`**           | **`800 mm/s²`**           | Supprime totalement le *ghosting* (vagues fantômes) sur les surfaces lisses (capes, armures).                         |

---

### 🧐 Les secrets techniques d'ObscuraNox sur la vitesse

#### 1. Le contrôle thermique sur les pointes (*Small Layers*)

Bien que les chiffres du tableau soient bas, ObscuraNox rappelle souvent que c'est le paramètre **"Min print speed"** (dans l'onglet *Filament / Cooling*) qui va sauver le haut de vos figurines. Quand la buse arrive sur la tête d'un Elfe ou la pointe d'une lance, la couche s'imprime en moins d'une seconde. Le profil force alors la machine à ralentir jusqu'à **10 mm/s** pour que le ventilateur de l'A1 Mini souffle en continu sur le plastique et le fige avant que la couche suivante n'arrive. Sans cela, la tête de la figurine fondrait sous la chaleur résiduelle de la buse.

#### 2. L'importance capitale des accélérations basses

L'A1 Mini utilise un système "Bed Slinger" (le plateau bouge d'avant en arrière). Si la machine change de direction avec une accélération d'origine à 5000 mm/s², la figurine (qui ne tient que par de fins supports en arbre) va subir des micro-fouettements. En bridant l'accélération de la paroi extérieure à **500 mm/s²**, la tête ralentit en douceur avant chaque virage. Les arrêtes des épées restent tranchantes et les visages parfaitement nets.

---