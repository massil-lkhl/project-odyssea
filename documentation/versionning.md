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
