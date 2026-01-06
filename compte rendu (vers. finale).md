# Rapport académique – Détection de fraude par carte bancaire

**Auteur : FRIMI Kawtar**  
**Filière : Finance – ENCG Settat**

![me](https://github.com/user-attachments/assets/51d1bb07-7675-43ea-97e6-95dfc1c40744)


---

## 1. Thématique
Cette étude s’inscrit dans le cadre de la **finance quantitative et de la gestion du risque opérationnel**, avec une focalisation sur la **détection automatisée de la fraude bancaire**. Elle mobilise des techniques de *Machine Learning supervisé* afin d’analyser des transactions par carte bancaire et d’identifier des comportements anormaux susceptibles de correspondre à des actes frauduleux.

La problématique traitée est centrale pour les institutions financières modernes, dans un contexte de digitalisation accrue des paiements, d’augmentation du volume transactionnel et de sophistication croissante des schémas de fraude.

---

## 2. Problématique
La fraude bancaire se caractérise par sa **rareté statistique**, sa **forte hétérogénéité** et son **évolution permanente**. Dès lors, une difficulté majeure réside dans la capacité à détecter efficacement des transactions frauduleuses sans perturber excessivement les transactions légitimes.

La problématique centrale peut être formulée comme suit :
> *Comment concevoir un modèle prédictif capable d’identifier les transactions frauduleuses dans un jeu de données massivement déséquilibré, tout en optimisant les performances selon des critères économiquement pertinents ?*

---

## 3. Contexte & Objectif
### Contexte
La digitalisation croissante des paiements a considérablement augmenté le volume de transactions électroniques. Bien que bénéfique pour les usagers, cette évolution s’accompagne d’une hausse significative des tentatives de fraude bancaire. Pour les établissements financiers, la détection tardive ou inefficace de ces fraudes engendre des pertes financières directes, une dégradation de la relation client et des risques réglementaires.

Dans ce contexte, les approches traditionnelles basées sur des règles fixes montrent leurs limites face à des schémas de fraude de plus en plus sophistiqués.

### Objectif
L’objectif principal de ce projet est de concevoir et d’évaluer un modèle de *Machine Learning* capable de :
- détecter précocement les transactions frauduleuses,
- s’adapter à un jeu de données fortement déséquilibré,
- optimiser les métriques pertinentes du point de vue métier (recall, ROC-AUC),
- fournir un outil d’aide à la décision pour les institutions financières.

---

## 4. Données & Nettoyage
### Description des données
Le jeu de données exploité est issu d’un ensemble de transactions réelles effectuées par carte bancaire. Afin de préserver la confidentialité des utilisateurs, les variables explicatives ont été transformées par *Analyse en Composantes Principales (ACP)*, à l’exception des variables `Time` et `Amount`.

### Tableau récapitulatif

| Élément | Description |
|-------|-------------|
| Nombre d’observations | Environ 284 000 transactions |
| Variables explicatives | V1 à V28 (variables anonymisées), Time, Amount |
| Variable cible | `Class` (0 : transaction légitime, 1 : fraude) |
| Proportion de fraude | Inférieure à 1 % |

### Nettoyage et préparation
- Vérification de l’absence de valeurs manquantes
- Standardisation de la variable `Amount` pour éviter un biais d’échelle
- Séparation des variables explicatives et de la variable cible
- Préparation des données pour l’entraînement supervisé

-------|-------------|
| Nombre d’observations | ~284 000 transactions |
| Variables | Variables numériques (V1 à V28), Time, Amount |
| Variable cible | `Class` (0 : légitime, 1 : fraude) |
| Déséquilibre | < 1 % de transactions frauduleuses |

### Nettoyage effectué
- Vérification des valeurs manquantes (aucune valeur critique)
- Normalisation du montant (`Amount`)
- Séparation claire variables explicatives / cible

---

## 5. Analyse Exploratoire des Données (EDA)

L’analyse exploratoire constitue une étape déterminante, car elle conditionne la compréhension du phénomène de fraude et oriente les choix méthodologiques ultérieurs. Dans un contexte de données réelles et déséquilibrées, l’EDA ne vise pas uniquement la visualisation, mais surtout l’identification de signaux faibles exploitables.

### Insight 1 – Déséquilibre structurel et implications méthodologiques
La proportion extrêmement faible de transactions frauduleuses (inférieure à 1 %) révèle un **déséquilibre structurel** typique des données financières réelles. Cette caractéristique implique que tout modèle naïf prédisant systématiquement la classe majoritaire atteindrait une accuracy élevée, sans pour autant présenter une quelconque utilité opérationnelle. Ce constat justifie le recours à des métriques alternatives et à des modèles capables de gérer des distributions asymétriques.

### Insight 2 – Différences de comportement transactionnel
L’analyse des montants met en évidence des **comportements distincts entre transactions légitimes et frauduleuses**. Les fraudes se concentrent souvent sur des montants atypiques, traduisant soit des tests de cartes à faible valeur, soit des tentatives ponctuelles de montants élevés. Cette hétérogénéité renforce la nécessité de modèles non linéaires.

### Insight 3 – Rôle discriminant de certaines composantes
Certaines variables issues de l’ACP (notamment V10, V14 et V17) présentent des distributions nettement différentes selon la classe. Ces variables concentrent une part significative de l’information discriminante, suggérant que les comportements frauduleux reposent sur des combinaisons spécifiques de signaux latents.

### Figure résumée
La figure suivante illustre les différences de distribution des montants selon la nature des transactions.

```python
import matplotlib.pyplot as plt

plt.hist(df[df['Class']==0]['Amount'], bins=50, alpha=0.5, label='Légitime')
plt.hist(df[df['Class']==1]['Amount'], bins=50, alpha=0.5, label='Fraude')
plt.legend()
plt.title("Analyse comparative des montants de transaction")
plt.xlabel("Montant")
plt.ylabel("Fréquence")
plt.show()
```

---

## 6. Méthodologie

### Approche générale
La démarche méthodologique adoptée repose sur un processus standard en science des données : compréhension métier, préparation des données, analyse exploratoire, modélisation, évaluation et interprétation des résultats.

### Split des données
Les données ont été divisées en ensembles d’entraînement et de test selon une approche *stratifiée* :
- 70 % pour l’entraînement
- 30 % pour le test

Cette méthode garantit le maintien de la proportion de transactions frauduleuses dans chaque sous-ensemble.

### Modèles testés
- **Régression Logistique** : modèle linéaire de référence, apprécié pour sa simplicité et son interprétabilité.
- **Random Forest** : modèle d’ensemble non linéaire, capable de capturer des interactions complexes entre variables.

### Métriques d’évaluation
Compte tenu du déséquilibre des classes, l’évaluation repose principalement sur :
- le *recall* de la classe fraude,
- la *precision*,
- l’aire sous la courbe ROC (ROC-AUC).

---

## 7. Résultats & Interprétations

L’analyse des résultats doit être interprétée à la lumière des contraintes métiers propres à la fraude bancaire, où le coût d’une fraude non détectée dépasse largement celui d’un faux positif.

### Performances comparées

| Modèle | Recall (Fraude) | Precision | ROC-AUC |
|------|----------------|-----------|---------|
| Régression Logistique | Élevé | Moyen | Bon |
| Random Forest | Très élevé | Élevé | Très bon |

### Analyse approfondie
La **régression logistique**, bien que limitée par son caractère linéaire, fournit une base de référence robuste et interprétable. Elle permet d’identifier des tendances générales, mais peine à capturer des interactions complexes.

Le **Random Forest**, en revanche, exploite des ensembles d’arbres de décision capables de modéliser des relations non linéaires et des effets d’interaction. Sa supériorité en termes de recall s’explique par sa capacité à détecter des combinaisons rares de signaux, caractéristiques des comportements frauduleux.

Toutefois, cette amélioration de la détection s’accompagne d’un risque accru de faux positifs. Le choix du modèle optimal doit donc être guidé par une analyse coût-bénéfice intégrant les impacts financiers, opérationnels et relationnels.

------|----------------|-----------|---------|
| Régression Logistique | Élevé | Moyen | Bon |
| Random Forest | Très élevé | Élevé | Très bon |

### Analyse critique
- La **régression logistique** constitue une base robuste et interprétable, mais reste limitée dans la capture de relations non linéaires.
- Le **Random Forest** offre de meilleures performances globales, notamment en termes de rappel, ce qui est crucial pour limiter les fraudes non détectées.
- Le compromis entre *precision* et *recall* doit être ajusté selon les coûts métier associés aux faux positifs et faux négatifs.

------|----------------|-----------|---------|
| Régression Logistique | Élevé | Moyen | Bon |
| Random Forest | Très élevé | Élevé | Très bon |

**Interprétation :**
- Le *recall* est privilégié afin de limiter les fraudes non détectées.
- Le Random Forest offre le meilleur compromis entre détection et stabilité.

---

## 8. Lien avec le sujet (arguments concrets)

Le projet présente une forte cohérence avec les enjeux académiques et professionnels de la finance moderne :
- il traite d’un **cas réel de gestion du risque**,
- il mobilise des **outils quantitatifs avancés** applicables en milieu bancaire,
- il met en évidence l’importance de l’alignement entre **objectifs statistiques et objectifs métier**,
- il illustre le rôle du *Machine Learning* comme outil d’aide à la décision et non comme une fin en soi.

---

## 9. Limites & Recommandations

### Limites
1. Le déséquilibre extrême des données complique l’apprentissage et l’évaluation des modèles.
2. L’anonymisation des variables limite l’interprétation économique des résultats.
3. Certains modèles performants sont moins transparents.
4. Les données ne prennent pas en compte l’évolution temporelle des schémas de fraude.

### Recommandations
- Intégrer des techniques de *rééquilibrage* (SMOTE, undersampling contrôlé).
- Tester des approches séquentielles (modèles temporels).
- Utiliser des méthodes d’explicabilité (SHAP, LIME).
- Adapter dynamiquement les seuils de décision selon le coût de la fraude.

---

## 10. Ouverture et Approche Globale

D’un point de vue global, la fraude bancaire doit être appréhendée comme un **phénomène systémique**, influencé par des facteurs technologiques, comportementaux et réglementaires. Les modèles de *Machine Learning* ne constituent qu’un maillon de la chaîne de valeur de la gestion du risque.

Une approche efficace repose sur l’intégration de ces modèles au sein d’un écosystème décisionnel plus large, combinant surveillance en temps réel, expertise humaine et mécanismes de contrôle interne. Cette complémentarité permet de renforcer la robustesse globale du dispositif antifraude.

---

## Conclusion

Cette étude met en évidence la pertinence du recours aux techniques de *Machine Learning* pour répondre à une problématique centrale de la finance moderne : la détection de la fraude bancaire dans un environnement caractérisé par des données massives, déséquilibrées et dynamiques.

L’analyse exploratoire a permis d’identifier des signaux discriminants malgré la rareté des événements frauduleux, justifiant le choix de modèles capables de capturer des relations non linéaires. Les résultats obtenus montrent que les modèles d’ensemble, tels que le Random Forest, offrent un avantage significatif en termes de détection des fraudes, au prix d’un compromis à gérer entre performance statistique et coût opérationnel.

Au-delà des performances chiffrées, ce travail souligne l’importance d’une approche intégrée, combinant analyse de données, compréhension métier et réflexion stratégique. Le *Machine Learning* apparaît ainsi non comme une solution autonome, mais comme un levier décisionnel au service de la gestion globale du risque bancaire.

En définitive, ce projet illustre la capacité des méthodes quantitatives à renforcer la résilience des institutions financières face à la fraude, tout en ouvrant des perspectives d’amélioration à travers l’intégration de modèles explicables et adaptatifs.

