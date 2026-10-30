# Sujet n° 1 : Prédiction des arrivées de navires au Havre

*Encadrant :* Christophe Duhamel

L’objectif de ce projet est d’exploiter des données AIS afin d’étudier et de prédire les arrivées de navires au Port du Havre, en particulier les porte-conteneurs et les navires de croisière.

Dans un premier temps, les étudiants devront récupérer et préparer les données AIS correspondant aux arrivées de navires au Havre. Une analyse statistique permettra ensuite d’identifier d’éventuelles régularités : fréquence des arrivées, saisonnalité, régularité des rotations d’un même navire, intervalles entre deux arrivées, etc.

À partir de cette analyse, différentes approches d’apprentissage automatique seront testées afin de prédire les prochaines arrivées. Deux problèmes pourront être étudiés : prédire la prochaine date d’arrivée d’un navire donné, ou prédire la prochaine arrivée dans le port, quel que soit le navire. Les méthodes proposées seront comparées à des approches simples de référence.

Enfin, les heures d’arrivée prédites seront injectées dans un modèle d’optimisation développé dans le cadre du projet NAVICLEAN. Ce modèle permet de planifier l’affectation des navires aux quais, les temps d’attente et l’utilisation de l’alimentation électrique à quai. L’objectif final est d’évaluer dans quelle mesure une meilleure prédiction des arrivées peut améliorer les décisions portuaires et réduire les impacts environnementaux.

*Outils envisagés :* Python, pandas, matplotlib, scikit-learn.
