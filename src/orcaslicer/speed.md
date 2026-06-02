# 🛠️ Onglet "Speed" (Buse 0.2 mm vs Buse 0.4 mm)

## 1. First Layer Speed (Vitesse de la première couche)

La stabilité de la figurine dépend entièrement de sa base pendant les heures d'impression.

| Paramètre (Field) | Buse 0.2 mm | Buse 0.4 mm | Explication |
|-------------------|-------------|-------------|-------------|
| **First layer**  |  15 - 20 mm/s     | 20 - 25 mm/s    | On veut que le plastique "rampe" et s'écrase parfaitement sur le plateau texturé. À cette vitesse, le taux d'échec au démarrage est proche de zéro.
| **First layer infill**  |  25 - 30 mm/s   | 25 - 30 mm/s   | Remplissage de première couche


## 2. Other layers speed

Pour les figurines, on applique la règle d'or : diviser les vitesses d'origine de la machine par deux, voire par trois.

Voici le second tableau au format Markdown, reprenant la même structure que le premier pour vos paramètres de vitesse :

| Paramètre (Field) | Buse 0.2 mm  | Buse 0.4 mm   | Explication                                                                                                                                                       |
|-------------------|--------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Outer wall**    | 25 - 35 mm/s | 40 - 50 mm/s  | **CRITIQUE :** La paroi extérieure doit être imprimée le plus lentement possible pour maximiser la netteté des micro-détails (visage, runes, textures d'armures). |
| **Inner wall**    | 45 - 60 mm/s | 60 - 80 mm/s  | On peut aller un peu plus vite car ces parois sont cachées à l'intérieur, mais pas trop pour ne pas bousculer la figurine.                                        |
| **Top surface**   | 25 - 35 mm/s | 40 - 50 mm/s  | Lent pour garantir une finition lisse et impeccable sur le dessus des crânes, épaules, etc.                                                                       |
| **Sparse infill** | 60 - 80 mm/s | 80 - 100 mm/s | Le remplissage peut être plus rapide pour gagner du temps, le Gyroid gère très bien ces vitesses.                                                                 |

## 3. Travel Speed (Vitesse de déplacement à vide)

C'est la vitesse à laquelle la tête se déplace sans imprimer, lorsqu'elle change de zone.

* Travel speed : 150 - 200 mm/s (L'A1 Mini peut monter à 500 mm/s, mais réduisez-la).

Explication : Lorsque la tête se déplace très vite entre deux figurines ou entre les supports et la figurine, le courant d'air et les vibrations peuvent secouer ou décoller une petite pièce fragile. Une vitesse modérée sécurise l'impression.

## 4. Acceleration (Accélération)

L'A1 Mini a des moteurs puissants qui accélèrent fort. Sur une figurine fine, une accélération trop brutale crée du ghosting (des échos ou vagues fantômes sur les surfaces lisses) ou peut simplement casser la figurine à la base en changeant de direction trop vite.

* Normal printing (Impression normale) : Réduire à 1500 - 2000 mm/s² (au lieu de 5000+ par défaut).
* Outer wall (Paroi extérieure) : Réduire à 500 - 800 mm/s².

| Paramètre (Field) | Valeur | Explication |
|-------------------|--------|-------------|
| **Acceleration Normal printing**  |  Réduire à 1500 - 2000 mm/s²    | au lieu de 5000+ par défaut.
| **Outer wall**  |  Réduire à 500 - 800 mm/s².   | En limitant l'accélération sur la paroi externe, la buse prend ses virages en douceur. Les détails des petites pièces restent nets, angulaires et sans bavure.


💡 Le Conseil Pro ( Cooling / Refroidissement ) :
Bien que ce soit dans l'onglet Filament (et non Speed), gardez en tête que le paramètre Min print speed (Vitesse d'impression minimale sous l'action du ventilateur) va souvent brider votre vitesse à 10 ou 15 mm/s sur les pointes d'épées ou les têtes. C'est normal et souhaitable ! Cela laisse le temps au ventilateur de l'A1 Mini de figer le plastique avant la couche suivante.
