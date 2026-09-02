# Git Basics

> Apprenez Git en comprenant ce qu'il est, en pratiquant ce qu'il fait et en gagnant en confiance, une petite étape à la fois.

Git Basics est une formation pratique et guidée pour les personnes qui débutent avec Git, qui viennent de Subversion ou qui cherchent un modèle mental plus clair du contrôle de version au quotidien.

[Commencer la formation](menu.md) | [Choisir votre langue](#langues) | [Contribuer](../../../CONTRIBUTING.md)

## Pourquoi cette formation existe

La documentation Git peut être techniquement exacte tout en restant difficile à aborder. Ce projet transforme les notions essentielles en un parcours guidé : des explications courtes, de vraies commandes, des résultats visibles et des exercices à pratiquer dans un dépôt temporaire.

L'objectif n'est pas de mémoriser une liste de commandes. Il est de comprendre l'état de votre projet, d'effectuer des changements intentionnels et de retrouver son calme quand quelque chose ne se passe pas comme prévu.

## Ce que vous apprendrez

- Comment le contrôle de version protège et explique l'historique d'un projet.
- Comment s'articulent l'arbre de travail, la zone de préparation, les commits, les branches et les dépôts distants de Git.
- Comment installer et configurer Git pour des projets personnels ou d'équipe.
- Comment examiner les changements avant de les valider.
- Comment créer des branches, synchroniser des dépôts distants et collaborer en toute sécurité.
- Comment choisir la bonne commande pour récupérer un changement indésirable.

## Parcours de la formation

| Chapitre | Thème | Vous pratiquerez |
| --- | --- | --- |
| [1. Concepts fondamentaux](chapters/01-basic-concepts/README.md) | Les idées à la base du contrôle de version et de Git | Réfléchir en instantanés, en historique et en états du projet |
| [2. Installation et configuration](chapters/02-installation-configuration/README.md) | Préparer Git à l'emploi | Vérifier l'installation, l'identité, les valeurs par défaut et les dépôts |
| [3. Commandes et opérations](chapters/03-commands-operations/README.md) | Construire un flux de travail quotidien fiable | Les commits, les branches, les dépôts distants, les fusions, les exercices et la récupération |
| [4. Intégration aux plateformes](chapters/04-platform-integration/README.md) | Connecter Git aux plateformes de collaboration hébergées | Les pull requests, les merge requests, les permissions, l'automatisation et une livraison sécurisée |

## Un premier exercice rapide

Une fois Git installé, créez un dépôt temporaire pour vous exercer :

```bash
mkdir git-practice
cd git-practice
git init
printf "My first Git file\n" > notes.txt
git add notes.txt
git commit -m "Add first practice file"
git log --oneline
```

Vous venez de créer un dépôt, de préparer un changement, d'enregistrer un commit et d'examiner son historique. Le chapitre 1 explique ce qui s'est passé à chaque étape.

## Comment utiliser la documentation

1. Commencez par le [menu de la documentation](menu.md).
2. Lisez le chapitre 1 avant de vous plonger dans la mémorisation des commandes.
3. Suivez les étapes de mise en place du chapitre 2.
4. Parcourez le chapitre 3 dans un dépôt temporaire.
5. Découvrez dans le chapitre 4 la plateforme utilisée par votre équipe.
6. Consultez le [glossaire](glossary.md) lorsqu'un terme vous est inconnu.

Chaque leçon est un fichier Markdown autonome, relié par des chemins relatifs afin de pouvoir être consultée directement sur GitHub.

## Langues

La formation est disponible en quatre langues :

- [English](../../../README.md)
- [Français](README.md)
- [Português (Brasil)](../pt-br/README.md)
- [Español](../es/README.md)

## Valeurs du projet

- **Pratique :** les exemples doivent aboutir à quelque chose que l'apprenant peut observer.
- **Accessible :** expliquer l'idée avant d'introduire la commande.
- **Sûr :** utiliser des dépôts temporaires et expliciter les opérations destructrices.
- **Ouvert :** conserver une documentation libre, réutilisable et facile à améliorer.

## Contribuer

Vous avez trouvé une explication confuse, un exercice manquant ou un lien brisé ? Consultez le [guide de contribution](../../../CONTRIBUTING.md) et aidez à rendre la première expérience de Git plus agréable pour les prochains apprenants.

## Origine

Cette formation est née d'une expérience en DevSecOps, au cours de laquelle j'ai accompagné des équipes qui migraient de Subversion vers Git. La documentation officielle et les sites de référence étaient utiles, mais certains apprenants avaient besoin d'un parcours plus guidé et plus pratique pour aborder le sujet. Git Basics a été créé pour leur proposer ce parcours et faciliter le partage de l'apprentissage.

Le projet est volontairement collaboratif. Les retours, corrections, exemples et traductions sont les bienvenus.
