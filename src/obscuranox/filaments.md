Pour clore magistralement le profil **ObscuraNox (V2.0)** sur OrcaSlicer, il reste **trois ajustements avancés** indispensables. Ils ne sont pas dans les onglets classiques de découpe, mais touchent aux réglages du filament et à la machine elle-même.

Sans eux, la finesse que nous avons configurée dans les onglets précédents risque de générer des cheveux d'ange (*stringing*) ou des variations de pression dans la buse de 0.2 mm.

---

### 1. L'onglet "Filament" : Le Flow Ratio (Débit) et le Pressure Advance

ObscuraNox insiste lourdement là-dessus : les profils génériques ont tendance à sur-extruder légèrement pour garantir des pièces solides. Sur de l'infanterie fine, cela gomme les détails (les yeux se bouchent, les doigts fusionnent).

* **Flow Ratio (Multiplicateur de débit) :** À baisser entre **`0.94`** et **`0.96`** (au lieu de 0.98 ou 1.0 par défaut).
* *Pourquoi ?* Cela crée une très légère sous-extrusion contrôlée. Associé à la largeur de ligne de 0.16 mm que nous avons vue, cela donne des détails d'une netteté absolue.


* **Pressure Advance (Avance de pression) :** À activer et calibrer précisément (généralement autour de **`0.025` à `0.035**` pour du PLA Matte sur l'A1 Mini).
* *Pourquoi ?* Cela gère la pression du plastique dans la buse lors des accélérations/décélérations. C'est ce qui évite d'avoir des petits "blobs" (gouttes) de plastique au bout des épées ou sur la pointe des nez.



---

### 2. L'onglet "Filament -> Cooling" (Le refroidissement chirurgical)

Nous en avons parlé rapidement, mais voici les valeurs exactes recommandées pour maintenir la tête des figurines bien nette :

* **No cooling thresholds - Layer time :** **`30 seconds`**
* **Max fan speed threshold - Layer time :** **`15 seconds`**
* **Minimum print speed :** **`10 mm/s`**
* *La logique ObscuraNox :* Dès qu'une couche de la figurine met moins de 15 secondes à s'imprimer (comme le haut du crâne), le ventilateur de l'A1 Mini est propulsé à 100% et la machine ralentit dynamiquement jusqu'à atteindre un plancher de 10 mm/s. Le plastique est "gelé" instantanément, empêchant les couches de s'affaisser les unes sur les autres.



---

### 3. La configuration "Machine" (Le Z-Hop alternatif)

Le **Z-Hop** est le petit mouvement où la buse se lève verticalement pendant qu'elle se déplace pour ne pas percuter la figurine. Le Z-Hop par défaut de Bambu Lab (mode *Triangle* ou *Auto*) peut créer des fils très fins (cheveux d'ange) difficiles à nettoyer sur de l'infanterie.

* **Z-hop type :** À passer en **`Normal`** ou **`Slope`** (Pente).
* **Z-hop height :** **`0.2 mm`** (pour la buse 0.2) et **`0.4 mm`** (pour la buse 0.4).
* *Pourquoi ?* Le mode *Slope* ou *Normal* combiné à une rétraction propre coupe net le fil de plastique avant le déplacement. Vous réduisez de 90% le travail d'ébarbage après l'impression.



---

### 🛠️ Le Processus Final recommandé par ObscuraNox

Avant de lancer votre première impression d'infanterie fine (avec votre PolyTerra Gris fraichement configuré), ObscuraNox conseille toujours de passer par les **outils de calibration intégrés d'OrcaSlicer** (Menu *Calibration* tout en haut) :

1. Faire le test de **Flow Rate** (pour bloquer votre débit parfait).
2. Faire le test de **Pressure Advance**.

Une fois ces deux valeurs reportées dans votre profil de filament PolyTerra, et combinées avec tous les tableaux Markdown (Quality, Strength, Speed, Support) que nous avons bâtis, vous aurez entre les mains l'équivalent d'un **profil professionnel de compétition** pour votre A1 Mini.

Prêt à faire chauffer la buse de 0.2 mm et à importer votre premier fichier STL ?