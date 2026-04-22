# 🛫 Maintenance Prédictive : Estimation de la RUL (Remaining Useful Life)
> Projet de Data Science Industrielle | Dataset NASA C-MAPSS

## 📋 Résumé du Projet
Ce projet implémente une solution de Maintenance Prédictive (PdM) pour des turboréacteurs d'avions. L'objectif est de prédire la Durée de Vie Utile Restante (RUL) — le nombre de cycles de vol avant une défaillance critique — en analysant les flux de données provenant de 21 capteurs (température, pression, vitesse).

L'enjeu : Passer d'une maintenance préventive rigide à une approche proactive, permettant de réduire les coûts opérationnels et d'éviter des pannes catastrophiques.

---

## 🔍 Analyse Approfondie des Données (EDA)
L'intelligence du modèle repose sur une compréhension fine de la physique du système. Voici l'analyse des résultats obtenus :

### 📉 1. Comportement Temporel des Capteurs

![Evolution des Capteurs](/assets/images/a-ML-7.png)
*Figure1: Dégradation des capteurs*
* Analyse : On observe que certains capteurs (comme les capteurs 2, 4, 7, 11, 12, 15) présentent une tendance très marquée (ascendante ou descendante) à mesure que le temps passe. 
* Interprétation : Le point de rupture se situe souvent après le cycle 120. Avant cela, le signal est stable ; après, la dégradation s'accélère. C'est cet indicateur que le modèle doit capter pour prédire l'imminence d'une panne.

### 🌡️ 2. Distribution et Variabilité

![Histogramme1](/assets/images/a-ML-4.png)
*Figure2: Modèle random-forest *

![Histogramme2](/assets/images/a-ML-5.png)
*Figure3: Modèle XGBoost*

* Analyse : Les histogrammes révèlent que certains capteurs ont une distribution bimodale ou très étalée, tandis que d'autres sont "plats" (capteurs statiques).
* Décision Technique : J'ai procédé à une réduction de dimensionnalité en supprimant les capteurs constants qui n'apportent aucun signal de dégradation, optimisant ainsi le temps de calcul.

### 🗺️ 3. Corrélation des Features

![Matrice de Corrélation](/assets/images/a-ML-5.png)
*Figure4: Comparaison des modèles de prédiction*

* Analyse : La matrice montre des corrélations proches de 1 (ou -1) entre certains capteurs et le temps (cycle). 
* Interprétation : Cela confirme que l'usure mécanique est directement corrélée à des variables physiques spécifiques (ex: augmentation de la température de sortie de turbine). Ces variables ont été priorisées lors du *Feature Engineering*.

---

## 🛠️ Pipeline Technique & Modélisation

### 1. Pré-traitement (Data Wrangling)
* Standardisation : Utilisation du StandardScaler pour normaliser les unités hétérogènes (Pressions vs Températures).
* Labeling : Création d'une fonction de décompte de RUL basée sur l'historique complet de chaque moteur.

### 2. Comparaison des Modèles
J'ai mis en compétition trois architectures pour identifier le meilleur compromis précision/fiabilité :

| Modèle | Performance (RMSE) | Observation |
| :--- | :--- | :--- |
| Random Forest | ~18 cycles | Bonne base, mais peine sur les extrêmes. |
| XGBoost | ~14 cycles | Meilleur résultat. Capture parfaitement les relations non-linéaires. |
| LSTM (RNN) | ~16 cycles | Très performant pour la mémoire séquentielle des séries temporelles. |

### 3. Logique de Sécurité (Score NASA)

* Analyse du Graphique : Le modèle suit fidèlement la courbe de dégradation réelle.
* Sécurité : J'ai intégré un score asymétrique qui pénalise plus lourdement les prédictions tardives. En aéronautique, prédire qu'un moteur tiendra 20 cycles alors qu'il n'en reste que 10 est inacceptable. Mon modèle favorise des alertes légèrement anticipées pour garantir la sécurité.

  ![Histogrammes](/assets/images/a-ML-6.png)
  *Figure5: Tableau de bord*

---

## 🚀 Déploiement : Dashboard de Décision
Pour rendre ce projet actionnable, j'ai développé une interface interactive avec Plotly Dash :
* Suivi en temps réel : Visualisation de la santé de chaque moteur de la flotte.
* Alertes Automatiques : Indicateurs visuels (NORMAL / ATTENTION / CRITIQUE) basés sur les seuils de RUL prédits.

  *Figure6: Degré d'importance de chaque capteur*

  ![Histogrammes](/assets/images/a-ML-1.png)
  ![Histogrammes](/assets/images/a-ML-2.png)
  ![Histogrammes](/assets/images/a-ML-3.png)

---

## ⚙️ Stack Technique
* Langage : Python (Pandas, NumPy)
* Machine Learning : Scikit-learn, XGBoost
* Deep Learning : TensorFlow/Keras (Architectures LSTM)
* Visualisation : Matplotlib, Seaborn, Plotly Dash

---

## 📈 Conclusion
Ce projet démontre ma capacité à gérer un cycle complet de MLOps industriel : de l'analyse physique de capteurs bruts jusqu'au déploiement d'un outil d'aide à la décision. Cette expertise est directement transférable dans les secteurs de l'automobile, de l'énergie et de l'aérospatiale.

---
*Ce projet fait partie de mon portfolio pour ma recherche d'alternance en Systèmes Embarqués et IA.*
