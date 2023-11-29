# Node.JS CHEATSHEET

## Qu'est ce que c'est ?

Node.js est un environnement d’exécution single-thread, open-source et multi-plateforme permettant de créer des applications rapides et évolutives côté serveur et en réseau. Il fonctionne avec le moteur d’exécution JavaScript V8 et utilise une architecture d’E / S non bloquante et pilotée par les événements, ce qui le rend efficace et adapté aux applications en temps réel.


## Le developpement synchrone et asynchrone

Par défaut, toute fonction définie en JavaScript est synchrone. Cela veut dire que, lorsqu’elle est appelée:

cette fonction exécute immédiatement l’intégralité de ses instructions puis retourne une valeur dans la foulée;
et que le reste du programme attend la fin de l’exécution de cette fonction avant de s’exécuter à son tour.
Ainsi, quand on appelle plusieurs fonctions synchrones d’affilée, on a la garantie qu’elles s’exécutent de manière séquentielle. L’une après l’autre.

Les fonctions synchrones sont appropriées pour effectuer des opérations courtes, rapides, tant qu’il n’est pas problématique de monopoliser le fil d’exécution du programme Node.js.

Quand on développe un programme effectuant des opérations d’entrées / sorties de données – que ce soit sur le système de fichier, sur un réseau, ou sur n’importe quel matériel périphérique – il vaut mieux lancer ces opérations en tâche de fond, tout en continuant l’exécution du reste du programme.

Par exemple: un serveur doit être prêt à répondre à des requêtes à tout instant, même si une autre requête est déjà en cours de traitement.

Pour permettre l’exécution de plusieurs opérations en parallèle – sans bloquer l’exécution du reste du programme – le langage JavaScript fournit plusieurs manières de définir et d’appeler des fonctions Asynchrones.

Le principe de fonction de callback est la manière la plus classique de procéder:

on appelle une fonction asynchrone (A) en lui passant une autre fonction (B) – appelée fonction de callback – en paramètres;
la fonction asynchrone (A) rend immédiatement la main au programme;
la fonction de callback (B) sera appelée une fois que l’opération aura terminé son exécution.
Ainsi, quand on appelle plusieurs fonctions asynchrones d’affilée, leurs fonctions de callback respectives ne seront pas forcément exécutées dans le même ordre !


## Le REPL

Node.js est livré avec une Boucle de Lecture-Évaluation-Impression (Read-Eval-Print Loop), également connue sous le nom de REPL. C'est l'invité de commande interactif de Node.js ; tout JavaScript valide qui peut être écrit dans un script peut être passé au REPL. Il peut être utile pour expérimenter avec Node.js, déboguer du code et comprendre certains des comportements les plus excentriques de JavaScript.

Node.js dispose d'un REPL autonome accessible depuis la ligne de commande, et d'un module REPL intégré que vous pouvez utiliser pour créer vos propres REPL personnalisés. Nous allons apprendre les bases du REPL autonome.

Commandes spéciales et sortie du REPL
Les commandes spéciales suivantes sont prises en charge par toutes les instances REPL (d'après la documentation REPL de Node.js (EN)) :

- .exit : ferme le flux d'entrée/sortie ou E/S (I/O), ce qui entraîne la sortie du REPL.
- .break : lors de la saisie d'une expression multilignes, l'entrée de la commande .break (ou l'appui sur la combinaison de touches <ctrl>-C) interrompt la saisie ou le traitement de cette expression.
- .clear : réinitialise le contexte REPL à un objet vide et efface toute expression multiligne en cours de saisie.
- .help : affiche cette liste de commandes spéciales.
- .save : enregistre la session REPL actuelle dans un fichier : > .save ./file/to/save.js.
- .load : charge un fichier dans la session REPL actuelle : > .load ./file/to/load.js.
- .editor : accéder au mode éditeur (<ctrl>-D pour terminer, <ctrl>-C pour annuler).

## Le NPM

Avec npm (Node package manager), les développeurs JavaScript peuvent découvrir et installer des paquets (packages) de code Node.js dans leurs applications réseau ou leurs projets backend (côté serveur).

Un paquet node.js est un répertoire contenant un ou plusieurs modules ou bibliothèques JavaScript utilisés pour ajouter diverses fonctionnalités aux applications ou aux scripts. Sans paquets, un développeur  doit écrire un nouveau code pour chaque fonctionnalité dont son projet a besoin.


### Les package managers:

#### NPM, Yarn et PNPM

npm est le gestionnaire de paquets historique (depuis 2010), fourni "par défaut" avec Node. C'est le plus connu, et souvent celui avec lequel on trouve le plus d'exemples dans les documentations et tutoriels. Il fonctionne en ligne de commande et télécharge les dépendances d'un projet depuis un registre consultable également depuis le site web www.npmjs.com

yarn, développé initialement par Facebook (Meta) en 2016, est un gestionnaire alternatif, conçu dans l'idée d'être plus rapide : il utilise un cache local pour stocker les paquets déjà téléchargés, ce qui permet d'éviter des téléchargements supplémentaires. Il évite également les problèmes de dépendances en garantissant que les paquets sont installés dans un ordre déterminé, ce qui évite les erreurs d'installation en cas de dépendances croisées.

pnpm dont le nom provient de performant npm est encore un autre gestionnaire de paquets pour Node.js qui se concentre, entre autres, sur la performance et l'efficacité en utilisant un système de stockage partagé pour les paquets : une seule copie d'un paquet peut être partagée entre plusieurs projets, réduisant ainsi l'utilisation de l'espace disque.


#### Les commandes de base

Ces commandes de base devraient vous aider à démarrer avec PNPM dans vos projets JavaScript. N'oubliez pas de consulter la documentation officielle de PNPM pour des informations plus détaillées : Documentation PNPM.



Installation de PNPM :

```bash
npm install -g pnpm
```


Pour initialiser un projet PNPM, vous pouvez utiliser la commande suivante dans le répertoire de votre projet :


```bash
pnpm init
```
Cette commande vous posera quelques questions pour configurer votre projet et créer un fichier package.json.



Pour installer les dépendances définies dans votre fichier package.json, utilisez la commande :

```bash
pnpm install
```
Vous pouvez également installer une dépendance spécifique, par exemple :

```bash
pnpm install nom-du-paquet
```

Pour ajouter une dépendance à votre projet, utilisez la commande :

```bash
pnpm add nom-du-paquet
```
Vous pouvez également ajouter une dépendance en mode développement avec l'option -D :

```bash
pnpm add nom-du-paquet -D
```

Pour désinstaller une dépendance, utilisez la commande :

```bash
pnpm remove nom-du-paquet
```
Exécuter des scripts définis dans le fichier package.json :

```bash
pnpm run nom-du-script
```

Pour vérifier les mises à jour des dépendances, vous pouvez utiliser la commande :

```bash
pnpm outdated
```

Pour mettre à jour les dépendances à leurs versions les plus récentes compatibles, utilisez la commande :

```bash
pnpm update
```

Pour afficher la liste des dépendances installées, vous pouvez 

```bash
pnpm list
```

#### Qu'est ce qu'un paquet?

Un paquet PNPM (prononcé "pineapple") sur Node.js fait référence à un module ou une bibliothèque JavaScript spécifique, empaqueté et distribué via le gestionnaire de paquets PNPM. PNPM est un gestionnaire de paquets alternatif à npm (Node Package Manager) qui offre des fonctionnalités intéressantes telles que la gestion de l'espace disque, le partage de modules entre projets, et la parallélisation des opérations d'installation.


#### Le Semantic Versionning (SemVer)

Semantic Versioning, souvent abrégé en SemVer, est une convention de numérotation de versions utilisée dans l'écosystème Node.js (et au-delà) pour décrire les changements dans un logiciel de manière standardisée et compréhensible. La spécification complète de Semantic Versioning peut être trouvée sur le site Web officiel : Semantic Versioning 2.0.0.

La version d'un logiciel sous Semantic Versioning est composée de trois segments principaux : MAJOR.MINOR.PATCH. Chaque segment a une signification spécifique :

- MAJOR (majeur) : Incrémente lorsque des modifications incompatibles avec les versions antérieures sont apportées (par exemple, des modifications qui rendent le code existant incompatible avec la nouvelle version).

- MINOR (mineur) : Incrémente lorsque des fonctionnalités sont ajoutées de manière rétrocompatible.

- PATCH (correctif) : Incrémente pour les corrections de bogues rétrocompatibles.

En plus de ces trois segments, Semantic Versioning permet l'utilisation de balises préliminaires (pre-release) et de balises de métadonnées (build metadata). 

#### Package.json

Le fichier package.json est un fichier de configuration essentiel dans les projets Node.js. Il est utilisé pour décrire les détails du projet, y compris ses dépendances, les scripts de démarrage, les métadonnées, et d'autres informations utiles. 

Lorsqu'un projet Node.js est partagé avec d'autres développeurs, ils peuvent exécuter npm install dans le répertoire du projet

Voici quelques-unes des propriétés couramment utilisées dans un fichier package.json :

- name : Le nom du projet.

- version : La version actuelle du projet, généralement en suivant les principes de Semantic Versioning (MAJOR.MINOR.PATCH).

- description : Une brève description du projet.

- main : Le fichier principal qui sera exécuté lorsque quelqu'un requiert le module.

- scripts : Des scripts qui peuvent être exécutés à l'aide de la commande npm run. Par exemple, npm start pourrait être défini pour démarrer votre application.

- dependencies : Les dépendances nécessaires pour exécuter le projet en production.

- devDependencies : Les dépendances nécessaires uniquement pour le développement et les tests.

- author : Le nom de l'auteur du projet.

- license : La licence sous laquelle le projet est distribué.

- repository : L'URL du référentiel Git où le code source du projet est hébergé.

- keywords : Un tableau de mots-clés qui décrivent le projet.

exemple

``` bash
{
  "name": "mon-projet",
  "version": "1.0.0",
  "description": "Un projet Node.js étonnant",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "express": "^4.17.1",
    "lodash": "^4.17.21"
  },
  "devDependencies": {
    "nodemon": "^2.0.12"
  },
  "author": "Votre Nom",
  "license": "MIT",
  "repository": {
    "type": "git",
    "url": "https://github.com/votre-nom/mon-projet.git"
  },
  "keywords": ["Node.js", "projet", "exemple"]
}
```

#### "4.0.0" , "^4.0.0" et "~4.0.0"

- "4.0.0" :
Cela spécifie une version exacte. Le projet utilisera uniquement la version 4.0.0 du paquet. Aucune mise à jour automatique ne sera effectuée, même si des versions ultérieures compatibles sont publiées.
- "^4.0.0" (Caret Range) :
Le symbole caret (^) permet les mises à jour compatibles avec la version spécifiée, mais bloque les mises à jour majeures qui ne sont pas rétrocompatibles avec la version spécifiée. 
- "~4.0.0" (Tilde Range) :
Le symbole tilde (~) permet les mises à jour de correctifs, mais bloque les mises à jour mineures et majeures. 

#### npm et npx

npm est le gestionnaire de paquets intégré à un serveur Node.js. npm est donc utilisé pour installer et mettre à jour les paquets déjà installés dans votre projet. npm a la capacité d'exécuter des packages. Si vous utilisez la commande "npm mon-paquet", cela n'exécutera le paquet que s'il a été installé globalement. 


npx est l'acronyme de Node Package eXecute. C'est un outil spécialement conçu pour l'exécution des paquets. Lorsque vous lancez l'exécution d'un paquet avec cet outil, npx va chercher dans la variable "PATH" de l'ordinateur puis dans les fichiers binaires des modules du projet pour lancer la commande. S'il ne l'a pas trouvé, l'outil est même capable d'aller sur internet chercher la commande et de l'exécuter ensuite.

#### Cheat Sheet pour package manager

NPM (Node Package Manager) Cheat Sheet:

```bash
npm install package-name #Install a package locally

npm install -g package-name #Install a package globally

npm install --save-dev package-name #Install a package as a development dependency

npm install package-name@version #Install a specific package version

npm show package-name #Show information about a package:

npm ls #List locally installed packages

npm ls -g --depth=0 #List globally installed packages

npm update #Update all local packages:

npm update package-name  #Update a specific local package:

npm uninstall package-name #Uninstall a package:

npm run script-name # Run a script defined in package.json:

npm search keyword #Search for packages:
```


##### PNPM Cheat Sheet:

```bash
pnpm install package-name #Install a package locally

pnpm install --save-dev package-name #Install a package as a development dependency

pnpm install package-name@version #Install a specific package version

pnpm show package-name #Show information about a package

pnpm ls #List locally installed packages

pnpm ls -g --depth=0 #List globally installed packages

pnpm update #Update all local packages

pnpm update package-name #Update a specific local package

pnpm remove package-name #Uninstall a package

pnpm run script-name #Run a script defined in package.json

pnpm search keyword #Search for packages
```
These commands should help you get started with package management in Node.js using npm and pnpm. Don't forget to check the official documentation for more detailed information on each command.

## Code Tooling

### Linters et Formaters


Les linters et formatters sont des outils de "code tooling" (outils pour le développement de logiciels) qui aident les développeurs à écrire un code source plus lisible, maintenable et sans erreurs. Bien qu'ils aient des rôles similaires dans l'amélioration de la qualité du code, ils sont utilisés à des fins légèrement différentes.

 Les linters (vérificateurs de code) analysent le code source à la recherche de pratiques ou de motifs qui pourraient conduire à des erreurs, à des bugs ou qui ne respectent pas les conventions de codage définies.

 Ils peuvent détecter des problèmes tels que des variables non déclarées, des fonctions non utilisées, des erreurs de style de codage, etc.

par exemple ESLint est un linter populaire pour JavaScript.



 Les formatters sont des outils qui restructurent automatiquement le code pour qu'il respecte un style de formatage spécifique.
 Ils modifient la disposition du code en ajustant l'indentation, la position des parenthèses, etc., conformément aux règles de formatage prédéfinies.
Par exemple, Prettier est un formatter utilisé dans plusieurs langages, y compris JavaScript et TypeScript.



L'utilisation conjointe de linters et de formatters permet d'améliorer la cohérence du code, d'éviter les erreurs courantes, et de maintenir une base de code propre et facile à lire.
Intégration dans les workflows : Ils sont souvent intégrés dans les pipelines de construction (build) ou de CI/CD (Continuous Integration/Continuous Deployment) pour garantir la qualité du code avant le déploiement.

Un linter pourrait signaler une variable non utilisée, tandis qu'un formatter pourrait réorganiser le code pour maintenir la cohérence de la mise en forme, même après la suppression de cette variable.
En résumé, les linters et les formatters sont des outils essentiels dans le processus de développement de logiciels modernes, contribuant à la qualité du code, à la cohérence et à la productivité des équipes de développement.