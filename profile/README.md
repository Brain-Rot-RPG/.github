# Brain Rot Chronicles : The Aura Farming Expedition

## 1. Concept Global

Jeu de rôle (Rogue-like) sur navigateur où le joueur incarne un "Brain Rot" qui doit traverser un donjon pour affronter le boss final : “La Grande Suprême Combinacion”.

## 2. Architecture et Données

- Architecture : Le système repose sur des micro-services (Héros, Donjon, Combat, Logs). 
- Bases de données : Utilisation de deux systèmes distincts :
  - Une base pour la gestion des héros et de leurs caractéristiques.
  - Une base dédiée au service de log pour l’historique des actions.

![Figure 2-1 : Architecture logique](images/2-1-architecture-logique.png)

*Figure 2-1 : Architecture logique*

## 3. Système de Jeu (Gameplay)

- Héros : Le joueur peut créer ou sélectionner un héros parmi une liste complète disponible à la connexion.
  - Statistiques : PV (Points de Vie), Niveau, Stat d'attaque, Gold (Or).
  - Inventaire : Objets de soin, bonus d'attaque, bonus de PV, ou objets modifiant les chances de rencontre de combat.
- Donjon et Déplacement :
  - Génération : Les donjons sont générés aléatoirement sous forme d'un arbre.
  - Structure des nœuds : Chaque nœud de l'arbre représente une étape où le joueur effectue l'action de se déplacer. Un nœud peut contenir :
    - Un combat.
    - Un objet (item).
    - Un événement aléatoire lié au donjon.
  - Progression : Le joueur choisit son chemin à travers l'arbre (chemins plus ou moins longs offrant plus ou moins de bonus) jusqu'à atteindre le nœud final du Boss.
- Combat :
  - Se déclenche sur les nœuds de l'arbre ou selon une chance de rencontre.
  - Le combat est un duel qui se termine dès que les PV du héros ou de l'adversaire atteignent 0.

## 4. Service de Log

- Suivi exhaustif de toutes les actions effectuées sur le système.
- Consultation possible de l'historique de manière chronologique ou filtrée par héros.
