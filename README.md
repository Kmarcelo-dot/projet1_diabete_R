# projet 1 : Determinants du Diabete
Portfolio Marcelo KALONJI

## Introduction :
Ce projet vise à prédire l’apparition du diabète chez des patientes adultes à partir de variables médicales et biologiques, à l’aide de méthodes de machine learning supervisé.
Au-delà de la simple prédiction, l’analyse vise également à identifier les facteurs les plus fortement associés au diabète, à mettre en évidence les limites inhérentes aux données utilisées — notamment la présence d’outliers et le déséquilibre entre les classes — et à évaluer de manière réaliste la performance d’un modèle prédictif dans un contexte de données de santé.
Le jeu de données utilisé provient du UCI Machine Learning Repository et concerne exclusivement des femmes d’ascendance Pima Indians.

## Objectif du projet :
L’objectif de ce projet est de prédire si une patiente développera le diabète (classe 1) ou non (classe 0) à partir d’un ensemble de variables cliniques et biologiques. 

Objectifs Spécifiques :
- Identifier les variables cliniques et biologiques les plus fortement associées au diabète ;
- Comparer des modèles prédictifs adaptés
- Évaluer les performances des modèles (sensibilité, spécificité, AUC, etc.)

## Méthodologie
Population d'études :
Femmes d’ascendance Pima Indians, âgées de 21 ans et plus, vivant dans la région de Phoenix (Arizona, États-Unis).

Outils d'Analyse des données :
Le projet est réalisé sous R, avec une extension Big Data via Spark (package sparklyr) pour la phase de machine learning.
Une régression logistique est mise en œuvre, avec une stratégie de validation reposant sur un découpage des données en 80 % pour l’entraînement et 20 % pour le test.

Variables du modèle :
- Pregnancies               :	Nombre de grossesses
- Glucose	                  : Concentration plasmatique en glucose à 2h
- BloodPressure             :	Pression artérielle diastolique (mm Hg)
- SkinThickness             :	Épaisseur du pli cutané tricipital (mm)
- Insulin                   :	Insuline sérique à 2h (mu U/ml)
- BMI	                      : Body Mass Index ou Indice de Masse Corporelle (poids / taille²)
- DiabetesPedigreeFunction	: Fonction de prédisposition génétique au diabète
- Age                       :	Âge (années)
- Outcome                   : 0 = non diabétique, 1 = diabétique

## Limites du Projet 
Ce projet présente plusieurs limites qu’il convient de prendre en compte dans l’interprétation des résultats.

- Qualité des données : présence de valeurs nulles non plausibles biologiquement (Glucose, BMI, Insulin, SkinThickness, BloodPressure), traitées comme manquantes, ce qui peut introduire un biais malgré l’imputation par la médiane.
- Imputation des valeurs manquantes : l’imputation médiane, bien que robuste, réduit la variabilité naturelle des données et peut lisser des profils cliniques réels.
- Présence importante d’outliers : notamment pour la variable Insulin ; la winsorisation limite leur influence mais peut masquer des situations cliniques extrêmes pourtant pertinentes.
- Déséquilibre des classes : surreprésentation des patientes non diabétiques entraînant un biais du modèle vers la classe majoritaire et une sensibilité insuffisante pour la détection des diabétiques.
- Validation externe absente : le modèle n’a pas été testé sur un jeu de données indépendant, ce qui limite l’évaluation de sa robustesse et de sa performance réelle en pratique clinique.
