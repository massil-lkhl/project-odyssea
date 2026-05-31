#  Project Odyssea
 
> Application de simulation d'agence de voyage accompagnant le client de A à Z.
 
---
 
## Introduction
 
**Project Odyssea** est né d'une expérience de formation (*FreeCodeCamp.org — Responsive Web Design*) où certains workshops portaient sur la création de sites web à thème agence de voyage. Ce projet vise à transformer ce concept en un produit opérationnel permettant aux clients de réaliser des réservations et de bénéficier de multiples services centralisés.
 
Le développement est structuré autour de **jalons progressifs** accompagnés de schématisations détaillées pour guider la construction de l'application.
 
---
 
## Modèle de développement
 
Le projet suit la **méthodologie Prototypage**, choisie pour les raisons suivantes :
 
| Critère | Justification |
|---|---|
|  Évolutivité | Le produit évoluera en plusieurs versions |
|  Mise à l'échelle | Progression des compétences intégrée |
|  Livraisons rapides | Itérations régulières et fonctionnelles |
|  Faible effectif | Adapté à une équipe réduite |
|  Besoins instables | Les spécifications évoluent au fil du temps |
 
> **Note :** La sécurité sera basique dans les premières itérations (hachage des mots de passe) puis renforcée progressivement lors des phases de mise en production réelles.
 
---
 
## Expression des besoins (MoSCoW)
 
###  Must Have — Version 1
 
- Authentification : login / signin / logout
- Recherche de voyages
- Réservation fictive
- Base de données
- Fiche de voyages
###  Should Have
 
- Filtrage des voyages
- Ajout / Suppression / Modification de voyages (CRUD)
###  Could Have
 
- Assistant visa
- Système de recommandation
- Chatbot intégré
- Prédiction des prix via Machine Learning
- Intégration Air France
- Intégration Amadeus
- API compagnies aériennes
###  Won't Have (hors périmètre)
 
- Paiement réel
- Application mobile
- Système de remboursement
- Gestion juridique réelle des visas
---
 
##  Contexte métier
 
L'application répond à un besoin de **centralisation** des ressources liées au voyage. La majorité des informations étant actuellement éparpillées, *Odyssea* unifie l'ensemble et guide l'utilisateur de A à Z pour voyager sans imprévus.
 
### Acteurs principaux
 
```
├── 👤 Utilisateurs
├── 🛠️ Administrateurs
└── 👥 Employés
```
 
---
 
##  Spécifications techniques
 
Chaque spécification est évaluée selon les attributs suivants :
 
| Attribut | Description |
|---|---|
| **État** | `Fini` / `En cours` / `Non débuté` |
| **Effort** | Durée estimée en jours |
| **Risque** | Criticité de la spécification |
| **Cible** | Acteur(s) concerné(s) |
| **Stabilité** | `> 50%` = stable / `< 50%` = à risque de remplacement |
| **Description** | Besoins fonctionnels et non fonctionnels détaillés |
 
---
 
##  Stack technique
 
```
Frontend     →  HTML · CSS · JavaScript
Base données →  SQL (via XAMPP)
Design       →  Figma · Canva
Modélisation →  Software Ideas Modeler · AnalyseSI
IDE          →  VS Code
Backend          →  Python
Framework Backend → Flask
```
 
---
 
##  Schématisations & Diagrammes
 
Chaque fonctionnalité sera accompagnée de ses diagrammes explicatifs :
 
- **UML** : diagrammes d'états, d'activités, de cas d'utilisation
- **MCD / MLD** : modélisation conceptuelle et logique des données
- **MOO** : modélisation orientée objet
- **BCE** : modèle Boundary-Control-Entity
---
 
##  Roadmap
 
```
v1.0  →  Auth + Recherche + Réservation fictive + Base de données
v2.0  →  CRUD voyages + Filtrage
v3.0  →  Chatbot + Recommandations + Assistant visa
v4.0  →  ML (prédiction des prix) + Intégrations API
```
 
---
 
##  Licence
 
Projet personnel à but pédagogique — *toute utilisation doit mentionner l'auteur original.*
 
Schématisations : 

	Pour les besoins étant en cours de production ou non débuté. Des diagrammes seront attribués afin de permettre la compréhension du fonctionnement du produit. Les diagrammes majoritairement utilisés dans ce projet seront : les diagrammes UML (états, activités, cas d’utilisations), MCD, MLD, Modélisation Orientée Objet ainsi que le modèle BCE. Chaque fonctionnalité sera accompagnée de son diagramme à but explicatif du fonctionnement du code. 
