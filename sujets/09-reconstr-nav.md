# Sujet n° 9 : Reconstruction de donnees  ́manquantes par IA genérative, application aux données maritimes

*Encadrant :* Frédéric Guinand

## Introduction

Les réseaux maritimes ont donné lieu à de nombreuses recherches au cours des dernières décennies. Avec le développement économique et la conteneurisation des échanges (utilisation des conteneurs pour stocker et transporter des marchandises sur de grandes distances). Une partie de ces recherches se sont focalisées sur la modélisation des réseaux maritimes à l'aide de graphes et certains de ces travaux ont essayé de considérer la prise en compte du temps.

La construction de ces graphes repose sur la disponibilité des données de déplacement des porte-conteneurs de port en port. Dans le cadre du projet MAGNETICS, nous disposons de données partielles de ces mouvements pour les années allant de 1977 à 2016.

---

## 2. Description du sujet

Nous possédons des données de mouvements de porte-conteneurs depuis 1977 jusqu'en 2016. Ces données nous permettent de savoir quel bateau s'est déplacé à quelle date depuis un port vers un autre port. Pour chaque année nous disposons des mouvements pour seulement 4 mois de l'année, par exemple pour les années de 1977 à 1995 :

| Année | Jan | Fév | Mar | Avr | Mai | Jun | Jul | Aoû | Sep | Oct | Nov | Déc |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **1977** | | X | | X | | | | | X | | | X |
| **1978** | | X | | X | | | | | X | | | X |
| **1979** | | X | | X | | | | | X | | | X |
| **1980** | | X | | X | | | | | X | | | X |
| **1981** | X | X | | | | | X | X | | | | |
| **1982** | | X | | X | | | | | X | | | X |
| **1983** | | X | | X | | | | | X | | | X |
| **1984** | | X | | X | | | | | X | | | X |
| **1985** | | X | | X | | | | | X | | | X |
| **1986** | X | X | | | | | X | X | | | | |
| **1987** | | X | | X | | | | | X | | | X |
| **1988** | | X | | X | | | | | X | | | X |
| **1989** | | X | | X | | | | | X | | | X |
| **1990** | | X | | X | X | X | X | | | X | | |
| **1991** | X | X | | | | | X | X | | | | |
| **1992** | | X | | X | | | | | X | | | X |
| **1993** | | X | | X | | | | | X | | | X |
| **1994** | | X | | X | | | | | X | | | X |
| **1995** | X | X | | X | | | | | X | | | X |

Mais pour deux années, 1996 et 2006 nous possédons l'ensemble des mouvements sur la durée totale de l'année.

Selon certaines hypothèses que vous devrez proposer, par exemple que les mouvements ne dépendent pas de la saison, et qui seront discutées, le projet consiste à mettre en œuvre une ou plusieurs méthodes utilisant les IA génératives pour combler les périodes pour lesquelles aucune donnée n'est disponible. Vous pourrez vous appuyer sur les durées de voyage, sur l'hypothèse que les bateaux effectuent des tournées plus ou moins régulières, etc.

## Format des données

Les données brutes sont au format `.csv`. Chaque ligne comprend un ensemble de champs :

* `move_pkid; move_id; year; month;` $\rightarrow$ informations inutiles
* `departure; arrival;` $\rightarrow$ date de départ du port et date d'arrivée dans le port suivant
* `from_id; to_id; from_name; to_name;` $\rightarrow$ identifiant et nom des ports de départ et d'arrivée
* `from_type; to_type;` $\rightarrow$ informations inutiles pour nous
* `vessel_id; vessel_name;` $\rightarrow$ identifiant et nom du navire
* `vessel_type; dwt; time` $\rightarrow$ informations inutiles

Les seuls champs qui vont nous intéresser sont les dates de départ, l'identifiant du port de départ et l'identifiant du bateau.

**Exemples :**

```text
departure; from_id; vessel_id
01/03/1977 00:00; 430; 337516
01/03/1977 00:00; 428; 912666
01/03/1977 00:00; 529; 557460
01/03/1977 00:00; 2993; 30654
01/03/1977 00:00; 2561; 17501
01/03/1977 00:00; 3164; 4371
01/03/1977 00:00; 2151; 43021
01/03/1977 00:00; 1697; 416
01/03/1977 00:00; 941; 65317
```

Pour connaître tous les bateaux qui étaient présents dans un même port le même jour, on peut filtrer par l'identifiant du port :

```text
19/03/1977 00:00; 4977; 22755
20/03/1977 00:00; 4977; 20130
20/03/1977 00:00; 4977; 52713
22/03/1977 00:00; 4977; 47701
22/03/1977 00:00; 4977; 4152
24/03/1977 00:00; 4977; 77127
24/03/1977 00:00; 4977; 24341
26/03/1977 00:00; 4977; 2050
26/03/1977 00:00; 4977; 75725
26/03/1977 00:00; 4977; 32464
27/03/1977 00:00; 4977; 27572
29/03/1977 00:00; 4977; 47705
```

On peut déduire de ces lignes que :

* Le 20 mars 1977, les bateaux **20130** et **52713** étaient présents simultanément dans le port d'identifiant **4977**.
* Le 26 mars 1977, les bateaux **2050**, **75725** et **32464** étaient présents dans le même port.
