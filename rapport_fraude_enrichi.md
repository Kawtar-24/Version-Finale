
# Détection de Fraude par Carte Bancaire

## Introduction
La fraude bancaire représente un risque financier et opérationnel majeur pour les établissements financiers. La multiplication des transactions électroniques rend les contrôles manuels inefficaces. L’exploitation des techniques de Machine Learning permet d’automatiser la détection des comportements anormaux tout en améliorant la réactivité des systèmes de contrôle.

Ce projet, réalisé dans le cadre du module *Data Science & Machine Learning*, vise à développer une approche complète de détection de fraude en suivant rigoureusement les étapes méthodologiques recommandées : compréhension métier, analyse exploratoire, modélisation et interprétation des résultats.

## Problématique et Objectifs
La problématique traitée est une **classification binaire** visant à distinguer les transactions frauduleuses des transactions légitimes dans un contexte de données fortement déséquilibrées.

Les objectifs principaux sont :
- comprendre la structure et la distribution des données,
- analyser l’impact du déséquilibre des classes,
- comparer plusieurs algorithmes de Machine Learning,
- interpréter les résultats à l’aide de métriques adaptées au contexte métier.

## Présentation et Analyse du Dataset
Le jeu de données contient des transactions par carte bancaire décrites par des variables numériques issues de transformations statistiques.

### Analyse Descriptive
- La variable cible montre une **asymétrie extrême**, avec une proportion très faible de fraudes.
- Les variables *Time* et *Amount* présentent des distributions étendues, justifiant une normalisation.
- Les statistiques descriptives (moyenne, médiane, écart-type) révèlent des écarts significatifs entre transactions normales et frauduleuses, notamment sur les montants.

### Lecture des Tableaux Statistiques
Les tableaux de statistiques montrent que les transactions frauduleuses tendent à avoir des montants atypiques. Cette observation renforce l’intérêt de modèles capables de capter des comportements non linéaires.

## Analyse Exploratoire des Données (EDA)

### Analyse des Distributions
Les histogrammes mettent en évidence :
- une concentration des transactions normales autour de valeurs centrales,
- une dispersion plus marquée pour les transactions frauduleuses.

Ces différences suggèrent un potentiel discriminant exploitable par les modèles.

### Analyse des Corrélations
La matrice de corrélation indique une faible corrélation linéaire directe avec la cible. Cela justifie l’utilisation d’algorithmes non linéaires tels que Random Forest ou Gradient Boosting.

### Analyse Graphique Comparative
Les boxplots comparant les deux classes montrent des valeurs aberrantes plus fréquentes dans les transactions frauduleuses. Cette observation soutient l’hypothèse d’un comportement transactionnel atypique.

## Prétraitement et Feature Engineering

### Prétraitement
- Standardisation des variables numériques afin d’uniformiser les échelles.
- Traitement du déséquilibre par rééchantillonnage pour améliorer la sensibilité des modèles.
- Séparation rigoureuse des jeux d’entraînement et de test.

### Feature Engineering
Une sélection des variables les plus informatives a été réalisée afin de réduire le bruit. Cette étape améliore la stabilité et la généralisation des modèles.

## Modélisation et Comparaison des Algorithmes

### Modèles Implémentés
- **Régression Logistique** : modèle de base interprétable.
- **Random Forest** : capture des relations complexes.
- **Gradient Boosting** : optimisation séquentielle des erreurs.

### Analyse Comparative des Résultats
Les tableaux de résultats montrent que :
- la régression logistique présente un rappel limité,
- les modèles d’ensemble améliorent significativement la détection des fraudes,
- le Gradient Boosting offre le meilleur compromis entre rappel et précision.

### Lecture des Métriques
Le rappel est privilégié afin de minimiser les faux négatifs. Le F1-score confirme l’équilibre global du modèle retenu. L’AUC-ROC valide la capacité de discrimination du classifieur.

### Analyse de la Matrice de Confusion
La matrice de confusion met en évidence :
- une réduction notable des fraudes non détectées,
- une augmentation contrôlée des faux positifs, acceptable d’un point de vue métier.

## Discussion et Interprétation
Les résultats confirment que le déséquilibre des données influence fortement les performances. Les modèles complexes s’adaptent mieux à cette contrainte. D’un point de vue opérationnel, le modèle retenu permet une détection plus proactive des fraudes.

## Limites
- dépendance à la qualité du rééchantillonnage,
- interprétabilité réduite des modèles complexes,
- absence de données comportementales enrichies.

## Perspectives
- intégration de méthodes de détection d’anomalies,
- utilisation de réseaux de neurones,
- déploiement en environnement temps réel.

## Conclusion
Ce travail démontre l’apport du Machine Learning dans la détection de fraude bancaire. L’approche méthodologique suivie garantit des résultats exploitables et alignés avec les enjeux métiers.

**Auteur : FRIMI Kawtar**
