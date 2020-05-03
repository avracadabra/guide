# Architecture

L'ensemble des codes source de la stack applicative sont hébergés sous
l'organisation [Avracadabra](https://github.com/avracadabra).

La pile applicative est composée de 4 éléments: [stock](./#stock),
[api-gateway](./#API Gateway), [backend](./#backend) et [mobile](./#mobile).

A ne pas manquer le chapitre [Assurance qualité](./#Assurance qualité)

## Stock

Le dépôt [stock](https://github.com/avracadabra/stock) est le service de gestion
de stock a proprement parlé (**WMS**: Warehouse Management System), développé avec
le framework[^1] [AnyBlok](https://github.com/AnyBlok/AnyBlok) et
principalement basé sur les modules fournis par
[AWB: (Anyblok Warehouse management system Base)](
https://github.com/AnyBlok/anyblok_wms_base).

Pourquoi AnyBlok ?

**AnyBlok** est un framework plutôt récent (moins de 10 ans) dont j'ai
(Pierre Verkest) confiance et contribue ! Il repose sur des librairie connue
tel que [SqlAlchemy](https://www.sqlalchemy.org/),
[pyramid](https://trypyramid.com/).

## API Gateway

Le dépôt [api-gateway](https://github.com/avracadabra/api-gateway) est le code
source du service passerelle (ou proxy) jouant un rôle d'intermédiaire entre
les interfaces utilisateurs ([backend](./#backend) et [mobile](./#moble)) et
les différents services métiers.

### Aspects techniques

Cette passerelle expose les données au travers d'API [GraphQL](https://graphql.org/),
dans l'objectif de découpler, un minimum, le code source des interfaces
utilisateurs et des services métiers.

Le moteur GraphQL [tartiflette](https://tartiflette.io/) est utilisé car il
est prévu pour fonctionner naturellement avec asyncio.

Le service est donc totalement conçu pour fonctionner en async/io avec notamment:

- [starlette](https://www.starlette.io/): Un framework [ASGI](https://asgi.readthedocs.io/en/latest/)
- [tartiflette-asgi](https://tartiflette.github.io/tartiflette-asgi/) qui fait la "glue"
entre *starlette* et *tartiflette*.
- [uvicorn](https://www.uvicorn.org/) le serveur ASGI.
- [Gunicorn](https://gunicorn.org/) qui permet de gérer les processus (ASGI) de
manière résiliente.

### Cache

A venir...

## backend

Le dépôt [backend](https://github.com/avracadabra/backend) est une application
[VueJs](https://vuejs.org) dont les cas d'usage sont pensé pour PC ou tablette
et uniquement testé sur les navigateurs PC.

## mobile

Le dépôt [mobile](https://github.com/avracadabra/mobile) est une application
mobile, outil asynchrone prévu pour gérer les déconnexions réseau (mode offline)
permettant de travailler dans des locaux ou le reseaux serait faible avec 
un smartphone ou un scanner sous Android.

## Assurance qualité

Le dépôt [QA](https://github.com/avracadabra/QA) contient:

- Les test d'intégration sous la forme de [Programmation pilotée par le comportement](
https://fr.wikipedia.org/wiki/Programmation_pilot%C3%A9e_par_le_comportement)
(BDD: Behavior-driven development) qui doit permettre à un non technique
de comprendre les jeux de test.


[^1]: un *framework* est une boite à outil pour développeur. Il fournis des
      primitives facilement réutilisable.

