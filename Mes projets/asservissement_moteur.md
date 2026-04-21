---
layout: post
title: "Asservissement Angulaire de Moteur à Courant Continu (MCC)"
date: 2026-04-04
categories: [Mechatronics, Automation]
tags: [Arduino, Matlab, Control-Systems, ESIEA]
---

# ⚙️ Asservissement Angulaire de Moteur à Courant Continu

## Présentation du Projet
Ce projet, réalisé dans le cadre du cursus ingénieur à l'**ESIEA**, porte sur la conception et la mise en œuvre d'un système d'asservissement de position pour un disque entraîné par un moteur à courant continu.L'objectif est de contrôler précisément l'angle du disque en utilisant des stratégies de correction analogiques et numériques via une carte **Arduino Mega**.



## Architecture Technique
Le système est modélisé par une fonction de transfert du second ordre intégrant :
* **Actionneur** : Moteur à courant continu couplé à un réducteur de rapport.
* **Capteur** : Potentiomètre fournissant une tension $V_p$ proportionnelle à la position angulaire $\theta_s$ ($V_p = K\theta_s$).
* **Contrôle** : Traitement du signal d'erreur via Arduino pour générer une commande PWM.
* * ![*Dispositif1*](/assets/images/montage_moteur.jpg)
* *Figure 1: Schéma du montage*
* * ![*Dispositif2*](/assets/images/visualisation_mcc.jpg)
* *Figure 2: Schéma et visualisation*

## Réalisations Principales

### 1. Modélisation & Identification
* **Détermination de la fonction de transfert théorique** : $T(p) = \frac{A}{p(1+\tau p)}$.
* **Identification expérimentale** : Mesure du premier dépassement ($D_1\%$) et de la pseudo-période ($T_p$) sur oscilloscope pour identifier le coefficient d'amortissement $m$ et la pulsation propre $\omega_0$.

### 2. Correction Proportionnelle
* Mise en place d'une boucle à retour unitaire ($A_b = 1$).
* Analyse de l'influence du gain $A_d$ sur la stabilité, la rapidité (temps de montée $t_m$) et la précision.
* ![*Analyse gain1*](/assets/images/a-bode-ad-4.png)
* *Figure 3: Diagramme de bode pour ad=4*
* ![*Analyse gain2*](/assets/images/a-ad-4.png)
* *Figure 4: Réponse pour ad=4*
* ![*Analyse gain3*](/assets/images/a-valeurs-ad.png)
* *Figure 5: Influence du gain sur la réponse*

### 3. Correction par Avance de Phase
* Conception d'un correcteur de type $C(p) = K_c \frac{1 + \alpha Tp}{1 + Tp}$ avec $\alpha > 1$.
* Optimisation des paramètres pour apporter une avance de phase (ex: $10^\circ$) et améliorer la marge de phase du système.

### 4. Simulation & C.A.O. (MATLAB/Simulink)
* Utilisation de **MATLAB** pour le tracé des diagrammes de **Bode** et l'analyse des marges de gain et de phase.
* * ![*Analyse correcteur1*](/assets/images/a-bode-correcteur.png)
* *Figure 6: Bode avec correcteur*
* * ![*Analyse correcteur2*](/assets/images/comparaison-sortie-correcteur.png)
* *Figure 7: Comparaison entre correcteur et gain ad=4*
* Modélisation sous **Simulink** pour valider le comportement dynamique en boucle fermée.

## Environnement Technologique
* **Hardware** : Arduino Mega, Moteur CC, Potentiomètre, Oscilloscope, Alimentation $\pm 12V$.
* **Software** : MATLAB, Simulink, Arduino IDE (C++), Bibliothèque `SimpleTimer`.

---
*Projet réalisé à l'ESIEA - École d'Ingénieurs du Monde Numérique.*
