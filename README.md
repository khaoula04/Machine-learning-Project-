Projet de Classification des Résultats Scolaires
Ce projet vise à prédire les résultats d’élèves (succès ou échec) à partir de données académiques et personnelles à l’aide de différents modèles de machine learning.

- Contenu du Projet
Analyse exploratoire des données

Nettoyage et prétraitement

Transformation des variables

Séparation train/test

Sélection et entraînement de plusieurs modèles de classification

Évaluation des performances (matrices de confusion, scores ROC, métriques)

Comparaison des modèles

Visualisation des résultats

 1. Analyse exploratoire des données
Avant tout traitement, nous avons procédé à une analyse visuelle des données numériques :

Utilisation de sns.heatmap() pour afficher la matrice de corrélation.

Observation des corrélations fortes avec la variable cible G3.

Suppression de la colonne G3 (note finale) pour éviter toute fuite de données dans le modèle (puisque result en dépend).

 2. Nettoyage et prétraitement
Suppression des variables non pertinentes (G3).

Remplacement des valeurs manquantes ou non numériques ('U') par NaN.

Conversion des variables via pd.to_numeric(errors='coerce').

Séparation des features X et de la variable cible y.

 3. Transformation des données
Standardisation des variables numériques avec StandardScaler pour assurer un bon comportement des modèles sensibles aux échelles (KNN, SVM, etc.).

Traitement automatique des types grâce à apply(pd.to_numeric) plutôt qu’un encodage explicite (car les données sont déjà numériques après traitement).

 4. Séparation des données
Utilisation de train_test_split avec test_size=0.2 pour diviser les données en ensembles d’entraînement et de test.

random_state=42 pour assurer la reproductibilité.

 5. Modélisation
Les modèles suivants ont été entraînés et évalués :

K-Nearest Neighbors (KNN) avec GridSearchCV pour sélectionner le meilleur n_neighbors.

Support Vector Machine (SVM) avec réglage des hyperparamètres C et kernel.

Régression Logistique

Arbre de Décision

Random Forest

(Bonus) : possibilité d’intégrer XGBoost pour une comparaison plus poussée.

 6. Évaluation
Pour chaque modèle, nous avons calculé :

Accuracy

Precision

Recall

F1-score

Matrice de confusion

AUC-ROC (si applicable)

Fonction utilisée : print_metrics() + affichage graphique des courbes ROC.

 7. Courbe ROC comparée
Une courbe ROC combinée a été tracée pour comparer visuellement les performances des modèles sur la capacité à distinguer les classes positives et négatives.

 8. Résultats et interprétation
Les performances ont montré que :

Le Random Forest est le modèle le plus performant avec le meilleur équilibre entre faux positifs et faux négatifs.

Le SVM et l’arbre de décision donnent également de bons résultats mais font légèrement plus d’erreurs sur les cas positifs.

La régression logistique est compétitive mais génère plus de faux positifs.

À noter
Une partie du dataset a été enrichie par des données synthétiques générées via des outils d’intelligence artificielle afin d'augmenter la représentativité de certains profils sous-représentés dans les données originales.

