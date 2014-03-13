## Fonctionalités du juge de combat

### A1 - Un juge de combat répond
Lorsque quelqu'un parle à un juge de combat, celui-ci répond en saluant. 

Exemple:

```yaml
pcreux: "@viviane Salut!"
viviane: "Salisalut très cher voisin !"
```

### A2 - Un juge de combat répond en mentionnant son interlocuteur
Lorsque quelqu'un parle à un juge, celui-ci répond le mentionnant.

Exemple:

```yaml
pcreux: "@viviane Salut!"
viviane: "@pcreux Salisalut très cher voisin !"
```

### A3 - Un juge de combat indique son arène
Exemple:

```yaml
pcreux: "@viviane Gym?"
viviane: "@pcreux my gym is @ViridianGym"
```

ou

```yaml
pcreux: "@viviane Gym?"
viviane: "@pcreux No gym"
```

### A4 - Un juge de combat peut être embauché
Exemple:

```yaml
ViridianGym: "@viviane Gym?"
viviane: "@ViridianGym No gym"

ViridianGym: "@viviane Hire!"
viviane: "@ViridianGym my gym is @ViridianGym"
```

### A5 - Un juge de combat embauché ne peut plus être embauché
Exemple:

```yaml
pcreux: "@viviane Gym?"
viviane: "@pcreux my gym is @ViridianGym"

pcreux: "@viviane Hire!"
viviane: "@pcreux @ViridianGym is my owner"
```

### A6 - Un juge indique le nombre de points perdus à chaque attaque

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

### A7 - Pénalités
Si un pokemon ne respecte pas les règles (déclaration d'un combat, suivi des round)
Alors il reçoit une pénalité (passe son prochain tour)

### A8 - Vainqueur

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

### A9 - Le juge calcul l'expérience gagnée en fin de combat

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

### A10 - Un juge de combat indique son arène dans sa bio twitter

### A11 - Un juge de combat valide le début du combat

En réponse à une demande de combat, le juge donne son accord
S'il est déjà en combat, il refuse

### A12 - Validité des attaques

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

### A13 - Validité des attaques
Si un pokemon accepte de lancer une attaque qu'il ne connait pas, il est sanctionné


### A14 - Un juge de combat donne ses caractéristiques quand on les lui demande
Nombre de combats déjà engagés dans la dernière heure

### A15 - Un juge de combat indique son gestionaire sa bio twitter

Afin de savoir qui est l'éleveur d'un pokemon
Le profile twitter du pokemon doit afficher le nom de son éleveur

Exemple:

```
#pokebattle - #pokemon - Owner: @nedseb - Level: 1
```

Pour implémenter cette fonctionalité, vous utiliserez la méthode 
[`updateProfile`](http://twitter4j.org/oldjavadocs/3.0.3/twitter4j/api/UsersResources.html#updateProfile%28java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String%29) de la classe `Twitter`.

### A16 - Limite de combat
Suite aux accords de branche du syndicat des juges de combat travailleurs, un juge ne peut pas arbitrer plus de 5 combats à l'heure


### A18 - Gestion des rounds de combat

Lors d'un combat, l'arbitre signale les rounds d'attaque.


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




