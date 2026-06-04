# Conception de la Base de Données - Version 1

## Raisonnement de Conception

Dans le cadre de ce projet, le développement est réalisé par itérations successives en appliquant le principe **KISS (Keep It Simple, Stupid)** de l'ingénierie logicielle. L'objectif est de concevoir une première version fonctionnelle et évolutive avant d'introduire progressivement des fonctionnalités plus complexes.

La Version 1 se concentre principalement sur les besoins fondamentaux de l'utilisateur :

* Création d'un compte utilisateur ;
* Recherche de voyages ;
* Application de filtres de recherche ;
* Consultation des offres disponibles ;
* Réservation de billets d'avion.

Ces fonctionnalités impliquent la présence de deux entités principales :

* **Client**
* **Billet d'avion**

La base de données sera enrichie lors des versions futures afin d'intégrer :

* Les administrateurs du produit ;
* Les systèmes de gestion avancés ;
* De nouvelles relations entre les entités ;
* Les mécanismes de sécurité.

Cette phase de conceptualisation permet également de remettre en question certaines interfaces utilisateur telles que :

* `inscription.html`
* Les pages de consultation des voyages
* Les formulaires de réservation

D'un point de vue produit, l'information recherchée par l'utilisateur doit être immédiatement accessible afin de réduire les abandons et maximiser les conversions.

La structure de la table **BilletAvion** a été conçue à partir :

* De l'analyse des plateformes concurrentes ;
* De l'étude de l'API Amadeus ;
* Des données réellement retournées par les services de réservation aérienne.

---

## Exemple de Données Fournies par l'API Amadeus

```json
{
  "type": "flight-offer",
  "id": "1",
  "price": {
    "currency": "EUR",
    "total": "450.25",
    "base": "380.00"
  },
  "itineraries": [
    {
      "duration": "PT9H35M",
      "segments": [
        {
          "departure": {
            "iataCode": "CDG",
            "at": "2026-07-15T08:00:00"
          },
          "arrival": {
            "iataCode": "LHR",
            "at": "2026-07-15T09:15:00"
          },
          "carrierCode": "BA",
          "number": "303"
        }
      ]
    }
  ]
}
```

---

# Modélisation des Données

## Modèle Conceptuel de Données (MCD)

La première version comporte deux tables principales :

### Client

Informations relatives aux utilisateurs de la plateforme.

### BilletAvion

Informations relatives aux offres de transport aérien.

### Association : Organiser

Cette association représente les réservations effectuées par les clients.

### Cardinalités

```text
Client (0,N) ----- Organiser ----- (0,N) BilletAvion
```

Justification :

* Un client peut consulter les offres sans effectuer de réservation.
* Un client peut réserver plusieurs voyages.
* Un même billet peut être réservé par plusieurs voyageurs selon la capacité disponible.
* L'API Amadeus confirme cette logique grâce à l'attribut `travelerId`.

---

## Modèle Logique de Données (MLD)

Le modèle logique respecte :

* Les règles de transformation Merise ;
* La Troisième Forme Normale (3FN).

L'association **Organiser** devient une table physique d'association car les cardinalités maximales sont de type N:N.

### Attributs ajoutés à Organiser

| Attribut          | Description                                |
| ----------------- | ------------------------------------------ |
| date_organisation | Date de réservation                        |
| nb_voyageurs      | Nombre de voyageurs                        |
| prix_reservation  | Prix du billet au moment de la réservation |

Ces informations permettent de conserver un historique cohérent des réservations.

---

# Choix Technologiques

## Système de Gestion de Base de Données

### Solution retenue

* SGBD : MySQL
* Environnement : XAMPP

### Justification

Les données manipulées possèdent une structure fortement contrainte :

* Un utilisateur doit fournir certaines informations obligatoires.
* Un voyage nécessite des champs précis.
* Les relations entre les entités sont clairement définies.

Une base relationnelle SQL est donc plus adaptée qu'une base NoSQL.

### Alternatives envisagées

| Technologie | Statut      |
| ----------- | ----------- |
| MySQL       | Retenue     |
| PostgreSQL  | Possible    |
| MongoDB     | Non retenue |

MongoDB offre davantage de flexibilité mais celle-ci n'est pas nécessaire pour les besoins de la Version 1.

---

## Outil de Modélisation

L'outil utilisé est :

**AnalyseSI v0.80**

Fonctionnalités utilisées :

* Création du MCD ;
* Génération automatique du MLD ;
* Génération du dictionnaire de données.

### Limites observées

Certaines limitations ont été identifiées :

* Types de données parfois incomplets ;
* Génération SQL comportant plusieurs erreurs ;
* Différences entre le dictionnaire généré et l'implémentation réelle.

Une adaptation manuelle du schéma SQL est donc nécessaire.

---

# Perspectives d'Évolution

## Version 2

* Gestion des administrateurs ;
* Gestion des offres ;
* Interface d'administration ;
* Amélioration des relations métier.

## Version 3

* Sécurité avancée ;
* Optimisation des performances ;
* Gestion des paiements ;
* Historisation complète des opérations.

---

# Limites de Sécurité

 **Important :**

Dans cette version expérimentale, les mots de passe sont stockés en clair dans la base de données.

Cette décision est volontaire et vise uniquement à simplifier le développement de la Version 1.

L'implémentation des mécanismes de sécurité sera réalisée dans les versions ultérieures :

* Hachage des mots de passe avec Bcrypt ;
* Hachage des mots de passe avec Argon2 ;
* Protection contre les attaques par force brute ;
* Gestion des rôles et permissions ;
* Sécurisation des accès administrateurs.

Cette dette technique est identifiée et planifiée dans la feuille de route du projet.

}
