
# Projet Data Science & Machine Learning  
## Détection de fraude par carte bancaire

**Nom : FRIMI Kawtar**  
**Filière : Finance**  
Année universitaire : 2025–2026

---

## 1. Contexte de la mission
La fraude bancaire constitue un enjeu stratégique majeur pour les institutions financières. L’augmentation continue du volume des paiements électroniques, combinée à la sophistication croissante des techniques frauduleuses, rend les méthodes de contrôle traditionnelles insuffisantes.

Dans ce contexte, le rôle du Data Scientist consiste à exploiter les données transactionnelles afin de détecter automatiquement les comportements suspects. La mission de ce projet est de transformer des données brutes en informations exploitables et en modèles prédictifs capables de soutenir la prise de décision.

---

## 2. Thématique d’étude et problématique
La thématique choisie est la **détection de fraude par carte bancaire**, relevant d’un problème de **classification binaire supervisée**.

La problématique centrale est la suivante :  
> Comment identifier efficacement des transactions frauduleuses, rares par nature, tout en limitant les erreurs coûteuses pour l’institution financière ?

Cette problématique est caractérisée par :
- un fort déséquilibre entre les classes,
- un coût métier asymétrique des erreurs,
- des exigences élevées en termes de fiabilité.

---

## 3. Présentation et compréhension du dataset

### 3.1 Description générale
Le dataset étudié contient des transactions bancaires décrites par des variables numériques issues d’une transformation préalable visant à protéger la confidentialité des clients.

Chaque observation correspond à une transaction, associée à une variable cible indiquant son caractère frauduleux ou non.

### 3.2 Analyse descriptive et tableaux statistiques
L’analyse des tableaux statistiques met en évidence :
- une proportion extrêmement faible de transactions frauduleuses,
- des montants atypiques plus fréquents dans les cas de fraude,
- une dispersion plus élevée pour certaines variables associées aux fraudes.

**Analyse critique :**  
Ces résultats confirment que la fraude ne peut être détectée par de simples règles métiers et nécessite des modèles capables de capter des schémas complexes.

---

## 4. Prétraitement des données

### 4.1 Nettoyage et normalisation
Les données ont été vérifiées afin d’éliminer les incohérences. Les variables *Time* et *Amount* ont été standardisées afin d’assurer une comparabilité entre les observations.

### 4.2 Gestion du déséquilibre des classes
Le déséquilibre marqué entre transactions normales et frauduleuses constitue un défi majeur. Des techniques de rééchantillonnage ont été utilisées pour améliorer la capacité des modèles à détecter les fraudes.

**Analyse critique :**  
Un rééquilibrage excessif peut introduire du bruit. Un compromis est donc nécessaire afin de préserver la représentativité des données.

---

## 5. Analyse exploratoire des données (EDA)

### 5.1 Analyse des distributions
Les histogrammes montrent une concentration importante des transactions normales autour de valeurs centrales, tandis que les transactions frauduleuses présentent des distributions plus dispersées.

### 5.2 Analyse des corrélations
La matrice de corrélation révèle une faible corrélation linéaire entre les variables et la cible, suggérant la nécessité de modèles non linéaires.

### 5.3 Analyse comparative par graphiques
Les boxplots mettent en évidence une variabilité accrue et un nombre plus élevé de valeurs aberrantes pour les transactions frauduleuses.

**Lecture graphique :**  
Ces comportements atypiques constituent des signaux faibles exploitables par les algorithmes de Machine Learning.

---

## 6. Modélisation et algorithmes

### 6.1 Algorithmes implémentés
Trois modèles ont été comparés :
- Régression Logistique, utilisée comme référence interprétable,
- Random Forest, capable de capturer des relations complexes,
- Gradient Boosting, optimisant séquentiellement les erreurs.

### 6.2 Méthodologie de validation
Une séparation stricte des jeux de données, associée à une validation croisée, a permis d’assurer la robustesse des résultats.

### 6.3 Analyse comparative des performances
Les tableaux de résultats montrent que les modèles d’ensemble surpassent la régression logistique, notamment en termes de rappel, critère essentiel dans un contexte de fraude.

### 6.4 Analyse de la matrice de confusion
La matrice de confusion révèle une diminution significative des faux négatifs, au prix d’une légère augmentation des faux positifs.

**Interprétation métier :**  
Ce compromis est acceptable, car le coût d’une fraude non détectée est supérieur à celui d’une fausse alerte.

---

## 7. Discussion des résultats
Les résultats obtenus confirment l’importance du choix des métriques et des algorithmes. Les modèles complexes offrent de meilleures performances, mais au détriment de l’interprétabilité.

Du point de vue financier, un modèle performant permet de réduire les pertes et d’améliorer la confiance des clients.

---

## 8. Limites du travail
- dépendance à la qualité des données transformées,
- interprétabilité limitée des modèles avancés,
- absence de variables comportementales détaillées.

---

## 9. Perspectives d’amélioration
- intégration de méthodes de détection d’anomalies,
- exploration de modèles de Deep Learning,
- mise en production en environnement temps réel.

---

## 10. Conclusion
Ce projet met en évidence le rôle clé du Data Science dans la lutte contre la fraude bancaire. L’approche méthodologique adoptée permet de développer un modèle robuste, aligné à la fois avec les exigences académiques et les enjeux financiers.

