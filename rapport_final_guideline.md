
# Projet Data Science & Machine Learning  
## Détection de fraude par carte bancaire

**Auteur : FRIMI Kawtar**  
Année universitaire : 2025–2026

---

## 1. Contexte de la mission
Dans le cadre du module *Data Science & Machine Learning*, ce projet se place dans la peau d’un Data Scientist intervenant pour un cabinet d’études stratégiques. La mission consiste à transformer un volume important de données transactionnelles complexes en informations exploitables et en modèles prédictifs fiables.

La problématique de la fraude bancaire constitue un cas d’usage réel à fort enjeu économique. Une détection tardive ou inefficace entraîne des pertes financières importantes ainsi qu’une dégradation de la confiance client.

---

## 2. Thématique choisie et problématique
La thématique retenue est la **détection de fraude bancaire**, relevant d’un problème de **classification binaire supervisée**.

La problématique est la suivante :  
> Comment identifier efficacement des transactions frauduleuses rares dans un ensemble massif de transactions légitimes tout en minimisant les erreurs critiques ?

Cette problématique est caractérisée par :
- un **fort déséquilibre des classes**,
- un coût métier asymétrique des erreurs,
- des données transformées et partiellement anonymisées.

---

## 3. Présentation et compréhension du dataset

### 3.1 Description générale
Le dataset contient des transactions par carte bancaire. Chaque observation représente une transaction décrite par des variables numériques issues de transformations statistiques.

Caractéristiques :
- données numériques uniquement,
- forte asymétrie de la variable cible,
- présence de variables temporelles et monétaires.

### 3.2 Analyse descriptive (tableaux statistiques)
Les tableaux statistiques révèlent :
- une moyenne et une médiane de montants différentes entre fraudes et transactions normales,
- une dispersion plus élevée pour les transactions frauduleuses,
- une forte présence de valeurs extrêmes.

**Analyse critique :**  
Ces observations suggèrent que les transactions frauduleuses présentent un comportement atypique, mais difficilement détectable par des seuils simples.

---

## 4. Prétraitement des données

### 4.1 Nettoyage et transformation
- vérification de l’absence de doublons,
- standardisation des variables *Time* et *Amount*,
- homogénéisation des échelles.

### 4.2 Gestion du déséquilibre
Le déséquilibre marqué entre classes impose l’utilisation de techniques de rééchantillonnage. Sans cette étape, les modèles tendent à prédire systématiquement la classe majoritaire.

**Analyse critique :**  
Le rééchantillonnage améliore la sensibilité du modèle mais peut introduire un biais s’il n’est pas contrôlé.

---

## 5. Analyse exploratoire des données (EDA)

### 5.1 Analyse des distributions
Les histogrammes montrent :
- une forte concentration des transactions normales,
- une dispersion irrégulière des transactions frauduleuses.

**Lecture graphique :**  
Cette différence de structure justifie l’utilisation de modèles capables de capturer des patterns complexes.

### 5.2 Analyse des corrélations
La matrice de corrélation indique une faible corrélation linéaire entre les variables et la cible.

**Interprétation :**  
Les modèles linéaires seuls sont insuffisants pour capturer la complexité des données.

### 5.3 Analyse comparative par boxplots
Les boxplots mettent en évidence :
- davantage de valeurs aberrantes pour les fraudes,
- une variabilité plus importante.

---

## 6. Modélisation et algorithmes

### 6.1 Modèles implémentés
Trois algorithmes ont été testés :
- Régression Logistique,
- Random Forest,
- Gradient Boosting.

### 6.2 Méthodologie de validation
- séparation entraînement/test,
- validation croisée,
- optimisation des hyperparamètres.

### 6.3 Analyse comparative des résultats (tableaux)
Les tableaux de résultats montrent :
- une faible performance de la régression logistique sur le rappel,
- une nette amélioration avec Random Forest,
- les meilleures performances globales avec Gradient Boosting.

**Lecture critique :**  
Les modèles d’ensemble s’adaptent mieux au déséquilibre et aux relations non linéaires.

### 6.4 Analyse de la matrice de confusion
La matrice de confusion montre :
- une réduction significative des faux négatifs,
- une augmentation modérée des faux positifs.

**Analyse métier :**  
Ce compromis est acceptable car le coût d’une fraude non détectée est supérieur à celui d’une fausse alerte.

---

## 7. Discussion des résultats
Les résultats confirment que :
- le déséquilibre impacte fortement les performances,
- le choix des métriques est déterminant,
- la complexité du modèle améliore la détection.

Toutefois, l’interprétabilité diminue avec la complexité des algorithmes.

---

## 8. Limites du travail
- dépendance aux données transformées,
- absence de variables comportementales,
- difficulté d’interprétation des modèles avancés.

---

## 9. Perspectives d’amélioration
- intégration de méthodes de détection d’anomalies,
- exploration du Deep Learning,
- déploiement en environnement temps réel.

---

## 10. Conclusion
Ce projet illustre l’importance d’une démarche complète en Data Science. L’approche méthodologique adoptée permet de développer un modèle robuste et exploitable pour la détection de fraude bancaire, répondant aux exigences académiques et aux enjeux métiers.

