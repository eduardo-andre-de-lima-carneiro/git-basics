# 1.2 Pourquoi Git

Git est distribué : chaque clone contient l'historique du projet nécessaire à la plupart des opérations locales. Les commits, les comparaisons et la création de branches sont ainsi rapides et disponibles hors ligne.

Git fournit également des points de contrôle explicites appelés commits. Un bon commit répond aux questions suivantes : qu'est-ce qui a changé et pourquoi?

## D'où vient Git

Git a été créé en 2005 par Linus Torvalds et la communauté du noyau Linux, après que l'outil propriétaire utilisé jusque-là par le projet, BitKeeper, a cessé d'être disponible gratuitement. Les objectifs de conception étaient la vitesse, une conception simple, un support solide du développement non linéaire (les branches), le fait d'être entièrement distribué, et la capacité à gérer efficacement de grands projets comme le noyau Linux lui-même. Voir la [rapide histoire de Git](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-Une-rapide-histoire-de-Git) dans le livre Pro Git pour l'histoire complète.

## Des instantanés, pas des diffs

Contrairement aux systèmes qui stockent une liste de changements par fichier, Git stocke un instantané de l'ensemble du projet à chaque commit ; un fichier qui n'a pas changé est simplement relié à la version identique précédente plutôt que d'être dupliqué. Chaque objet est doté d'une somme de contrôle avant d'être stocké — historiquement avec SHA-1, SHA-256 étant disponible comme option plus récente via la [transition de fonction de hachage](https://git-scm.com/docs/hash-function-transition) de Git — de sorte qu'une corruption silencieuse ou une falsification soit détectable. Voir [Rudiments de Git](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-Rudiments-de-Git) dans le livre Pro Git.

## Git vs. Subversion vs. Mercurial

| | Git | Subversion (SVN) | Mercurial |
|---|---|---|---|
| Modèle | [Distribué](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-%C3%80-propos-de-la-gestion-de-version) | [Centralisé](https://subversion.apache.org/) | [Distribué](https://www.mercurial-scm.org/) |
| Coût des branches | Une branche est un pointeur mobile vers un commit — [quasi instantanée à créer](https://git-scm.com/book/fr/v2/Les-branches-avec-Git-Les-branches-en-bref) | Une [copie bon marché côté serveur](https://svnbook.red-bean.com/en/1.7/svn.branchmerge.using.html), mais sa création et son utilisation exigent encore le serveur central | Bon marché ; les branches et signets vivent dans le clone local |
| Capacité hors ligne | Totale — commit, diff, log et branche fonctionnent sans réseau | Limitée — la plupart des opérations doivent contacter le serveur | Totale — « chaque clone contient tout l'historique du projet » |
| Usage typique aujourd'hui | Choix par défaut pour la plupart des nouveaux projets ; utilisé par [96 % des développeurs professionnels](https://git-scm.com/about) (enquête Stack Overflow 2022) | Encore présent dans certaines entreprises voulant un contrôle d'accès centralisé sur l'historique | De niche ; surtout des déploiements hérités, largement supplanté par Git |

## Pièges courants

- **Un commit n'est pas un diff.** Git enregistre l'instantané complet préparé dans la zone de staging au moment du commit, pas seulement ce qui a changé — c'est ce qui fait qu'extraire un ancien commit est une opération directe sur l'arborescence des fichiers, plutôt que de rejouer une chaîne de patches. Voir [Enregistrer des modifications dans le dépôt](https://git-scm.com/book/fr/v2/Les-bases-de-Git-Enregistrer-des-modifications-dans-le-d%c3%a9p%c3%b4t).

## Idée clé

Git n'est pas seulement un système de sauvegarde de fichiers. C'est un outil qui sert à construire, examiner et partager une chronologie de changements intentionnels.

## Références

Cette page s'appuie sur les sources officielles suivantes :

- Pro Git (2ᵉ éd.) — [Une rapide histoire de Git](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-Une-rapide-histoire-de-Git)
- Pro Git (2ᵉ éd.) — [Rudiments de Git](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-Rudiments-de-Git)
- Manuel de référence de Git — [Transition de fonction de hachage de Git](https://git-scm.com/docs/hash-function-transition)
- git-scm.com — [About Git](https://git-scm.com/about)
- Apache Subversion — [subversion.apache.org](https://subversion.apache.org/)
- Mercurial — [mercurial-scm.org](https://www.mercurial-scm.org/)
