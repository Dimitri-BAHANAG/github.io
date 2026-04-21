---
layout: post
title: "Asservissement Angulaire de Moteur à Courant Continu (MCC)"
date: 2026-04-21
categories: [Mechatronics, Automation]
tags: [Arduino, Matlab, Control-Systems, ESIEA]
---

# ⚙️ Asservissement Angulaire de Moteur à Courant Continu

## Présentation du Projet
[span_0](start_span)Ce projet, réalisé dans le cadre du cursus ingénieur à l'**ESIEA**[span_0](end_span), porte sur la conception et la mise en œuvre d'un système d'asservissement de position pour un disque entraîné par un moteur à courant continu. [span_1](start_span)[span_2](start_span)L'objectif est de contrôler précisément l'angle du disque en utilisant des stratégies de correction analogiques et numériques via une carte **Arduino Mega**[span_1](end_span)[span_2](end_span).



## Architecture Technique
Le système est modélisé par une fonction de transfert du second ordre intégrant :
* **[span_3](start_span)[span_4](start_span)Actionneur** : Moteur à courant continu couplé à un réducteur de rapport $N$[span_3](end_span)[span_4](end_span).
* **[span_5](start_span)Capteur** : Potentiomètre fournissant une tension $V_p$ proportionnelle à la position angulaire $\theta_s$ ($V_p = K\theta_s$)[span_5](end_span).
* **[span_6](start_span)Contrôle** : Traitement du signal d'erreur via Arduino pour générer une commande PWM[span_6](end_span).

## Réalisations Principales

### 1. Modélisation & Identification
* [span_7](start_span)Détermination de la fonction de transfert théorique : $T(p) = \frac{A}{p(1+\tau p)}$[span_7](end_span).
* **[span_8](start_span)Identification expérimentale** : Mesure du premier dépassement ($D_1\%$) et de la pseudo-période ($T_p$) sur oscilloscope pour identifier le coefficient d'amortissement $m$ et la pulsation propre $\omega_0$[span_8](end_span).

### 2. Correction Proportionnelle
* [span_9](start_span)Mise en place d'une boucle à retour unitaire ($A_b = 1$)[span_9](end_span).
* [span_10](start_span)[span_11](start_span)Analyse de l'influence du gain $A_d$ sur la stabilité, la rapidité (temps de montée $t_m$) et la précision[span_10](end_span)[span_11](end_span).

### 3. Correction par Avance de Phase
* [span_12](start_span)Conception d'un correcteur de type $C(p) = K_c \frac{1 + \alpha Tp}{1 + Tp}$ avec $\alpha > 1$[span_12](end_span).
* [span_13](start_span)Optimisation des paramètres pour apporter une avance de phase (ex: $10^\circ$) et améliorer la marge de phase du système[span_13](end_span).

### 4. Simulation & C.A.O. (MATLAB/Simulink)
* [span_14](start_span)[span_15](start_span)Utilisation de **MATLAB** pour le tracé des diagrammes de **Bode** et l'analyse des marges de gain et de phase[span_14](end_span)[span_15](end_span).
* [span_16](start_span)Modélisation sous **Simulink** pour valider le comportement dynamique en boucle fermée[span_16](end_span).

## Environnement Technologique
* **[span_17](start_span)[span_18](start_span)Hardware** : Arduino Mega, Moteur CC, Potentiomètre, Oscilloscope, Alimentation $\pm 12V$[span_17](end_span)[span_18](end_span).
* **[span_19](start_span)[span_20](start_span)Software** : MATLAB, Simulink, Arduino IDE (C++), Bibliothèque `SimpleTimer`[span_19](end_span)[span_20](end_span).

---
*Projet réalisé à l'ESIEA - École d'Ingénieurs du Monde Numérique.*
