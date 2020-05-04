# Avracadabra

Guide utilisateur pour la gestion de stock de vrac avec Avracadabra.

!!! warning "Attention"
    Le projet est à ses débuts. Il est grandement prématuré d'envisager d'utiliser
    ce service en production. Certain passage de cette documentation parle au
    présent pour donner l'état fini souhaité, mais la fonctionnalité n'est
    pas nécessairement implémenté ! (cf [Road-map et fonctionnalités](./#road-map-et-fonctionnalites))

## Bienvenue

Ce guide est destiné aux personnes désireuses de gérer des stocks de vrac avec
l'outil [Open Source](https://fr.wikipedia.org/wiki/Open_source) développé par
[Avracadabra](https://github.com/avracadabra). 

La raison d'être d'[Avracadabra](https://www.avracadabra.fr) est faciliter la
mise en oeuvre des modes de vies zéro déchets pour **éradiquer les emballages à
usage unique de la planète.**

Cette documentation est découpé en plusieurs parties:

* [Premiers pas](initialisation/): vous guide dans les premières étapes
de choses à configurer.
* [Cas d'usage](cas_usages/): Procédure pas à pas et explications détaillés
du fonctionnement.
* [Procédure utilisateur](procedures/): listes à cocher succincte précisant
les étapes a faire pour obtenir un résultat. 
* [Administration](architecture/): donnes des informations techniques
sur comment fonctionne la pile applicative, certains choix technique et
pourquoi et quelques informations à destination d'administrateurs du service,
procédure d'installation et points de vigilance.

## Road-map et fonctionnalités

Quel est le projet, où allons nous ? Nous tâchons de détailler ici les points
d'étapes et les différents fonctionnalités implémentées.

!!! note
    Cette liste et les priorités vont évoluer au grès de l'humeur, du contexte
    et des idées 

### Choix des technos et mise en place (en cours)

La première phase consiste à choisir les technologies utilisées, mettre en
oeuvre les projets avec la configuration de l'intégration continue des
fonctionnalités pour permettre, ensuite, d'avancer efficacement, et, avec
une exigence qualité importante:

- [x] Mise en place du projet [stock](/architecture/architecture/#stock)
- [x] Mise en place du projet [api-gateway](/architecture/architecture/#api-gateway)
- [x] Mise en place du projet [backend](/architecture/architecture/#backend)
- [ ] Mise en place de tests d'intégration [QA](/architecture/architecture/#assurance-qualite)
- [ ] Mise en oeuvre de cette documentation
- [ ] Déploiement d'une instance de test

### Gestion des emplacements et conteneurs

L'objectif est de représenter les "emplacements" (nommé "containers" dans AWB)
pouvant stocker des objets physiques. Ou emplacement "virtuel" permettant
d'agréger des données de stock (on peut imaginer une société mère avec plusieurs
entreprises, on voudra alors valoriser les stocks à plusieurs niveau
de la structure).

- [ ] Création d'emplacement parent
- [ ] Génération d'emplacement en masse (définition d'étagères)
- [ ] Visualisation des emplacements (arborescence  ?)
- [ ] Impression des étiquettes (code barre)
- [ ] Assistant de configuration de magasin

### Produits

L'outil permet de récupérer les références produit depuis plusieurs sources
de données de système tiers pour éviter d'encombrer le WMS avec des catalogues
produits dont nous n'aurions pas besoin et éviter les doubles saisies. Un constat
qui a également était fait est que dans les acteurs du vrac actuel, il travail
localement avec des petits artisanats qui n'ont pas nécessairement les moyens ni
le besoin direct de de s'outiller informatiquement (besoin à étudier ?)


A ce stade l'objectif sera de s'appuyer sur 2 sources de données:
 - [ ] Les produits présent dans stock (non créé par un système tiers)
       !!! note
           A ce state aucune interface graphique prévu pour la création de produit
 - [ ] Des données de l'[OpenData](
https://fr.wikipedia.org/wiki/Donn%C3%A9es_ouvertes) grâce à
[Open Food Facts](https://openfoodfacts.org)

A terme (hors scope du sprint) il est envisagé de developer des connecteurs pour
les services de gestion de produit (PIM) ou d'entreprise (ERP) tel que:
- akeneo
- odoo
- treopim
- icecat

- [ ] Le backend est en capacité de rechercher / filtrer par nom, code barre ou sku.
- [ ] Mise en place du mécanisme de création de produit dans *stock* avec enrichissement
      de la donnée par le fournisseur.

### Inventaire initiale

L'Objectif sera de permettre de faire le premier inventaire pour initialiser
le stock et visualiser l'état des stocks.

- [ ] Interfaces graphique dans le *backend* permettant un premier inventaire
      basé sur des produits [Open Food Facts](https://openfoodfacts.org) sélection par
      code barre.
- [ ] Visualisation des stocks par emplacement ou par produit

### Mobile

Développement de l'application pour mobilie offline.

- [ ] Choix des technos
- [ ] Mise en place de l'intégration continue et tests d'intégration
- [ ] L'application mobile est en capacité de faire le premier inventaire
      de manière offline et l'on peut visualiser l'état des stock dans le backend
      quand le réseau est "retrouvé" et l'inventaire finalisé.

### Inventaire

Permettre différent scénario d'inventaire:

- [ ] Inventaire partiel sur une sous zone d'emplacements
- [ ] Inventaire par emplacement
- [ ] Inventaire par produit

L'interface mobile a la capacité:

- [ ] La visualisation du nombre théorique de produit avec capacité d'indiquer
      le nombre de présent et ainsi affichage des écarts.
- [ ] Scan de l'ensemble des containers et articles.

### Gestion de réception

Capacité de réceptionner des marchandises non pré-déclaré.

### Gestion du ré-approvisionnement magasin

### Gestion des sortie (ventes)

### Gestion des rebuts

### Traçabilité des contenants clients

Permet d'afficher des alertes du type vous avez mis un produit ménagé la fois
précédente, je ne peux pas vous vendre de la farine dedans aujourd'hui !

Permet d'afficher les informations produit au consommateur.

### Gestion d'entrepôt

Imaginons maintenant que l'on a un entrepôt pour gérer de plus grand stock
et approvisionner 2 arrières boutiques en magasin

### Mécanisme de réservation et prévision de stock


### Gestion de préparation de commandes

Capacité de préparation de commande dans un entrepôt avec expédition (connecteur
outils transporteurs)

### Gestion des retours

Par exemple les contenants pourraît être suivi et retourné par le destinataire !

### Gestion de fabrication / production artisanale

On fait désormais notre propre farine ! pourquoi ne pas la transporter en
vrac ?! :wink:


## En savoir plus sur Avracadabra

Pour En savoir plus [Avracadabra](https://www.avracadabra.fr), vous pouvez
également nous suivre sur
[facebook](https://www.facebook.com/Avracadabra-825697851127286) et 
[twitter](https://twitter.com/avracadabra1)
