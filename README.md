# Codewyrm

Codewyrm est une petite application web contenue dans un seul fichier HTML, pensée comme un Tamagotchi pour développeur. L'idée de départ était d'avoir une créature en pixel-art qui évolue en fonction de mon activité réelle sur GitHub et des exercices d'algorithmique résolus sur LeetCode.

J'ai réalisé ce projet entièrement avec Claude à l'époque où tout le monde en parlait, principalement par curiosité pour tester ses capacités de génération d'interface et de rendu direct (Artifacts) à partir d'une idée personnelle.

## Concept et fonctionnement

Le principe repose sur une jauge d'activité appelée *Vigor* et sur le nombre de jours consécutifs de code (*Flame / Streak*) :

* **Synchronisation GitHub :** En entrant un pseudo GitHub public, le script interroge directement l'API publique de GitHub (sans clé API ni serveur intermédiaire) pour analyser les événements récents : nombre de commits, Pull Requests fusionnées, nombre de dépôts publics et langage de programmation principal.
* **Suivi LeetCode :** Trois boutons permettent d'ajouter manuellement les problèmes résolus selon leur difficulté (Easy +1, Medium +3, Hard +7) pour faire progresser la créature même les jours sans commit sur GitHub.
* **Évolution sur 6 stades :** En fonction du score total, la créature passe par six étapes (*Egg*, *Hatchling*, *Drakeling*, *Young Dragon*, *Elder Dragon*, *Ancient Wyrm*). À chaque stade, son apparence change avec l'apparition progressive d'épines dorsales, de cornes, d'ailes plus grandes et d'une queue plus longue.
* **Apparence dynamique en SVG :** Le dragon n'est pas une image fixe. Il est dessiné dynamiquement en JavaScript sur une grille de 30x22 pixels convertie en balises `<svg>`. Sa couleur s'adapte automatiquement au langage le plus utilisé sur le profil GitHub (vert pour Python, jaune pour JavaScript, violet pour C++, etc.), et une flamme apparaît au bout de sa queue à partir de 7 jours d'activité consécutifs.

## Utilisation

Le projet ne nécessite aucune installation ni dépendance externe (tout le HTML, le CSS et le JavaScript sont regroupés dans le même fichier).

1. Cloner le dépôt ou télécharger le fichier `index.html`.
2. Ouvrir le fichier directement dans n'importe quel navigateur web.
3. Entrer un nom d'utilisateur GitHub dans le champ dédié et cliquer sur **Hatch**.

## Détails techniques

* **HTML5 / CSS3 :** Interface inspirée des fiches de jeu de rôle rétro avec polices Google Fonts (*Press Start 2P*, *Cinzel*, *JetBrains Mono*) et animations CSS légères.
* **JavaScript Vanilla :** Appels asynchrones (`fetch`) vers les routes `/users/{user}`, `/events/public` et `/repos` de l'API REST GitHub, calcul des séries de jours actifs et moteur de rendu pixel-art procédural en SVG.
