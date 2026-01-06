
# Projet Data Science & Machine Learning

**Nom : FRIMI Kawtar**  
**Filière : Finance**  
Année universitaire : 2025–2026

---

## 1. Contexte de la Mission
Dans le cadre du module *Data Science & Machine Learning*, ce projet place l’étudiant dans la position d’un Data Scientist au sein d’un cabinet d’études stratégiques. La mission consiste à exploiter des données complexes afin de produire des analyses pertinentes et des modèles prédictifs fiables.

La détection de fraude bancaire représente un enjeu critique pour les institutions financières. Une identification tardive des transactions frauduleuses entraîne des pertes économiques directes et une dégradation de la relation client. L’automatisation par le Machine Learning constitue ainsi une réponse adaptée à ces défis.

---

## 2. Thématique d’Étude
La thématique choisie est : **Détection de fraude bancaire**.

Cette problématique relève d’un cas réel de **classification binaire supervisée**, visant à prédire si une transaction est frauduleuse ou non. Le choix de cette thématique s’explique par son importance stratégique dans le secteur financier et par la complexité des données associées.

---

## 3. Le Dataset (Données)

### 3.1 Sélection du Dataset
Le jeu de données utilisé concerne des transactions par carte bancaire, largement reconnu pour l’étude des problématiques de fraude. Il se caractérise par un volume important d’observations et un fort déséquilibre entre transactions normales et frauduleuses.

### 3.2 Définition de la Problématique
La tâche à résoudre est une **classification binaire**, dans laquelle la variable cible indique le caractère frauduleux d’une transaction.

### 3.3 Dictionnaire des Données
- Observations : transactions bancaires individuelles  
- Variables explicatives : variables numériques transformées, montant et temps  
- Variable cible : fraude (0 : normale, 1 : frauduleuse)

L’analyse descriptive met en évidence une rareté extrême des fraudes, ce qui complexifie la modélisation.

---

## 4. Implémentation Technique (Python)

### 4.1 Pré-traitement des Données

#### Nettoyage
Les données ont été inspectées afin de vérifier l’absence de doublons et d’incohérences.

#### Gestion des valeurs manquantes
Le dataset ne présente pas de valeurs manquantes explicites, ce qui facilite la phase de préparation.

#### Encodage
Les variables étant exclusivement numériques, aucun encodage catégoriel n’a été requis.

#### Normalisation
Les variables *Time* et *Amount* ont été standardisées afin d’assurer une comparabilité des échelles.

#### Gestion du déséquilibre
Des techniques de rééchantillonnage ont été utilisées afin d’améliorer la capacité du modèle à détecter les fraudes.

**Analyse critique :**  
Un déséquilibre non traité conduit à des modèles biaisés vers la classe majoritaire.

---

### 4.2 Analyse Exploratoire des Données (EDA)

#### Visualisation des distributions
Les histogrammes révèlent une forte concentration des transactions normales et une dispersion importante des transactions frauduleuses.

#### Analyse des corrélations
La matrice de corrélation montre une faible corrélation linéaire entre les variables et la cible.

#### Feature Engineering
Une sélection des variables les plus informatives a été réalisée afin de limiter le bruit.

Chaque graphique a été interprété afin de relier les observations statistiques aux enjeux financiers.

---

### 4.3 Modélisation (Machine Learning)

#### Algorithmes testés
- Régression Logistique  
- Random Forest  
- Gradient Boosting  

#### Validation
Une séparation entraînement/test combinée à une validation croisée a été appliquée.

#### Optimisation des hyperparamètres
Les hyperparamètres ont été optimisés afin d’améliorer les performances globales des modèles.

---

## 5. Résultats & Discussion

### 5.1 Métriques d’Évaluation
Les métriques utilisées incluent :
- Accuracy  
- Recall  
- F1-score  
- AUC-ROC  

Le rappel est privilégié afin de minimiser les faux négatifs.

### 5.2 Analyse des Résultats
Les modèles d’ensemble présentent de meilleures performances que la régression logistique, notamment en termes de détection des fraudes.

### 5.3 Matrice de Confusion
L’analyse de la matrice de confusion montre une réduction significative des fraudes non détectées, au prix d’une augmentation modérée des faux positifs.

**Interprétation métier :**  
Dans un contexte financier, ce compromis est acceptable.

---

## 6. Conclusion
Ce projet démontre l’apport du Machine Learning dans la détection de fraude bancaire. L’approche méthodologique suivie permet de développer un modèle robuste et pertinent pour un usage opérationnel.

### Limites
- dépendance à la qualité des données,
- interprétabilité limitée des modèles complexes.

### Pistes d’Amélioration
- détection d’anomalies non supervisée,
- intégration de modèles de Deep Learning,
- déploiement en environnement réel.

