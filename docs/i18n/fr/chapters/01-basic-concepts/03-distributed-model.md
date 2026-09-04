# 1.3 Le modèle distribué de Git

Un dépôt individuel possède généralement un arbre de travail, un historique local et, éventuellement, des dépôts distants. Un dépôt distant est un point de collaboration, et non la définition de Git lui-même. Voir la [présentation du contrôle de version](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-%C3%80-propos-de-la-gestion-de-version) du livre Pro Git pour comprendre en quoi cela diffère d'un VCS centralisé.

## Opérations courantes

Les opérations courantes ont des objectifs distincts :

- [`clone`](https://git-scm.com/docs/git-clone/fr) copie un dépôt, y compris tout son historique.
- [`fetch`](https://git-scm.com/docs/git-fetch/fr) télécharge l'historique distant sans modifier le travail local — il ne fait que mettre à jour les branches de suivi distant (ex. : `origin/main`).
- [`pull`](https://git-scm.com/docs/git-pull/fr) exécute `fetch`, puis intègre le résultat dans la branche courante (fusion ou rebase, selon la configuration).
- [`push`](https://git-scm.com/docs/git-push/fr) publie les commits locaux vers un dépôt distant.

## Pièges courants

- **« Distribué » ne signifie pas « sans serveur central en pratique ».** Git lui-même n'exige aucun dépôt central — n'importe quel clone peut servir de dépôt distant pour n'importe quel autre — mais la plupart des équipes désignent tout de même un dépôt distant (souvent hébergé sur GitHub, GitLab ou équivalent) comme source de vérité partagée, par convention, et non parce que Git l'exige techniquement.
- **`fetch` est sûr, `pull` peut surprendre.** Comme `pull` fait aussi une fusion ou un rebase, exécutez d'abord [`git fetch`](https://git-scm.com/docs/git-fetch/fr) si vous voulez examiner les changements entrants avant qu'ils n'affectent votre branche de travail.
- **Le nom d'un dépôt distant n'est qu'une étiquette.** [`git remote`](https://git-scm.com/docs/git-remote/fr) affiche les noms courts (comme `origin`) associés à des URL réelles ; le nom n'a aucune signification particulière pour Git au-delà de cette correspondance.

## Exercice

Exécutez `git remote -v` dans un clone existant pour voir les URL derrière les noms de ses dépôts distants. Exécutez ensuite `git fetch` et comparez `git log main` avec `git log origin/main` — la différence est exactement ce que `pull` rapatrierait.

## Références

Cette page s'appuie sur les sources officielles suivantes :

- Pro Git (2ᵉ éd.) — [À propos de la gestion de version](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-%C3%80-propos-de-la-gestion-de-version)
- Manuel de référence de Git — [git-clone](https://git-scm.com/docs/git-clone/fr)
- Manuel de référence de Git — [git-fetch](https://git-scm.com/docs/git-fetch/fr)
- Manuel de référence de Git — [git-pull](https://git-scm.com/docs/git-pull/fr)
- Manuel de référence de Git — [git-push](https://git-scm.com/docs/git-push/fr)
- Manuel de référence de Git — [git-remote](https://git-scm.com/docs/git-remote/fr)
