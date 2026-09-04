# 2.3 Dépôts locaux et distants

## `git init` contre `git clone`

Démarrez un tout nouveau projet en local avec [`git init`](https://git-scm.com/docs/git-init) :

```bash
git init
```

Cela crée un sous-répertoire `.git` dans le dossier courant et le transforme en dépôt Git sans commit et sans dépôt distant configuré. Copiez un projet existant — historique compris — avec [`git clone`](https://git-scm.com/docs/git-clone) :

```bash
git clone <repository-url>
```

`git clone` crée un nouveau répertoire, copie tout l'historique, extrait la branche par défaut et configure automatiquement un dépôt distant nommé `origin` pointant vers la source. Utilisez `git init` quand un projet n'existe pas encore en tant que dépôt Git ; utilisez `git clone` quand il existe déjà, que ce soit sur une plateforme d'hébergement ou sur un chemin local.

## Ce que contient réellement `.git/`

Les deux commandes vous laissent avec un répertoire `.git/` qui contient les données réelles du dépôt — les fichiers de travail que vous voyez ne sont qu'un instantané extrait à partir de lui. Il comprend :

- `objects/` — le stockage adressé par contenu des commits, arbres (trees) et blobs (l'historique lui-même).
- `refs/heads/` et `refs/tags/` — les pointeurs vers les pointes de branches et les tags.
- `HEAD` — la branche (ou le commit) actuellement extraite.
- `config` — la configuration locale du dépôt (portée `--local`, voir [2.2](02-configure.md)).
- Après un clone, `refs/remotes/origin/` ainsi que `remote.origin.url` et `remote.origin.fetch` dans `config`, qui enregistrent d'où le dépôt a été cloné.

Supprimer `.git/` supprime tout l'historique du dépôt ; les fichiers de travail restants ne sont plus suivis par Git.

## URL de dépôt distant : HTTPS ou SSH

Une URL de dépôt distant prend l'une de ces deux formes courantes :

```bash
# HTTPS
https://github.com/OWNER/REPOSITORY.git

# SSH
git@github.com:OWNER/REPOSITORY.git
```

HTTPS fonctionne depuis n'importe quel réseau sans configuration locale supplémentaire et s'authentifie avec un jeton d'accès personnel plutôt qu'avec le mot de passe de votre compte ; c'est le point de départ le plus simple. SSH s'authentifie avec une paire de clés enregistrée sur la plateforme et est plus pratique pour des push fréquents une fois configuré, car il ne demande pas de jeton à chaque fois. Les deux formes fonctionnent aussi bien avec `git clone` qu'avec `git remote add`. La configuration spécifique à chaque plateforme pour les jetons et les clés SSH est traitée au [Chapitre 4 : Intégration aux plateformes](../04-platform-integration/01-integration-fundamentals.md#choose-https-or-ssh) ; choisissez la forme qui correspond déjà à la façon dont vous vous authentifiez sur la plateforme.

## Inspecter et gérer les dépôts distants

```bash
git remote -v
```

Liste chaque dépôt distant configuré et son URL de fetch et de push. Un dépôt fraîchement cloné affiche `origin` ; ajoutez-en un autre avec `git remote add <name> <url>`, ou modifiez-en un existant avec `git remote set-url <name> <url>` (par exemple pour passer `origin` de HTTPS à SSH sans recloner).

## Pièges courants

- **Exécuter `git clone` dans un répertoire déjà existant.** Git refuse de cloner dans un répertoire non vide, donc `git clone <url>` dans un dossier de projet existant échoue ; clonez dans un nouveau répertoire ou passez un nom de répertoire cible en second argument.
- **Exécuter `git init` dans un dépôt déjà cloné.** Cela réinitialise `.git/` sur place — généralement sans danger (l'historique et la configuration existants sont préservés) — mais ce n'est rarement ce que vous vouliez faire ; vérifiez `git status` ou cherchez un `.git/` existant si vous doutez qu'un dossier soit déjà un dépôt.
- **Supposer qu'un clone utilise toujours `origin`.** `origin` n'est que le nom conventionnel que Git attribue automatiquement ; un dépôt peut avoir zéro, un ou plusieurs dépôts distants sous n'importe quel nom.

## Exercice

Créez un répertoire vide, exécutez `git init` à l'intérieur, puis `git remote -v` et vérifiez qu'il n'affiche rien (aucun dépôt distant configuré pour l'instant). Dans un autre répertoire, clonez un dépôt public quelconque en HTTPS, puis exécutez de nouveau `git remote -v` et vérifiez qu'`origin` apparaît désormais avec une URL de fetch et une URL de push.

## Références

Voici les sources officielles utilisées pour cette page :

- Manuel de référence de Git — [git-init](https://git-scm.com/docs/git-init)
- Manuel de référence de Git — [git-clone](https://git-scm.com/docs/git-clone)
- Pro Git (2e édition) — [Démarrer un dépôt Git](https://git-scm.com/book/fr/v2/Les-bases-de-Git-D%c3%a9marrer-un-d%c3%a9p%c3%b4t-Git)
