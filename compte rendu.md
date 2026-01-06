
# Détection de Fraude par Carte Bancaire

## Introduction
Ce travail s’inscrit dans le cadre du module *Data Science & Machine Learning*. L’objectif est de développer un modèle de détection de fraude capable d’identifier des transactions bancaires frauduleuses à partir de données fortement déséquilibrées.

## Dataset et Problématique
Le jeu de données étudié concerne des transactions par carte bancaire. La variable cible indique si une transaction est frauduleuse ou non. La problématique relève d’une **classification binaire** avec un fort déséquilibre de classes.

## Méthodologie
### Prétraitement
Les données ont été nettoyées et normalisées. Les variables temporelles et monétaires ont été standardisées. Le déséquilibre a été traité par des techniques de rééchantillonnage afin d’améliorer la capacité prédictive des modèles.

### Analyse Exploratoire
L’analyse exploratoire met en évidence :
- une distribution très asymétrique de la variable cible,
- des différences significatives de distribution entre transactions normales et frauduleuses,
- une faible corrélation linéaire directe entre les variables individuelles et la cible.

### Modélisation
Plusieurs algorithmes ont été comparés, notamment :
- Régression Logistique,
- Random Forest,
- Gradient Boosting.

Une validation croisée a été appliquée afin de garantir la robustesse des résultats.

## Résultats et Discussion
Les métriques d’évaluation utilisées incluent l’Accuracy, le Recall, le F1-score et l’AUC-ROC. Les modèles basés sur des méthodes d’ensemble montrent une meilleure capacité à détecter les fraudes, notamment en termes de rappel, critère clé dans ce contexte métier.

L’analyse de la matrice de confusion révèle que la réduction des faux négatifs constitue l’enjeu principal.

## Limites et Perspectives
Les performances restent dépendantes de la qualité du rééchantillonnage. Des approches avancées comme le Deep Learning ou l’Anomaly Detection non supervisée pourraient être explorées.

## Conclusion
Ce projet démontre l’importance d’une approche méthodologique rigoureuse pour traiter des données déséquilibrées. Les résultats obtenus montrent qu’un modèle bien calibré peut apporter une réelle valeur ajoutée opérationnelle dans la lutte contre la fraude.

**Auteur : FRIMI Kawtar**
