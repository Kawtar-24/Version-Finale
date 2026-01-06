
# Projet Data Science & Machine Learning

**Nom : FRIMI Kawtar**  
**Filière : Finance**  
Année universitaire : 2025–2026

![me](https://github.com/user-attachments/assets/72aeead1-35d3-46bd-8b86-56bacba8f861)

---

## 1. Contexte de la Mission
Ce projet s’inscrit dans un contexte de **lutte contre la fraude bancaire par carte de crédit**, problématique centrale pour les institutions financières modernes. Les documents techniques fournis (notebooks Python) portent explicitement sur l’analyse de transactions par carte bancaire et sur la mise en place de modèles de détection de fraude.

Dans ce cadre, la mission du Data Scientist consiste à exploiter des données transactionnelles massives afin d’identifier automatiquement des comportements frauduleux, tout en minimisant l’impact sur les clients légitimes.

---

## 2. Thématique d’Étude
La thématique traitée est la **détection de fraude bancaire par carte de crédit**, en cohérence directe avec les fichiers fournis.

Il s’agit d’un problème de **classification binaire supervisée**, où chaque transaction est classée comme :
- transaction normale,
- transaction frauduleuse.

Cette thématique est directement liée aux enjeux de gestion du risque financier et de prévention des pertes.

---

## 3. Le Dataset (Données)

### 3.1 Sélection du Dataset
Le dataset utilisé est celui des **transactions par carte bancaire** couramment utilisé pour l’étude de la fraude. Il correspond exactement au dataset exploité dans les notebooks fournis, caractérisé par :
- un grand nombre de transactions,
- une anonymisation des variables,
- un fort déséquilibre des classes.

### 3.2 Définition de la Problématique
La problématique consiste à détecter des transactions frauduleuses rares parmi une majorité de transactions légitimes, ce qui rend l’apprentissage particulièrement complexe.

### 3.3 Dictionnaire des Données
- **Transaction** : opération financière individuelle par carte bancaire  
- **Variables explicatives** : variables numériques transformées (V1 à Vn), montant (*Amount*), temps (*Time*)  
- **Variable cible** : fraude (1) ou transaction normale (0)

**Analyse orientée fraude :**  
Les transactions frauduleuses présentent des patterns subtils, souvent masqués par l’anonymisation des variables.

---

## 4. Implémentation Technique (Python)

### 4.1 Pré-traitement des Données

#### Nettoyage
Les données transactionnelles ont été vérifiées afin d’assurer leur cohérence avant l’analyse.

#### Valeurs manquantes
Le dataset ne contient pas de valeurs manquantes, ce qui est cohérent avec les fichiers fournis.

#### Encodage
Aucun encodage n’a été nécessaire, les variables étant numériques.

#### Normalisation
Les variables *Time* et *Amount* ont été standardisées pour éviter que les montants élevés n’influencent excessivement la détection de fraude.

#### Gestion du déséquilibre
Des techniques de rééchantillonnage ont été utilisées afin d’améliorer la détection des fraudes.

---

### 4.2 Analyse Exploratoire des Données (EDA)

#### Distributions
Les graphiques montrent que les transactions frauduleuses présentent des distributions plus étalées et plus irrégulières.

#### Corrélations
La faible corrélation linéaire observée confirme que la fraude ne repose pas sur une seule variable, mais sur des combinaisons complexes.

#### Feature Engineering
La sélection de variables pertinentes permet de renforcer la capacité des modèles à identifier des schémas frauduleux.

---

### 4.3 Modélisation (Machine Learning)

#### Algorithmes implémentés
- Régression Logistique  
- Random Forest  
- Gradient Boosting  

Ces algorithmes correspondent à ceux implémentés dans les notebooks fournis.

#### Validation
Une validation croisée a été appliquée afin d’évaluer correctement la performance en détection de fraude.

#### Optimisation
Les hyperparamètres ont été optimisés pour maximiser le rappel des transactions frauduleuses.

---

## 5. Résultats & Discussion

### 5.1 Métriques d’Évaluation
Les métriques retenues sont adaptées à la fraude :
- Recall (prioritaire),
- F1-score,
- AUC-ROC.

### 5.2 Analyse Comparative
Les modèles d’ensemble obtiennent de meilleures performances que la régression logistique, notamment pour la détection des fraudes.

### 5.3 Matrice de Confusion
L’analyse montre une réduction des fraudes non détectées, au prix d’un nombre contrôlé de faux positifs.

**Analyse métier :**  
Ce compromis est acceptable dans un contexte bancaire.

---

## 6. Conclusion

### Limites
- dépendance au dataset anonymisé,
- interprétabilité limitée des modèles complexes.

### Perspectives
- détection d’anomalies,
- intégration de modèles avancés,
- déploiement opérationnel.

**Conclusion générale :**  
Ce travail, basé sur les fichiers fournis, démontre l’efficacité du Machine Learning pour la détection de fraude bancaire par carte de crédit.

