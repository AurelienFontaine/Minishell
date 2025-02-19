# Minishell - Un Petit Shell en C

## Description
Ce projet implémente un shell minimaliste nommé `Minishell`. Il vise à reproduire certaines fonctionnalités de Bash tout en respectant des contraintes spécifiques.

## Fonctionnalités Implémentées

### Affichage et Entrée
- Affiche un prompt en attente d'une nouvelle commande.
- Gère un historique des commandes exécutées.
- Recherche et exécute le bon fichier binaire en fonction de la variable `PATH` ou en utilisant un chemin absolu ou relatif.

### Gestion des Signaux
- Utilisation d'une seule variable globale pour indiquer qu'un signal a été reçu.
- Cette variable ne doit fournir aucune autre information que le numéro du signal reçu.
- Les structures "norm" dans l'espace global sont interdites.

### Interprétation des Commandes
- Ne pas interpréter les guillemets non fermés ou les caractères spéciaux non requis tels que `\` ou `;`.
- Gestion des quotes :
  - `'` (guillemet simple) empêche l'interprétation des métacaractères.
  - `"` (guillemet double) empêche l'interprétation des métacaractères sauf `$` (dollar).

### Redirections
- `<` : Redirige l'entrée standard.
- `>` : Redirige la sortie standard.
- `<<` : Utilise un délimiteur pour lire l'entrée jusqu'à ce qu'une ligne contenant ce délimiteur soit rencontrée (sans mise à jour de l'historique).
- `>>` : Redirige la sortie standard en mode ajout (`append`).

### Pipelines
- Gestion du caractère `|` : la sortie d'une commande est connectée à l'entrée de la suivante via un pipe.

### Variables d'Environnement
- Gestion des variables d'environnement : `$nom_variable` est remplacé par sa valeur.
- Gestion de `$?` : retourne le statut de sortie de la dernière commande exécutée en premier plan.

### Gestion des Signaux en Mode Interactif
- `ctrl-C` : Affiche un nouveau prompt sur une nouvelle ligne.
- `ctrl-D` : Quitte le shell.
- `ctrl-\` : Ne fait rien.

### Commandes Builtins
Minishell implémente les commandes internes suivantes :
- `echo` avec l'option `-n`.
- `cd` avec un chemin absolu ou relatif.
- `pwd` sans option.
- `export` sans option.
- `unset` sans option.
- `env` sans option ou argument.
- `exit` sans option.

## Compilation et Exécution
### Compilation
Utilisation d'un Makefile avec `gcc`, pour compiler le programme :
```sh
make
```

### Exécution
Lancez le minishell avec :
```sh
./minishell
```

## Exemples d'Utilisation
### Exemple 1 : Exécution d'une commande
```sh
$ echo "Hello, world!"
Hello, world!
```

### Exemple 2 : Utilisation d'un pipe
```sh
$ ls | grep .c
main.c
.
.
.
utils.c
```

### Exemple 3 : Redirection de sortie
```sh
$ echo "Hello" > output.txt
```

### Exemple 4 : Gestion des variables d'environnement
```sh
$ export VAR=42
$ echo $VAR
42
```

## Auteur
Projet développé par **[Aurelien Fontaine] et [Benjamin Salor](https://github.com/Kwro91)**.

Le Repo original est sur le Github de Benjamin avec tout les push, celui ci est celui une fois le projet rendu et valide.


