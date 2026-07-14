# Big Data

Estimer la probabilité qu’une PME cesse son activité dans un horizon de deux ans à partir de données financières, organisationnelles et territoriales.

## Contexte métier

Une banque, un fournisseur, un bailleur ou un partenaire commercial doit pouvoir évaluer la pérennité d’une entreprise avant de s’engager.

Ce projet transforme des données comptables et structurelles en **score de risque de sortie**, utilisable comme aide à la décision.

## Données

L’échantillon final comprend :

- 1 935 entreprises ;
- 135 sorties ;
- 1 800 entreprises restées actives ;
- PME de moins de 10 M€ de chiffre d’affaires ;
- période d’étude : 2012-2014.

Les variables couvrent notamment les ventes, les actifs, les passifs, les stocks, les liquidités, le résultat annuel, la masse salariale, le nombre de dirigeants, la localisation et l’effectif moyen.

## Pipeline

1. filtrage du périmètre PME ;
2. traitement des valeurs manquantes et incohérentes ;
3. construction de la cible binaire de sortie ;
4. sélection de variables par régression logistique et backward selection ;
5. entraînement de trois modèles ;
6. comparaison par AUC, précision, rappel et matrice de confusion.

## Modèles comparés

| Modèle | AUC |
|---|---:|
| k plus proches voisins | **0,733** |
| Régression logistique | 0,672 |
| Arbre de décision | 0,626 |

Le k-NN obtient le meilleur pouvoir de classement parmi les modèles testés.

## Point d’attention

La cible est fortement déséquilibrée. Une accuracy proche de 93 % pourrait masquer une mauvaise détection des entreprises réellement à risque.

L’analyse privilégie donc l’AUC et recommande d’ajouter :

- le rappel de la classe minoritaire ;
- le score F1 ;
- la courbe précision-rappel ;
- un seuil de décision calibré selon les coûts métier.

## Technologies

`Python` · préparation de données · classification supervisée · sélection de variables · AUC-ROC · gestion du déséquilibre

## Ce que ce projet démontre

- compréhension d’un besoin métier ;
- construction rigoureuse d’une cible ;
- préparation de données financières ;
- comparaison de modèles ;
- lecture critique des métriques ;
- transformation d’une analyse statistique en outil d’aide à la décision.

## Limites et améliorations

Le faible nombre de sorties limite la stabilité des modèles. Une suite logique serait de mettre en place une validation temporelle, une calibration des probabilités et des méthodes de rééquilibrage appliquées uniquement aux données d’entraînement.

## Auteurs

Projet académique réalisé par **Benjamin BAILLET** et **Alexandra MILLOT**.

---
