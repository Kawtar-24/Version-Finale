
# Détection de Fraude par Carte Bancaire

## Introduction
La fraude bancaire constitue un enjeu majeur pour les institutions financières, tant sur le plan économique que sur celui de la confiance client. L’augmentation du volume des transactions électroniques complexifie l’identification manuelle des opérations frauduleuses. Dans ce contexte, les techniques de **Machine Learning** représentent un levier stratégique pour automatiser et fiabiliser la détection des comportements anormaux.

Ce projet s’inscrit dans le cadre du module *Data Science & Machine Learning*. Il vise à concevoir un modèle prédictif capable d’identifier les transactions frauduleuses à partir de données réelles, déséquilibrées et bruitées, en respectant l’ensemble du cycle de vie d’un projet de Data Science.

## Problématique et Objectifs
La problématique centrale est la suivante : **comment détecter efficacement des transactions frauduleuses rares tout en minimisant les erreurs critiques ?**  
Il s’agit d’un problème de **classification binaire**, caractérisé par un fort déséquilibre entre les classes.

Les objectifs sont :
- analyser la structure et la qualité des données,
- concevoir un pipeline de prétraitement robuste,
- comparer plusieurs modèles de classification,
- évaluer les performances selon des métriques adaptées au contexte métier.

## Présentation du Dataset
Le jeu de données étudié regroupe des transactions par carte bancaire. Chaque observation correspond à une opération financière décrite par des variables numériques issues d’une transformation préalable des données.

Caractéristiques principales :
- données fortement déséquilibrées,
- absence de variables catégorielles explicites,
- présence de variables temporelles et monétaires,
- variable cible indiquant le caractère frauduleux ou non de la transaction.

Ce type de données impose une vigilance particulière lors de l’analyse et de la modélisation.

## Méthodologie

### Prétraitement des Données
Le prétraitement constitue une étape déterminante. Les données ont été nettoyées afin d’éliminer les incohérences et préparées pour la modélisation. Les variables *Time* et *Amount* ont été standardisées afin de garantir une homogénéité des échelles.

Le déséquilibre des classes a été traité par des techniques de rééchantillonnage, permettant d’améliorer la capacité des modèles à détecter les fraudes sans biaiser excessivement les prédictions.

### Analyse Exploratoire des Données
L’analyse exploratoire a permis de :
- mettre en évidence l’extrême rareté des transactions frauduleuses,
- observer des différences significatives de distribution entre les deux classes,
- identifier certaines variables plus discriminantes que d’autres.

Les visualisations ont été systématiquement accompagnées d’une interprétation, afin de relier les observations statistiques à des enjeux métiers concrets.

### Feature Engineering
Bien que les variables soient déjà transformées, une attention particulière a été portée à la sélection des caractéristiques les plus pertinentes. Cette étape vise à réduire le bruit et à améliorer la généralisation des modèles.

## Modélisation

### Modèles Testés
Trois familles de modèles ont été implémentées :
- **Régression Logistique**, utilisée comme modèle de référence,
- **Random Forest**, pour capturer des relations non linéaires,
- **Gradient Boosting**, reconnu pour ses performances sur des données complexes.

Une validation croisée a été appliquée afin de garantir la robustesse des résultats et de limiter le sur-apprentissage.

### Métriques d’Évaluation
Dans un contexte de fraude, l’accuracy seule est insuffisante. Les métriques privilégiées sont :
- le **Recall**, afin de limiter les faux négatifs,
- le **F1-score**, pour équilibrer précision et rappel,
- l’**AUC-ROC**, pour évaluer la capacité globale de discrimination.

## Résultats et Discussion
Les résultats montrent que les modèles d’ensemble surpassent la régression logistique en termes de rappel. Le Gradient Boosting obtient les meilleures performances globales, notamment dans la détection des transactions frauduleuses.

L’analyse de la matrice de confusion met en évidence un compromis nécessaire entre la réduction des faux négatifs et la limitation des faux positifs. D’un point de vue métier, manquer une fraude est plus coûteux qu’alerter à tort, ce qui justifie le choix des métriques.

## Limites du Travail
Plusieurs limites doivent être soulignées :
- dépendance aux techniques de rééchantillonnage,
- absence de données contextuelles enrichies,
- difficulté à interpréter certains modèles complexes.

Ces limites ouvrent la voie à des améliorations futures.

## Perspectives d’Amélioration
Des pistes d’amélioration incluent :
- l’utilisation de méthodes de détection d’anomalies non supervisées,
- l’intégration de réseaux de neurones,
- l’optimisation plus fine des hyperparamètres,
- l’évaluation du modèle en conditions quasi réelles.

## Conclusion
Ce projet met en évidence l’importance d’une approche méthodologique rigoureuse pour traiter des problématiques réelles de fraude bancaire. Les résultats obtenus démontrent qu’un modèle bien calibré peut constituer un outil d’aide à la décision performant pour les institutions financières.

**Auteur : FRIMI Kawtar**
