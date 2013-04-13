# Pokémon battle

## Univers

Le projet Pokémon battle est une adaptation des jeux de programmation comme 
[Core War](http://fr.wikipedia.org/wiki/Core_War) ou [Robocode](http://robowiki.net/). Le but de ces jeux est de 
voir s'affronter des programmes dans une compétition dans un univers aux règles connues de tous.

Dans notre cas l'univers choisi est celui des Pokémons. Les combattants sont des dresseurs qui ont pour objectif de 
faire s'affronter des Pokémons pour remporter la compétition. Au début du jeu les combattants pourront être humains 
mais au fur et à mesure de l'avancée du projet, il faudra les remplacer autant que possible par des intelligences
artificielles.

## Sujet

Le projet Pokebattle a pour but de créer un jeu Pokemon en ligne via
Twitter.

Les dresseurs ont pour objectif de faire s'affronter des Pokémons pour
remporter des compétitions.

Chaque dresseur et chaque Pokémon a son propre compte Twitter. Ils
communiquent en utilisant un protocole commun.

Dans un premier temps, les comptes Twitter des dresseurs seront gérés
par des humains, les comptes de Pokemon seront gérés par des bots
Twitter... que vous allez implémenter!

## Pré-requis

Vous devez créer un compte twitter pour chaque pokemon et chaque
éleveur.

La bio des pokemons doit commencer par:

```
#pokebattle - #pokemon
```

En se basant sur le travail réalisé lors du [TP-4](http://bit.ly/iut-4), @nedseb a 
commencé à implémenter le projet Pokebattle.

Rendez-vous sur https://github.com/IUTInfoAix/PokeBotDemo, forkez ce projet et commencez à travailler en équipe. La première étape pour le rendre fonctionnel,
est de compléter le fichier `src/main/resource/twitter4j.properties` avec les clefs de connexion que vous obtiendrez après avoir créé une application sur la page 
https://dev.twitter.com/apps. Pour configurer ces clefs il existe d'autres méthodes que vous pouvez découvrir sur la page suivante : twitter4j.org/en/configuration.html 

## Sujet détaillé

Après avoir pris connaissance de l'[Univers](https://github.com/IUTInfoAix/PokeBattle/blob/master/univers.md), 
vous pourrez développer les [Fonctionnalités](https://github.com/IUTInfoAix/PokeBattle/blob/master/fonctionalites.md)
définies en suivant la [Méthodologie](https://github.com/IUTInfoAix/PokeBattle/blob/master/methodologie.md) proposée.

Vous pouvez suivre l'avancement de votre projet sur le tableau de bord
[PokeStatus](http://bit.ly/pokestatus) et sur
[Sonar](http://sonar.zapto.org:9000/) (serveur interne à l'IUT).

En fin de projet, nous vous invitons à nous faire parvenir une [Retrospective](https://github.com/IUTInfoAix/PokeBattle/blob/master/retrospective.md).
