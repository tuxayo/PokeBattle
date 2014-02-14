## Fonctionalités du juge de combat

### A1 - Un juge de combat répond

### A2 - Un juge de combat répond en mentionnant son interlocuteur

### A3 - Un juge de combat indique son arène

### A4 - Un juge de combat peut être embauché

### A5 - Un juge de combat embauché ne peut plus être embauché

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
### A12 - Un juge de combat indique son gestionaire sa bio twitter

Afin de savoir qui est l'éleveur d'un pokemon
Le profile twitter du pokemon doit afficher le nom de son éleveur

Exemple:

```
#pokebattle - #pokemon - Owner: @nedseb - Level: 1
```

Pour implémenter cette fonctionalité, vous utiliserez la méthode 
[`updateProfile`](http://twitter4j.org/oldjavadocs/3.0.3/twitter4j/api/UsersResources.html#updateProfile%28java.lang.String,%20java.lang.String,%20java.lang.String,%20java.lang.String%29) de la classe `Twitter`.

### A13 - Limite de combat
Suite aux accords de branche du syndicat des juges de combat travailleurs, un juge ne peut pas arbitrer plus de 5 combats à l'heure

### A14 - Un juge de combat donne ses caractéristiques quand on les lui demande
Nombre de combats déjà engagés dans la dernière heure

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



