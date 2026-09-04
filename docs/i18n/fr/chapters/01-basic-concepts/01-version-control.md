# 1.1 Systèmes de contrôle de version

Le contrôle de version enregistre les changements apportés aux fichiers au fil du temps. Il permet à une équipe de comparer les révisions, d'identifier leurs auteurs, de restaurer des états antérieurs et de travailler sur des changements distincts sans écraser le travail des autres.

## Le problème résolu

Sans contrôle de version, des noms de fichiers comme `project-final-final-2` finissent par constituer l'historique. Git conserve plutôt cet historique dans un dépôt structuré.

## Trois générations de contrôle de version

Les systèmes de contrôle de version se répartissent en trois grandes catégories, décrites dans la [présentation du contrôle de version](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-%C3%80-propos-de-la-gestion-de-version) du livre Pro Git :

- **VCS local** (ex. : RCS) conserve une base de patches sur une seule machine. Il n'y a aucune collaboration possible, ni aucune protection si cette machine est perdue.
- **VCS centralisé** (ex. : CVS, Subversion) stocke tout l'historique sur un serveur ; les clients récupèrent des copies de travail. La collaboration fonctionne, mais le serveur est un point unique de défaillance — s'il tombe en panne, ou si sa base de données est corrompue sans sauvegarde, l'historique du projet peut être perdu.
- **VCS distribué** (ex. : Git, Mercurial) donne à chaque clone l'historique complet. N'importe quel clone peut restaurer le projet si un serveur est perdu, et la plupart des opérations quotidiennes ne nécessitent pas le réseau.

## Pièges courants

- **Le contrôle de version n'est pas un service de sauvegarde.** Une sauvegarde copie des fichiers ; le contrôle de version enregistre aussi *pourquoi* quelque chose a changé, et permet de comparer, d'identifier l'auteur (blame) et d'annuler des changements individuels.
- **Un dépôt n'est pas la même chose qu'une simple copie extraite.** Supprimer votre copie de travail ne supprime pas l'historique déjà validé et stocké en sécurité ailleurs (localement ou sur un dépôt distant).

## Mise en pratique

Créez un petit fichier texte, modifiez-le deux fois et notez les informations dont vous auriez besoin pour retrouver la première version. Cette liste représente la valeur apportée par le contrôle de version.

## Références

Cette page s'appuie sur les sources officielles suivantes :

- Pro Git (2ᵉ éd.) — [À propos de la gestion de version](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-%C3%80-propos-de-la-gestion-de-version)
- Manuel de référence de Git — [git-scm.com/docs](https://git-scm.com/docs)
