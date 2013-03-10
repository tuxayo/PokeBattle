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
numéro de la fonctionnalité. Exemple: `F-1-pokemon-repond-pikapika`

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
que vous implémentez. Exemple: `F-1 - Pokemon répond "Pika Pika"` ou
`F-1 - Correction des tests`

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
développées. Vous pouvez les développer dans n'importe quel ordre.
Vous n'avez pas à toutes les développer.

Vous devez créer un compte twitter pour chaque pokemon et chaque
éleveur.

La bio des pokemons doit commencer par:

```
#pokebattle - #pokemon
```

### F-1 - Pokemon répond (Déja implémenté)

Lorsque quelqu'un parle à un pokémon, celui-ci répond.

Exemple:

```yaml
pcreux: "@pikachuNyanNyan Salut!"
pikachuNyanNyan: "Pika pika!"
```

### F-2 - Pokemon répond en mentionnant son interlocuteur

Lorsque quelqu'un parle à un pokémon, celui-ci répond le mentionnant.

Exemple:

```yaml
pcreux: "@pikachuNyanNyan Salut!"
pikachuNyanNyan: "@pcreux Pika pika!"
```

### F-3 - Pokemon indique le nom de son éleveur

Exemple:

```yaml
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux @nedseb is my owner"
```

ou

```yaml
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux No owner"
```

### F-4 - Un Pokemon sans éleveur peut être attrapé

Exemple:

```yaml
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux No owner"

pcreux: "@pikachuNyanNyan Pokeball!"
pikachuNyanNyan: "@pcreux @pcreux is my owner"
```

### F-5 - Un pokemon avec éleveur ne peut être attrapé

Exemple:

```yaml
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux @nedseb is my owner"

pcreux: "@pikachuNyanNyan Pokeball!"
pikachuNyanNyan: "@pcreux @nedseb is my owner"
```

### F-6 - Un pokemon attaque lorsque son éleveur le lui demande

Exemple:

```yaml
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux @pcreux is my owner"

pcreux: "@pikachuNyanNyan #attack #foudre @bulbizare1"
pikachuNyanNyan: "@bulbizare1 #attack #foudre! /cc @pcreux"
```

Notez que le pokemon mentionne son éleveur

### F-7 - Un pokemon répond uniquement aux ordres de son éleveur

Exemple:

```yaml
pcreux: "@pikachuNyanNyan Owner?"
pikachuNyanNyan: "@pcreux @nedseb is my owner"

pcreux: "@pikachuNyanNyan #attack #foudre @bulbizare1"
pikachuNyanNyan: "@pcreux @nedseb is my owner"
```

### F-8 - Un pokemon indique le nom de son éleveur dans sa bio twitter

Afin de savoir qui est l'éleveur d'un pokemon
Le profile twitter du pokemon doit afficher le nom de son éleveur

Exemple:

```
#pokebattle - #pokemon - Owner: @nedseb
```

### F-9 - Un pokemon mentionne l'éleveur du pokemon qu'il attaque

* `@pcreux` élève `bulbizare1`.
* `@nedseb` élève `pikachuNyanNyan`.

Lors de l'attaque, l'éleveur doit mentionné le nom de l'éleveur du
pokemon qu'il attaque.

```yaml
pcreux: "@bulbizare1 #attack #foudre @pikachuNyanNyan /cc @nedseb"
pikachuNyanNyan: "@bulbizare1 #attack #foudre /cc @nedseb @pcreux"
```

### F-10 - Un juge indique le nombre de points perdus à chaque attack

* @viviane est juge

Lors d'un combat:

```yaml
pcreux: "@bulbizare1 #attack #foudre @pikachuNyanNyan /cc @nedseb @viviane"
bulbizare1: "@pikachuNyanNyan #attack #foudre /cc @nedseb @pcreux @viviane"

nedseb: "@pikachuNyanNyan #attack #baston @bulbizare1 /cc @nedseb @viviane"
pikachuNyanNyan: "@bulbizare1 #attack #foudre /cc @nedseb @pcreux @viviane"
```

Le juge indique le nombre de points perdus par chaque pokemon:

```yaml
viviane: "@bulbizare1 -15pv /cc @pcreux"
viviane: "@pikachuNyanNyan -10pv /cc @nedseb"
```

### F-11 - Un pokemon indique lorsqu'il est #KO

* @viviane est juge
* @bulbizare n'a plus que 10pv

Lors d'un combat:

```yaml
pcreux: "@bulbizare1 #attack #foudre @pikachuNyanNyan /cc @nedseb @viviane"
bulbizare1: "@pikachuNyanNyan #attack #foudre /cc @nedseb @pcreux @viviane"

nedseb: "@pikachuNyanNyan #attack #baston @bulbizare1 /cc @nedseb @viviane"
pikachuNyanNyan: "@bulbizare1 #attack #foudre /cc @nedseb @pcreux @viviane"

viviane: "@bulbizare1 -15pv /cc @pcreux"
viviane: "@pikachuNyanNyan -10pv /cc @nedseb"
```

`@bulbizare1` arrive à 0pv et dit:

```yaml
bulbizare1: "#KO /cc @viviane @nedseb @pikachuNyanNyan"
```

### F-12 - Combat

Un dresseur est à l'origine d'un combat. Il indique le pokemon avec
lequel il veut combattre et le nom du juge de combat.

L'autre dresseur répond avec quel pokemon il souhaite combattre.

```yaml
pcreux: "@nedseb #fight with @bulbizare1 /cc @viviane"
nedseb: "@pcreux #fight #ok with @pikachuNyanNyan. /cc @viviane"
```

### F-13 - Vainqueur

Lorsqu'un pokemon meurt:

```yaml
# suite d'attaques

viviane: "@bulbizare1 -15pv /cc @pcreux"
viviane: "@pikachuNyanNyan -10pv /cc @nedseb"

bulbizare1: "#KO /cc @viviane @nedseb @pikachuNyanNyan"
```

Le juge indique le pokemon vainqueur:

```yaml
viviane: "@pikachuNyanNyan #Win"
```

