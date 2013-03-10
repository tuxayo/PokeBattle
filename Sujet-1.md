# Pokebattle!

## Univers

Le projet Pokémon battle est une adaptation des jeux de programmation comme 
[Core War](http://fr.wikipedia.org/wiki/Core_War) ou [Robocode](http://robowiki.net/). Le but de ces jeux est de 
voir s'affronter des programmes dans une compétition dans un univers aux règles connues de tous.

Dans notre cas l'univers choisi est celui des Pokémons. Les combattants sont des dresseurs qui ont pour objectif de 
faire s'affronter des Pokémons pour remporter la compétition. Au début du jeu les combattants pourront être humains 
mais au fur et à mesure de l'avancée du projet, il faudra les remplacer autant que possible par des intelligences
artificielles.

Il existe plusieurs solutions pour gérer l'univers de notre jeu, partant des plus centralisées avec un serveur
omniscient qui a la responsabilité d'animer les acteurs jusqu'aux plus décentralisées où chaque acteur est un 
programme totalement autonome interagissant directement avec les autres programmes. La solution que nous avons retenue, 
est entre les deux. En effet, en plus des dresseurs et des Pokémons, il existe plusieurs autres types d'acteurs que 
nous appellerons les *médiateurs*. Le but de ces acteurs particuliers est de garantir le bon fonctionnement du jeu. Un 
peu comme les gendarmes et les voleurs, vous devrez améliorer les médiateurs au fur et à mesure que les dresseurs se perfectionneront .

En plus des acteurs il existe un certain nombre de services publics qui permettent de gérer certaines règles de l'univers. Par exemple, la gestion de tous les échanges financiers sera confiée à la *Pokémon National Bank*(PNB).

* Rôles :
   - Pokémon
   - Dresseurs
   - Arbitre de combat
   - Gérant d'une Arène
   - Organisateur de championnats
   - Espion

* Services :
   - Tableau des scores et classements
   - Annuaire des dresseurs
   - Pokedexia Universalis
   - Tribunal Révolutionaire Pokémon
   - Pokémon National Bank

### Description des rôles :

1. Pokémon :  
   ![Pikachu](http://img4.xooimage.com/files/f/6/1/pikachu-110ec1.jpg) Les Pokémons sont des créatures belliqueuses par nature, leur préoccupation principale est de se battre. Pour cela chaque espèce apprend des attaques. La liste des attaques que peut apprendre un Pokémon dépend uniquement de son espèce. Pour chacune d’elles, on souhaite connaître sa description textuelle, sa puissance et la probabilité d’atteindre sa cible. Comme les espèces de Pokémons, les attaques aussi possède un “type”. Une attaque n’a qu’un et un seul type. Un Pokémon d’un type donné ne peut apprendre que des attaques de son type. Au fil des combats, il gagne des points d'expérience qui lui permette de faire évoluer ses caractéristiques. Son parcours initiatique est jalonné en niveau. Le Pokémon peut évoluer. Chaque espèce de Pokémon à des caractéristiques qui lui sont propres. À la naissance, deux Pokémons de la même espèces sont légèrement différents. Ses différences s'expliquent par le caractère propre à chaque individu.
   

2. Dresseurs :  
   ![Sacha](https://twimg0-a.akamaihd.net/profile_images/2711619684/e05382a4d026c7654d7a0cbf21fe64b7.jpeg) Le dresseur est le propriétaire d'un Pokémon. Son but est d'entraîner au mieux ses Pokémons au combat pour obtenir l'équipe capable de remporter tous les championnats. Dans son équipe il ne peut pas avoir plus de 3 Pokémons. Pour obtenir de nouveaux Pokémon il y a 4 possibilités : Les attraper, les gagner au combat, les échanger ou les vendre.

3. Arbitre de combat :  
   L'arbitre de combat est la personne qui a la responsabilité de veiller au respect des règles de combat. C'est lui qui déclare le gagnant et le perdant de chaque combat. Il doit aussi transmettre les fiches de combat au gérant de l'arène qui s'occupera d'établir les classements. Si un dresseur contrevient au règlement, son Pokémon engagé au combat ira au dresseur adverse.

4. Gérant d'une arène :  
   C'est la mémoire d'une arène, les arbitres s'adressent à lui pour organiser les combats. Il s'occupe de la gestion des points ainsi que des classements. Il vérifie la cohérence des informations qui lui sont transmises et établit les différents classements.
   
5. Organisateur de championnats :  
   Régulièrement les arènes organisent des championnats pour déterminer qui est le meilleur dresseur. L'organisateur a 
   la charge de gérer les inscriptions, de planifier les combats, choisir les arbitres et de déclarer le vainqueur de la 
   compétition.

6. Espion :  
   L'espion se fait passer pour un dresseur pour identifier les tricheurs. À chaque tricheur détecté il gagne des points qui lui permettent d'améliorer son classement dans la ligue des espions. Quand il pense avoir détecté une fraude, il la déclare au *Tribunal Révolutionaire Pokémon* qui déterminera grâce aux éléments fournis si la fraude est avérée. Toute fraude détectée rapporte aussi de l'argent.

### Description des services :

1. Tableau des scores et classements :  
   TODO!

   
2. Annuaire des dresseurs :  
   TODO!
   
3. Pokedexia Universalis :  
   Le pokédex (ou Pokedexia Universalis) est l'encyclopédie des Pokémons, il connaît tout sur toute les espèces. L’un des premiers objectifs du Pokédex est de répertorier toutes les espèces de Pokémons existantes. Pour chacun d’eux le dresseur souhaite connaître toutes les caractéristiques. Une espèce de Pokémon possède un nom qui est unique, une taille, un poids et une couleur. Par exemple l’espèce nommée “Bulbizarre” mesure 0,7m, pèse 6,9kg et est de couleur verte. Pour chaque espèce, on souhaite aussi connaître en quelle espèce elle peut évoluer. Certaines espèces sont au sommet de l’arbre de l’évolution et n’ont donc pas d’évolution possible. 

   Le pokédex est capable de répondre à toutes les questions sur les espèces de Pokémons. Jamais il ne se trompe. Il peut être utilisé pour établir la fraude d'un dresseur. Quand un Pokémon vient au monde, il peut apprendre ses caractéristiques de base en interrogeant le pokédex.

4. Tribunal Révolutionaire Pokémon :  
   C'est le gardien de la loi, c'est lui qui punit le tricheur et qui récompense les espions.

5. Pokémon National Bank :  
   Le monde des Pokémons étant encore soumis à une dictature communiste, il n'y a qu'une seule banque d'état. C'est elle qui effectue la gestion des comptes de chaque dresseur et les flux financiers associés.

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

## Pré-requis

Vous devez créer un compte twitter pour chaque pokemon et chaque
éleveur.

La bio des pokemons doit commencer par:

```
#pokebattle - #pokemon
```

En se basant sur le travail réalisé lors du dernier TP, @nedseb a 
commencé à implémenter le projet Pokebattle.

Rendez-vous sur https://github.com/IUTInfoAix/XXXXX, forkez ce projet et
commencez à travailler en équipe.

## Fonctionnalités

Voici les liste des fonctionnalité que nous souhaiterions voir
développées.

### F-1 - Pokemon répond (Déjà implémenté par @nedseb)

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

### F-10 - Un juge indique le nombre de points perdus à chaque attaque

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

