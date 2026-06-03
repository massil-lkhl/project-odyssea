#  Spécification Technique : Module Recherche & Filtrage dynamique

## Description du Besoin Fonctionnel
Ce module est le cœur de l'expérience utilisateur d'Odyssea. Il a pour objectif de permettre à l'utilisateur de trouver la destination idéale le plus rapidement possible en évitant les frictions, favorisant ainsi le tunnel de conversion vers la réservation fictive.
Le périmètre fonctionnel défini pour la **Version 1.0.0** impose :
* Une exploration fluide directement depuis la page d'accueil (`index.html`).
* Un système de filtrage combinatoire (croisement dynamique des critères : destination, budget, nombre de voyageurs).
* Une gestion du cas critique "zéro résultat" pour éviter l'abandon de l'utilisateur.

---

### Analyse des Nœuds Clés du Flux

1. **Le Choix d'Entrée (Index vs Recherche Avancée) :** Dès son arrivée sur `index.html`, l'utilisateur a deux options graphiques. S'il souhaite une navigation rapide, il interagit directement sur la page principale. S'il a un besoin précis non couvert, il bascule sur la page dédiée `research.html`.
2. **Le Nœud de Décision des Filtres :** Ce losange évalue si la base de données renvoie des correspondances. 
   * **Flux Nominal :** Des voyages correspondent -> Affichage des cartes de séjours -> Consultation de la fiche détaillée (`trip.html`).
   * **Flux Alternatif de Secours (Gestion de l'échec UX) :** Si les filtres rapides de l'index sont trop restrictifs (0 résultat), le système ne bloque pas l'utilisateur sur une page blanche. Il affiche dynamiquement un bouton de secours redirigeant vers la recherche avancée.
3. **Le Nœud de Fusion (Merge) de Sortie :** Les trois parcours de découverte mènent au même point de convergence : la consultation d'une offre. L'authentification n'est déclenchée qu'en fin de flux (*Lazy Authentication*), juste avant l'étape de réservation, afin de ne pas décourager l'utilisateur durant sa phase d'exploration.

---

## Journal de Bord & Évolutivité (UX Optimization)

Conformément à notre démarche basée sur le **modèle de prototypage**, ce module et ses interfaces ont évolué au fil de l'analyse UML :

* **v0.1.0 (Optimisation UX suite à l'UML) :** * *Évolution Interface :* Décision d'intégrer la division des filtres directement au-dessus des offres sur la page `index.html` (Bandeau horizontal).
  * *Évolution Algorithmique :* Introduction d'une logique combinatoire permissive. Les filtres gèrent le croisement strict (**Pays ET Prix**) mais acceptent le cumul de critères (**Espagne OU Italie** via des cases à cocher), ce qui sera traduit en SQL par des clauses dynamiques `WHERE ... AND` et `WHERE ... IN ()`.
  * *Évolution Traitement :* Ajout de la branche de redirection vers la recherche poussée en cas de recherche infructueuse.
