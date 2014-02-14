## Fonctionalités du juge de combat

### A1 - Un juge indique le nombre de points perdus à chaque attaque

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

### A2 - Vainqueur

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

### A3 - Le juge calcul l'expérience gagnée en fin de combat

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