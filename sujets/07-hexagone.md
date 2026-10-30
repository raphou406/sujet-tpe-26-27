# Sujet n° 7 : Géoxagone - réalisation et description mutiscopique d'un pavage hexagonal

*Encadrant :* Frédéric Serin

Le projet Géoxagone modélise le pavage hexagonal du plan. Il est attendu de mettre en avant l'approche « multiscopique », c'est-à-dire la capacité d'observer et d'interroger la structure à plusieurs échelles d'analyse spatiale. Le projet s'appuie sur une base Java générant un fichier SVG d'hexagones. Il sera attendu, en particulier, l'ajout de fonctionnalités dynamiques en JavaScript pour permettre la description de l'environnement.

Nous nous intéressons au pavage du plan par des hexagones. Lors de ce recouvrement du plan, on peut parler de représentation aréolaire ou réticulaire. Un code Java déjà réalisé et validé sera fourni permettant de réaliser le pavage paramétré hexagonal d'un plan, avec voisinages géométrique. Ce programme génère un fichier au format SVG représentant les hexagones qui constituent de façon fractale des territoires
autour d'un centre initial.

L'objectif du projet sera d'introduire des éléments en Javascript permettant à partir de n'importe quel hexagone d'avoir des informations sur ses territoires contenants et ses voisinages.

Le programme pourra être enrichi par la génération des voisinage arithmétiques (voisinages classiques en couronne).

Des éléments sur le déplacement afin de générer les hexagones seront fournis afin de donner une trame homogène aux diverses approches et objectifs.

## Précisions de représentations

Lorsque l'on manipule ces structures, on bascule généralement entre deux visions de
l'espace :

### La représentation aréolaire (ou surfacique)

L'accent est mis sur l'aire, la surface pleine de chaque hexagone en tant qu'entité géométrique fermée (un polygone à deux dimensions).

Le plan est découpé en cellules — pour nous des hexagones — approche pertinente en géographie et en traitement de l'information spatiale. Il insiste sur la décomposition de l'espace en unités élémentaires.

Cette représentation est privilégiée lorsque l'hexagone est considéré comme un contenant, une zone d'accumulation, ou un réceptacle de données (par exemple, en cartographie thématique pour stocker une valeur statistique, une densité de population ou une mesure environnementale). Chaque hexagone possède une extension spatiale propre, des limites franches et une surface mesurable.

### La représentation réticulaire (ou réseau)

L'accent est déplacé de la surface vers la structure topologique et les relations d'adjacence. L'espace n'est plus vu comme un ensemble de surfaces pleines, mais comme un système de nœuds et de liens.

*Déclinaisons :* C'est ici que se fait la distinction fondamentale entre deux types de réseaux.

Le maillage hexagonal : Très employé en modélisation numérique (éléments finis, simulations physiques), il met l'accent sur la structure de grille interconnectée.

Il correspond au réseau dual du maillage explicité juste après. Le réseau est basé sur les centres et le voisinage. On abstrait la géométrie surfacique de l'hexagone en plaçant un nœud unique en son centre (le centroïde). On relie ensuite ce centre aux six centres des hexagones voisins directs par des segments (les arêtes du graphe de voisinage).

Ce réseau de centres et de liens forme un graphe triangulaire (ou réseau triangulaire), qui est le graphe dual planaire de la mosaïque hexagonale initiale. Les distances entre centres adjacents sont uniformes, formant un maillage triangulaire équilatéral parfait. Cette approche est courante en analyse de voisinage (ex. automates cellulaires) et pour le calcul des plus courts chemins.

Le réseau basé sur les frontières géométriques considère le squelette physique des hexagones, c'est-à-dire l'ensemble des sommets (les coins où se rejoignent trois hexagones) et des arêtes (les segments de droite partagés par deux hexagones adjacents). Ce réseau représente donc les frontières entre hexagones. C'est le maillage structurel direct du nid d'abeille. Les arêtes forment les barrières ou les canaux de circulation entre les cellules, et les sommets constituent des points de convergence triples.
