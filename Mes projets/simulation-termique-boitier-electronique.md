# 🌀 Simulation Thermo-Aéraulique de Précision : Boîtier Électronique


## 🔬 Vision du Projet
Ce projet consiste en une étude approfondie de la **fiabilité opérationnelle** d'un système électronique critique. En utilisant la simulation numérique des fluides (CFD), j'ai modélisé les phénomènes de transfert thermique et de dynamique des gaz pour valider l'intégrité du système sous contraintes thermiques sévères.

L'objectif est d'assurer qu'aucun composant ne dépasse sa température critique de fonctionnement, garantissant ainsi la longévité du matériel.

---

## 🛠️ Paramétrage & Environnement de Simulation
Une attention particulière a été portée à la fidélité des conditions aux limites pour obtenir des résultats hautement prédictifs :

### 📐 Domaine de Calcul & Maillage
* **Volumétrie optimisée :** Domaine de calcul de **120 x 40 x 80 mm**, calibré pour capturer les interactions turbulentes sans perte de précision.
* **Maillage adaptatif :** Utilisation d'un maillage automatique de **Niveau 3**, offrant un ratio optimal entre résolution géométrique et convergence du solveur.

### 🌬️ Conditions de Flux et Thermiques
* **Vitesse d'entrée forcée :** Flux d'air de **0,500 m/s** injecté par les ports d'entrée, simulant un refroidissement actif efficace.
* **Charge Calorifique :** Dissipation thermique volumique de **5,000 W** appliquée aux sources de chaleur (puces/CPU), modélisant une charge processeur intensive.
* **Conditions Ambiantes :** Simulation réalisée à **20,05 °C** et **101 325 Pa** (Pression atmosphérique standard).
  
![Paramètres1](/assets/images/parametres-simulation-1.jpg)
  *Figure1: Conditions ambiantes*


---

## 📊 Science des Matériaux & Physique
L'étude intègre des propriétés physiques avancées pour une modélisation réaliste des échanges :

* **Matériau Structurel :** Nylon 6 (Polymère technique).
    * **Densité :** 1120 kg/m³
    * **Conductivité thermique :** 0,286 W/(m·K)
    * **Chaleur spécifique :** 1620 J/(kg·K)
* **Physique de l'Écoulement :**
    * Prise en compte des **effets gravitationnels** ($g = -9,81 m/s^2$) pour la convection naturelle.
    * Gestion de la **viscosité dynamique** de l'air en fonction de la température.
    * Régime de transfert thermique conjugué (Conduction dans les solides + Convection dans les fluides).
      
![Paramètres2](/assets/images/parametres-simulation-2.jpg)
*Figure2: Paramètres d'écoulement*

---

## 🚀 Analyse des Résultats & Convergence
Le modèle a été poussé jusqu'à **4 000 transferts** pour garantir une stabilité parfaite des variables calculées.

### Points Clés de l'Analyse :
1. **Optimisation des Flux :** Identification des zones de recirculation et des "angles morts" aérauliques.
2. **Gradient Thermique :** Cartographie précise de la distribution de chaleur pour valider le placement des composants sensibles.
3. **Barrière Adiabatique :** Configuration des parois extérieures en mode adiabatique pour isoler et comprendre uniquement le comportement interne du boîtier.
   
   ![Visualisation](/assets/images/exterieur-boitier.jpg)
   *Figure3: Visualisation extérieure*
   
   ![Visualisation](/assets/images/interieur-boitier.jpg)
   *Figure4: Visualisation intérieure*

4. ## Rapport et code source
 - [Télécharger le rapport TD3 (PDF)](/assets/images/Rapport%20boitier%20electronique.pdf)

> **Synthèse de l'Ingénieur :** Cette simulation démontre une maîtrise de l'outil **Flow Simulation** et une capacité à interpréter des données CFD complexes pour prendre des décisions de design robustes en ingénierie électronique.

---
*Projet réalisé par Dimitri Bahanag – Spécialisation Systèmes Embarqués & Mécatronique*
