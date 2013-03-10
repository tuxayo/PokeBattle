# Pokebattle!

## Sujet

Le projet Pokebattle a pour but de créer un jeu Pokemon en ligne via
Twitter.

Les dresseurs ont pour objectif de faire s'affronter des Pokémons pour
remporter des compétitions.

Chaque dresseurs et chaque Pokémon a son propre compte Twitter. Ils
communiquent en utilisant un protocole commun.

Dans un premier temps, les comptes Twitter des dresseurs seront gérés
par des humain, les comptes de Pokemon seront gérés par des bots
Twitter... que vous allez implémenter!

## Méthode Agile

### Formez des groupes

Nous vous invitons à former des groupes de 4 à 5 personnes. Vous
travaillerez ensemble pour la durée du projet.

### Stand-up!

Chaque début de séance, vous faites un "Stand-up". Vous vous mettez en
cercle, debout. À tour de rôle, chaque membre de l'équipe fait le point
sur:

* ce qu'il a fait lors de la dernière séance, 
* ce qu'il compte faire lors de cette séance,
* indique si quelque chose l'empêche d'avancer.

Le "Stand-up" ne doit pas durer plus de 5 minutes.

### TDD, Git et Pull-Requests

À chaque fonctionnalité, créez une branche spécifique commençant par le
numéro de la fonctionnalité. Exemple: `STORY-1-pokemon-repond-pikapika`

Nous vous invitons à développer en faisant du Développement guidé par
les tests (TDD in english): 

* 1 - Écrivez un test, regardez le échouer.
* 2 - Écrivez le code correspondant, regardez le test passer.
* 3 - Refactorez le code pour qu'il soit plus simple, plus expressif, plus
lisible.
* 4 - Committez ce nouveau test.
* 5 - Retour au 1.

**Note:** Afin de faciliter le suivi du projet, nous vous demandons
de commencer vos messages de commit par le numéro de la fonctionnalité
que vous implémentez. Exemple: `STORY-1 - Pokemon répond "Pika Pika"` ou
`STORY-1 - Correction des tests`

Une fois que la fonctionnalité est développée, créez une pull request!

Un autre étudiant de l'équipe devra vérifier la pull request:

* les tests passent?
* le code est compréhensible?
* chaque classe possède sa classe de tests?
* il y a suffisament de tests?
* la fonctionnalité implémenté correspond à la story?

Si tout est bon, mergez la Pull-Request dans master! Sinon, faites vos
commentaires via Github. Il suffit de continuer de travailler sur la
même branche et la pusher pour mettre à jour la pull request.

## Fonctionnalités

Voici les liste des fonctionnalité que nous souhaiterions voir
développées.

### F-1 - Pokemon répond (Déja implémenté)

Lorsque quelqu'un parle à un pokémon, celui-ci répond.

Exemple:

```
pcreux: "@pikachuNyanNyan Salut!"
pikachuNyanNyan: "Pika pika!"
```

### F-2 - Pokemon répond en mentionnant son interlocuteur

Lorsque quelqu'un parle à un pokémon, celui-ci répond le mentionnant.

Exemple:

```
pcreux: "@pikachuNyanNyan Salut!"
pikachuNyanNyan: "@pcreux Pika pika!"
```

### F-3 - Pokemon indique le nom de son éleveur

Exemple:

```
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux @nedseb is my owner"
```

ou

```
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux No owner"
```

### F-4 - Un Pokemon sans éleveur peut être attrapé

Exemple:

```
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux No owner"

pcreux: "@pikachuNyanNyan Pokeball!"
pikachuNyanNyan: "@pcreux @pcreux is my owner"
```

### F-5 - Un pokemon avec éleveur ne peut être attrapé

Exemple:

```
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux @nedseb is my owner"

pcreux: "@pikachuNyanNyan Pokeball!"
pikachuNyanNyan: "@pcreux @nedseb is my owner"
```

### F-6 - Un pokemon attaque lorsque son éleveur le lui demande

Exemple:

```
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux @pcreux is my owner"

pcreux: "@pikachuNyanNyan #attack #foudre @bulbizare1"
pikachuNyanNyan: "@bulbizare1 #attack #foudre! /cc @pcreux"
```

### F-7 - Un pokemon répond uniquement aux ordres de son éleveur

Exemple:

```
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux @nedseb is my owner"

pcreux: "@pikachuNyanNyan #attack #foudre @bulbizare1"
pikachuNyanNyan: "@pcreux @nedseb is my owner"
```

