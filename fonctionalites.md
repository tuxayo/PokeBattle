## Fonctionalités

### F-1 - Pokemon répond (Déjà implémenté par @nedseb)

Lorsque quelqu'un parle à un pokémon, celui-ci répond avec son cri. Si vous ne vous souvenez 
plus du cri exact de votre pokémon, vous pouvez essayer de le retrouver [ici](http://www.youtube.com/watch?v=YPvcwfbR7pY).

Exemple:

```yaml
pcreux: "@pikachuNyanNian Salut!"
pikachuNyanNian: "Pika pika!"
```

### F-2 - Pokemon répond en mentionnant son interlocuteur

Lorsque quelqu'un parle à un pokémon, celui-ci répond le mentionnant.

Exemple:

```yaml
pcreux: "@pikachuNyanNian Salut!"
pikachuNyanNian: "@pcreux Pika pika!"
```

### F-3 - Pokemon indique le nom de son éleveur

Exemple:

```yaml
pcreux: "@pikachuNyanNian Owner?"
pikachuNyanNian: "@pcreux @nedseb is my owner"
```

ou

```yaml
pcreux: "@pikachuNyanNian Owner?"
pikachuNyanNian: "@pcreux No owner"
```

### F-4 - Un Pokemon sans éleveur peut être attrapé

Exemple:

```yaml
pcreux: "@pikachuNyanNian Owner?"
pikachuNyanNian: "@pcreux No owner"

pcreux: "@pikachuNyanNyan Pokeball!"
pikachuNyanNian: "@pcreux @pcreux is my owner"
```

### F-5 - Un pokemon avec éleveur ne peut être attrapé

Exemple:

```yaml
pcreux: "@pikachuNyanNian Owner?"
pikachuNyanNian: "@pcreux @nedseb is my owner"

pcreux: "@pikachuNyanNian Pokeball!"
pikachuNyanNian: "@pcreux @nedseb is my owner"
```

### F-6 - Un pokemon attaque lorsque son éleveur le lui demande

Exemple:

```yaml
pcreux: "@pikachuNyanNian Owner?"
pikachuNyanNian: "@pcreux @pcreux is my owner"

pcreux: "@pikachuNyanNian #attack #foudre @bulbizare1"
pikachuNyanNian: "@bulbizare1 #attack #foudre! /cc @pcreux"
```

Notez que le pokemon mentionne son éleveur

### F-7 - Un pokemon répond uniquement aux ordres de son éleveur

Exemple:

```yaml
pcreux: "@pikachuNyanNian Owner?"
pikachuNyanNian: "@pcreux @nedseb is my owner"

pcreux: "@pikachuNyanNian #attack #foudre @bulbizare1"
pikachuNyanNian: "@pcreux @nedseb is my owner"
```

### F-8 - Un pokemon indique le nom de son éleveur dans sa bio twitter

Afin de savoir qui est l'éleveur d'un pokemon
Le profile twitter du pokemon doit afficher le nom de son éleveur

Exemple:

```
#pokebattle - #pokemon - Owner: @nedseb
```
Pour implémenter cette fonctionalité, vous utiliserez la méthode 
[`updateProfile`](http://twitter4j.org/oldjavadocs/3.0.3/twitter4j/api/UsersResources.html#updateProfile%28java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String%29) 
de la classe `Twitter`.

### F-9 - Un pokemon mentionne l'éleveur du pokemon qu'il attaque

* `@pcreux` élève `bulbizare1`.
* `@nedseb` élève `pikachuNyanNian`.

Lors de l'attaque, l'éleveur doit mentionné le nom de l'éleveur du
pokemon qu'il attaque.

```yaml
pcreux: "@bulbizare1 #attack #charge @pikachuNyanNian /cc @nedseb"
bulbizare1: "@pikachuNyanNian #attack #charge /cc @nedseb @pcreux"
```

### F-10 - Un juge indique le nombre de points perdus à chaque attaque

* @viviane est juge
* Pour le moment, toutes les attaques infligent les même dégats (-10pv), tous les pokémons ont le même nombre maximum de PV (100pv) et sont au niveau 1 

Lors d'un combat:

```yaml
pcreux: "@bulbizare1 #attack #charge @pikachuNyanNian /cc @nedseb @viviane"
bulbizare1: "@pikachuNyanNian #attack #charge /cc @nedseb @pcreux @viviane"

nedseb: "@pikachuNyanNian #attack #foudre @bulbizare1 /cc @pcreux @viviane"
pikachuNyanNian: "@bulbizare1 #attack #foudre /cc @nedseb @pcreux @viviane"
```

Le juge indique le nombre de points perdus par chaque pokemon:

```yaml
viviane: "@bulbizare1 -10pv /cc @pcreux"
viviane: "@pikachuNyanNian -10pv /cc @nedseb"
```

### F-11 - Un pokemon indique lorsqu'il est #KO

* @viviane est juge
* @bulbizare n'a plus que 10pv

Lors d'un combat:

```yaml
pcreux: "@bulbizare1 #attack #charge @pikachuNyanNian /cc @nedseb @viviane"
bulbizare1: "@pikachuNyanNian #attack #charge /cc @nedseb @pcreux @viviane"

nedseb: "@pikachuNyanNian #attack #foudre @bulbizare1 /cc @pcreux @viviane"
pikachuNyanNian: "@bulbizare1 #attack #foudre /cc @nedseb @pcreux @viviane"

viviane: "@bulbizare1 -10pv /cc @pcreux"
viviane: "@pikachuNyanNian -10pv /cc @nedseb"
```

`@bulbizare1` arrive à 0pv et dit:

```yaml
bulbizare1: "#KO /cc @viviane @nedseb @pcreux"
```

### F-12 - Combat

Un dresseur est à l'origine d'un combat. Il indique le pokemon avec
lequel il veut combattre et le nom du juge de combat.

L'autre dresseur répond avec quel pokemon il souhaite combattre.

```yaml
pcreux: "@nedseb #fight with @bulbizare1 /cc @viviane"
nedseb: "@pcreux #fight #ok with @pikachuNyanNian /cc @viviane"
```

### F-13 - Vainqueur

Lorsqu'un pokemon meurt:

```yaml
# suite d'attaques

viviane: "@bulbizare1 -10pv /cc @pcreux"
viviane: "@pikachuNyanNian -10pv /cc @nedseb"

bulbizare1: "#KO /cc @viviane @nedseb @pcreux"
```

Le juge indique le pokemon vainqueur:

```yaml
viviane: "@pikachuNyanNian #Win"
```

### F-14 - Validité des attaques

Un pokémon refuse d'attaquer s'il ne connait pas une attaque. 
Le joueur perd donc le droit d'attaquer pour le tour courant.

Lors d'un combat:

```yaml
pcreux: "@bulbizare1 #attack #charge @pikachuNyanNian /cc @nedseb @viviane"
bulbizare1: "@pikachuNyanNian #attack #charge /cc @nedseb @pcreux @viviane"

nedseb: "@pikachuNyanNian #attack #grumpycat @bulbizare1 /cc @pcreux @viviane"
pikachuNyanNian: "@nedseb  o_O ? /cc @pcreux @viviane @bulbizare1"

viviane: "@bulbizare1 -0pv /cc @pcreux"
viviane: "@pikachuNyanNian -10pv /cc @nedseb"
```
Pour connaitre les attaques dont il dispose, le pokémon peut utiliser le Pokedex mis à sa disposition (https://raw.github.com/IUTInfoAix/Pokedex/master/data/pokedex.json). 
Ce fichier évoluera au fur et à mesure de l'ajout des stories, il faudra donc sur son évolution.
Pour parser un fichier JSON vous pouvez vous inspirer des exemples suivants : https://gist.github.com/nedseb/29b8ca20dd0a5c14a9f3.

### F-15 - Un Pokémon donne ses caractéristiques quand on les lui demande

Un pokémon dispose d'un certain nombre de caractéristiques qui lui sont propres. 
Il doit les donner quand on les lui demande. 

Par exemple pour connaitre le niveau d'un pokémon :
```yaml
pcreux: "@bulbizare1 #stat #level ?"
bulbizare1: "@pcreux #level=1"
```

Pour l'expérience :
```yaml
pcreux: "@bulbizare1 #stat #XP ?"
bulbizare1: "@pcreux #XP=0"
```

Pour connaitre le nombre de PV (courant et max) :
```yaml
pcreux: "@bulbizare1 #stat #PV ?"
bulbizare1: "@pcreux #PV=10/100"
```
### F-16 - Un Pokémon donne ses caractéristiques d'attaque quand on les lui demande

Pour savoir combien de PP il lui reste pour une attaque donnée :
```yaml
pcreux: "@bulbizare1 #statAttack #PP #charge ?"
bulbizare1: "@pcreux #charge #PP=10/35"
```
### F-17 - Un Pokémon inactif retrouve progressivement ses PV

Un pokémon laissé inactif récupère ses PV au fil du temps. Au total il récupère 10% de ses 
PV toutes les heures.

Par exemple, à 8h30 :
```yaml
pcreux: "@bulbizare1 #stat #PV ?"
bulbizare1: "@pcreux #PV=10/100"
```

@bulbizare1 reste inactif

À 9h29 :
```yaml
pcreux: "@bulbizare1 #stat #PV ?"
bulbizare1: "@pcreux #PV=10/100"
```

À 9h30
```yaml
pcreux: "@bulbizare1 #stat #PV ?"
bulbizare1: "@pcreux #PV=20/100"
```

### F-18 - Un Pokémon peut aller au centre pokémon pour retrouver toutes ses capacités

 * @JoelleBourgPalet est la gérante du centre pokémon du Bourg Palette
 * @bulbizare1 n'a plus que 10PV

Quand un dresseur porte un de ses pokémons dans un centre pokémon, la durée des soins est proportionnelle 
au pourcentage de PV à restaurer. 

Si un pokémon est KO (restauration de 100% des PV), il lui faut attendre 10 minutes avant de retrouver 
l'usage de son pokémon. Si un pokémon n'a que 50% de ses PV à recupérer, il devra attendre 5 minutes.

```yaml
pcreux: "@bulbizare1 #stat #PV ?"
bulbizare1: "@pcreux #PV=20/100"
pcreux: "@JoelleBourgPalet #heal @bulbizare1"
JoelleBourgPalet: "@bulbizare1 #stat #PV ?"
bulbizare1: "@JoelleBourgPalet #PV=20/100"
JoelleBourgPalet: "@bulbizare1 come in the #pokecenter /cc @pcreux"
```
Après 8 minutes d'attente
```yaml
JoelleBourgPalet: "@pcreux @bulbizare1 is restored to full health"
pcreux: "@bulbizare1 #stat #PV ?"
bulbizare1: "@pcreux #PV=100/100"
```
Pour que le centre pokémon soit capable d'avertir quand il a fini, vous pouvez utiliser le service [@poketimer](https://twitter.com/PokeTimer).
Ce service est une sorte de réveil que vous programmez pour vous avertir quand le temps demandé est terminé. 
Pour programmer le @poketimer, il suffit d'envoyer un tweet avec le hashtag #WakeMeUp et la durée souhaitée en minute. 
Pour reconnaitre les différents réveils que l'on a programmé, on peut personnaliser le message reçu. Pour ce faire, 
le reste du message après la durée sera recopié dans le message envoyé par le @poketimer. 
```yaml
JoelleBourgPalet: "@PokeTimer #WakeMeUp 1 Min #PokePoke"
```
Après une minute d'attente
```yaml
PokeTimer: "@JoelleBourgPalet #DringDring #PokePoke"
```

### F-19 - Un pokemon indique son niveau dans sa bio twitter

Afin de savoir qui est l'éleveur d'un pokemon
Le profile twitter du pokemon doit afficher le nom de son éleveur

Exemple:

```
#pokebattle - #pokemon - Owner: @nedseb - Level: 1
```

Pour implémenter cette fonctionalité, vous utiliserez la méthode 
[`updateProfile`](http://twitter4j.org/oldjavadocs/3.0.3/twitter4j/api/UsersResources.html#updateProfile%28java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String%29) 
de la classe `Twitter`.

### F-20 - Le juge calcul l'expérience gagnée en fin de combat

* dans l'exemple @bulbizare1 est au niveau 1.
* Il a une expérience de base de 64.
* Il ne lui reste que 10pv.

Après le combat, le juge va calculer l'expérience gagné par le vainqueur. 

Pour calculer cette expérience, il utilise la formule suivante :
```
Exp = expval* Level/7
```
`expval` est l'expérience de base propre à l'espèce du Pokémon vaincu.

```yaml
# suite d'attaques

viviane: "@bulbizare1 -10pv /cc @pcreux"
viviane: "@pikachuNyanNian -10pv /cc @nedseb"

bulbizare1: "#KO /cc @viviane @nedseb @pcreux"

viviane: "@pikachuNyanNian #Win +9xp"
```
### F-21 - Gestion des rounds de combat

Lors d'un combat:

```yaml
pcreux: "@nedseb #fight with @bulbizare1 /cc @viviane"
nedseb: "@pcreux #fight #ok with @pikachuNyanNian /cc @viviane"

viviane: "Round #1 /cc @nedseb @pikachuNyanNian @pcreux @bulbizare1"

pcreux: "@bulbizare1 #attack #charge @pikachuNyanNian /cc @nedseb @viviane #1"
bulbizare1: "@pikachuNyanNian #attack #charge /cc @nedseb @pcreux @viviane #1"

nedseb: "@pikachuNyanNian #attack #foudre @bulbizare1 /cc @pcreux @viviane #1"
pikachuNyanNian: "@bulbizare1 #attack #foudre /cc @nedseb @pcreux @viviane #1"

viviane: "@bulbizare1 -10pv /cc @pcreux #1"
viviane: "@pikachuNyanNian -10pv /cc @nedseb #1"

viviane: "Round #2 /cc @nedseb @pikachuNyanNian @pcreux @bulbizare1"

```
### F-22 - Ajout du hashtag #PokeBattle

Rajouter, quand c'est possible, le hashtag #PokeBattle à la fin de tous les tweets émis par vos bot. 

### F-23 - Déployer les bots sur Heroku
En vous aidant de ce tutoriel (https://github.com/nedseb/TutoHeroku), déployez vos bots sur la 
plate-forme de cloud computing Heroku (http://www.heroku.com/). Soyez très vigilent avec la gestion 
de vos clefs ssh quand vous changez de machine.

### F-24 - Contrôle de la qualité de votre code
Pour vous aider à vérifier les indicateurs de qualité de votre code, nous avons installé 
une instance sonar sur l'un des serveurs de l'iut. Pour accèder aux métriques de votre projet 
allez sur la page http://sonar.zapto.org:9000/ et regardez tous les indicateurs disponibles. Le 
nom de votre projet doit commencer par votre login github. Pour importer les projets, nous nous sommes
basé sur la liste des forks donné par github. Si vous avez rendu votre dépot privé il est possible que 
vous n'apparaissiez pas.

Pour cette fonctionnalité, vous devez diminuer autant que possible les violations indiquées par sonar
et augmenter la couverture du code testé.

### Retrospective

En fin de semaine, merci de nous faire parvenir votre [retrospective](https://github.com/IUTInfoAix/PokeBattle/blob/master/retrospective.md).




