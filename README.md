# Étude de marché international : quels pays cibler pour exporter de la volaille ?

Étude réalisée pendant ma formation Data Analyst (OpenClassrooms) pour une entreprise avicole fictive, La poule qui chante, qui veut s'implanter à l'international. La question posée par la direction : quels groupes de pays cibler en priorité ? Le livrable final est une recommandation argumentée présentée à un comité de direction non technique.

## La démarche en deux notebooks

- `1_preparation_donnees.ipynb` : collecte multi-sources, construction des variables, nettoyage, fusion et contrôle de couverture
- `2_acp_clustering.ipynb` : exploration, analyse en composantes principales, classification ascendante hiérarchique, k-means, profils des groupes et recommandations

## Les données

Trois sources publiques croisées : les bilans alimentaires de la FAO (disponibilité en calories, protéines, volaille, importations), les données de population FAO sur 2000 et 2017, le PIB par habitant de la Banque mondiale et l'indicateur de stabilité politique des Worldwide Governance Indicators.

Le choix des variables s'appuie sur une grille PESTEL, pour couvrir les dimensions politique, économique et sociale d'un marché, pas seulement l'alimentation. Neuf variables construites : population, croissance démographique 2000-2017, protéines totales, calories totales, disponibilité de volaille par habitant, taux de dépendance aux importations, part des protéines animales, PIB par habitant, stabilité politique.

Le rapprochement entre sources se fait par code ISO3 plutôt que par nom de pays, pour éviter les échecs de correspondance dus aux libellés. Résultat : 165 pays complets, couvrant 96 % de la population mondiale, bien au-delà des 100 pays et 60 % demandés.

Les fichiers sources ne sont pas publiés dans ce dépôt : ils proviennent de la FAO et de la Banque mondiale et restent librement téléchargeables sur leurs sites respectifs.

## Les résultats

L'ACP montre que l'information se concentre sur un axe principal (48 % de la variance) qui est un axe de développement : richesse, stabilité, consommation de protéines animales et de volaille vont ensemble, à l'opposé de la croissance démographique. Le deuxième axe oppose les géants démographiques aux petits territoires dépendants des importations. Trois composantes sont retenues, soit 73 % de l'information conservée.

Deux méthodes de clustering sont appliquées puis comparées : classification ascendante hiérarchique (méthode de Ward) et k-means à quatre groupes. Les deux convergent sur la structure, ce qui valide la segmentation : un groupe de pays développés, un groupe intermédiaire, un groupe en développement, et un segment à part réunissant la Chine et l'Inde.

Recommandation retenue : cibler le groupe des pays développés, seul à réunir les quatre critères d'un marché premium (pouvoir d'achat, consommation de volaille déjà élevée, stabilité politique, ouverture aux importations). Priorités identifiées : États-Unis, Australie, Canada, Nouvelle-Zélande, Israël, et plusieurs marchés européens proches pour la logistique.

## Limites assumées

Les données portent sur 2017, année la plus complète disponible sur toutes les sources au moment de l'étude ; les conclusions valent pour cette photographie. Le clustering décrit des groupes, il ne prédit pas un succès commercial : c'est un outil de priorisation, pas une garantie. Les valeurs atypiques (géants démographiques, pays très riches, territoires très dépendants des importations) ont été conservées volontairement parce qu'elles correspondent à des réalités de marché, mais elles influencent la formation des groupes. Enfin, une étude d'implantation réelle demanderait des données que ce jeu ne contient pas : droits de douane, coûts logistiques, concurrence locale, normes sanitaires.

## Exécution
```
pip install -r requirements.txt
```

Télécharger les fichiers sources depuis la FAO et la Banque mondiale, les placer dans un dossier `data/`, puis exécuter les deux notebooks dans l'ordre.

## Auteur

Ahmed El Ghrairi, Data Analyst à Marseille.
[Portfolio](https://ahmedelghrairi.github.io) · [LinkedIn](https://www.linkedin.com/in/ahmed-el-ghrairi-a581ba177/)
