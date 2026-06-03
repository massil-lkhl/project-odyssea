## Version 1.0.0

| Attribut | Description |
|---|---|
| **Version** | v1.0.0 |
| **Avancement** | `En cours` |
| **Effort / Durée** | 1 mois |
| **Stabilité** | `> 70%` |
| **Stack Technique** | HTML5, CSS3, JavaScript (Vanilla), Python (Flask), MySQL |

### Expression des Besoins (V1)

#### Spécifications Fonctionnelles
* **Système d'Authentification :** Permettre l'inscription, la connexion et la déconnexion des utilisateurs (`forms.html`).
* **Moteur de recherche & Filtrage dynamique :** Permettre aux utilisateurs de filtrer les voyages simultanément par prix, destinations et nombre de personnes directement depuis la page principale.
* **Fiches Voyages & Réservation :** Permettre la consultation détaillée d'un voyage (`trip.html`) et la simulation d'une réservation fictive en base de données.

#### Spécifications Non Fonctionnelles & Techniques
* **Architecture API :** Mise en place d'une architecture découplée avec une API REST (Flask) pour faire communiquer le Front-end et le Back-end.
* **Persistance des données :** Stockage et gestion des données (utilisateurs, voyages, réservations) intégralement sur un serveur de base de données relationnelle MySQL local (XAMPP).
* **Performance / UX :** Prise en charge du non-chargement (recherche vide) avec redirection ou message de secours vers la recherche avancée.
* **séries de tests :** Stockage de seed samples sql afin de permettre le test du fonctionnement de l'API, le backend ainsi que la sécurité de la BDD en empechant les valeurs invalides.

## Version 2.0.0 

| Attribut | Description |
|---|---|
| **Version** | v2.0.0 |
| **Avancement** | `Planifié` |
| **Effort / Durée** | À définir (Phase d'industrialisation) |
| **Stabilité** | `En cours de définition` |
| **Stack Technique** | Stack V1 + API Amadeus, Bibliothèques de hachage (ex: Bcrypt), Librairies de Data Viz (ex: Chart.js) |

### Évolution des Besoins (V2)

#### Spécifications Fonctionnelles
* **Espace Back-Office (Admin / Product Team) :** Implémentation d'une interface de gestion (CRUD complet : Ajouter, Modifier, Supprimer un voyage) et d'un tableau de bord (Dashboard) statistique.
* **Gestion multi-profils :** Système d'authentification avancé capable de rediriger l'utilisateur vers son interface dédiée selon son rôle (Client ➡️ Index / Admin & Product Team ➡️ Dashboard).
* **Données réelles (API externe) :** Connexion de l'application à l'acteur secondaire **API Amadeus** pour récupérer des offres et des tarifs de vols en temps réel, remplaçant ainsi les données fictives de la V1.

#### Spécifications Non Fonctionnelles & Techniques
* **Sécurité & Hachage :** Protection des données d'authentification par l'implémentation d'algorithmes de hachage stricts (ex: Bcrypt) pour sécuriser les mots de passe en base de données.
* **Collecte de données (Analytics) :** Mise en place d'un système de tracking discret pour stocker le nombre de clics par annonce et par filtre dans la BDD, fournissant la matière première au dashboard de la Product Team.
  
