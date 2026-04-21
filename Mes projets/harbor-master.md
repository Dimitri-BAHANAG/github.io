# Harbor Master - Orchestrateur de Logistique Portuaire Intelligente


## ⚓ Présentation du Projet
**Harbor Master** est un challenge technique intensif réalisé dans le cadre du cursus ingénieur à l'**ESIEA**. L'objectif est de concevoir et développer un client Java autonome capable d'orchestrer en temps réel les flux logistiques d'un terminal portuaire via une API REST.

Le projet simule un environnement complexe où des navires déchargent des conteneurs qui doivent être triés, stockés par zone de spécificité (Standard, Réfrigéré, Hazmat), puis chargés sur des camions ou d'autres navires en respectant des contraintes temporelles strictes (Deadlines).

## 🚀 Défis Techniques & Compétences
Ce projet met en œuvre des concepts avancés de génie logiciel :
* **Modélisation POO Avancée :** Conception d'un modèle métier robuste (Navires, Grues, Conteneurs, Zones de stockage) pour refléter fidèlement l'état du port.
* **Algorithmique & Stratégies de Décision :** Implémentation de plusieurs moteurs de décision (Heuristiques) pour maximiser le score.
* **Intégration API REST :** Consommation d'endpoints HTTP, gestion de l'authentification et parsing de données JSON en temps réel.
* **Robustesse :** Gestion des erreurs réseau, des timeouts et des contraintes métier (capacité des quais, types de grues compatibles).

![Harbor Master](/assets/images/a-challenge-harbor-master.PNG)
**Figure1*: Présentation du projet harbor master*

## 🛠 Architecture du Système
L'application repose sur une boucle de jeu (Game Loop) synchrone :
1. **Observation :** Récupération de l'état actuel du port via `/v1/state`.
2. **Analyse :** Mise à jour du modèle interne et prédiction des arrivées (Anticipation sur 20 ticks).
3. **Décision :** Choix des actions optimales selon la stratégie active.
4. **Action :** Envoi des commandes aux grues via `/v1/action`.
5. **Évolution :** Passage au tick suivant via `/v1/tick`.

![Interface graphique](/assets/images/a-interface-harbor-master.PNG)
**Figure2*: Interface graphique de l'application*

### Stratégies implémentées
Pour répondre aux exigences de performance, le système supporte le changement de stratégie à la volée :
* **Mode Urgentiste :** Priorité absolue aux conteneurs dont la `dueTick` est imminente pour éviter les pénalités.
* **Mode Flux Tendu :** Maximisation du débit de chargement/déchargement pour libérer les quais rapidement.

![Terminal utilisateur1](/assets/images/a-terminal-harbor-master.PNG)
**Figure3*: Terminal utilisateur*

![Terminal utilisateur2](/assets/images/a-terminal-strategie.PNG)
**Figure3*: Terminal utilisateur:CHOIX DE LA STRATEGIE*

## 📋 Règles Métier & Contraintes
Le moteur de décision doit jongler avec plusieurs contraintes critiques :
* **Spécialisation des Zones :** Les conteneurs `REFRIGERATED` doivent impérativement rejoindre la zone `COLD`, et les `HAZMAT` la zone dédiée.
* **Logistique Obligatoire :** Un conteneur ne peut pas être transféré directement d'un bateau à un camion ; il doit transiter par le `YARD` (zone de stockage).
* **Gestion des Grues :** Chaque grue est limitée à une seule action par tick et possède une typologie spécifique de conteneurs qu'elle peut manipuler.

## 📦 Structure du Projet
Le dépôt est organisé selon les standards professionnels :
```text
.
├── src/ # Code source Java
├── livrables/
│ ├── conception/ # Diagrammes UML et plans de tests
│ └── final/ # Rapport de stratégie et résultats de benchmark
├── pom.xml # Gestionnaire de dépendances Maven
└── README.md

## Rapport et code source
 - [Télécharger le rapport TD3 (PDF)](/assets/images/Rapport%20de%20Projet%20CHALLENGES%20TECHNIQUES.docx)
 - [Dépôt GitLab](https://gitlab.esiea.fr/dimitri.bahanag/gestionnaire_traffic_portuaire.git)
