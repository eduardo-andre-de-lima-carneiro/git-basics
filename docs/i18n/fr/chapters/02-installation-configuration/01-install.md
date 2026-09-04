# 2.1 Installer Git

Git 2.23 ou une version plus récente est recommandée pour les exemples `git switch` et `git restore` utilisés plus loin. Les versions plus anciennes peuvent nécessiter des commandes équivalentes comme `git checkout`. Installez Git avec le gestionnaire de paquets ou le programme d'installation recommandé pour votre système d'exploitation, listés ci-dessous, ou parcourez toutes les options sur la [page officielle des téléchargements](https://git-scm.com/downloads).

## Windows

Installez avec [winget](https://learn.microsoft.com/fr-fr/windows/package-manager/winget/install), fourni avec les versions récentes de Windows 10/11 :

```bash
winget install --id Git.Git -e --source winget
```

Vous pouvez aussi télécharger le programme d'installation depuis [git-scm.com/downloads/win](https://git-scm.com/downloads/win). Pendant l'installation, gardez l'option par défaut « Git from the command line and also from 3rd-party software » pour que `git` soit ajouté au `PATH` ; sinon, les commandes suivantes de ce cours échoueront avec « command not found » dans un nouveau terminal.

## macOS

Si vous utilisez [Homebrew](https://docs.brew.sh/Installation), installez avec :

```bash
brew install git
```

macOS propose aussi Git via les Xcode Command Line Tools :

```bash
xcode-select --install
```

Les command line tools installent un Git fonctionnel, mais souvent plus ancien que celui de Homebrew. Si vous avez besoin d'une version récente précise, préférez Homebrew et exécutez `brew upgrade git` régulièrement.

## Linux

Utilisez le gestionnaire de paquets de votre distribution. Sur Debian et Ubuntu :

```bash
sudo apt install git
```

Sur Fedora et les autres distributions basées sur `dnf` :

```bash
sudo dnf install git
```

Les dépôts des distributions peuvent avoir des mois de retard sur la dernière version de Git. Si vous avez besoin d'une version plus récente sur Ubuntu, ajoutez le [PPA git-core](https://git-scm.com/downloads/linux) avant d'installer ; sur Fedora, `dnf` suit généralement l'amont d'assez près pour que ce soit rarement nécessaire.

## Vérifier l'installation

```bash
git --version
```

La version exacte peut varier. La commande doit afficher une version et non une erreur. Si elle affiche « command not found » juste après une installation sous Windows, rouvrez le terminal (ou redémarrez) pour que le `PATH` mis à jour prenne effet.

## Après l'installation

Un Git fraîchement installé n'a ni identité ni nom de branche par défaut configurés. Avant votre premier commit, configurez-les comme décrit dans [Configurer l'identité et les valeurs par défaut](02-configure.md) — un `user.email` non configuré produit des commits attribués à une adresse générique au lieu de vous.

## Pièges courants

- **Installer depuis une source non officielle.** N'utilisez que les gestionnaires de paquets et le programme d'installation ci-dessus, ou la [page officielle des téléchargements](https://git-scm.com/downloads) ; les « installeurs Git » non officiels trouvés dans une recherche peuvent être obsolètes ou dangereux.
- **Installations multiples de Git.** Installer Git par plusieurs méthodes (par exemple les Xcode tools et Homebrew) peut laisser un `git` plus ancien en tête du `PATH`. Exécutez `which git` (macOS/Linux) ou `where git` (Windows) pour confirmer quel binaire s'exécute réellement.
- **Sauter la vérification de version.** Exécutez toujours `git --version` juste après l'installation — c'est le moyen le plus simple de confirmer que l'installation a réussi avant d'investiguer autre chose.

## Exercice

Installez Git pour votre système d'exploitation avec la méthode ci-dessus, puis exécutez `git --version` et confirmez qu'elle indique 2.23 ou une version plus récente. Si une version plus ancienne s'affiche, mettez à jour avec le même gestionnaire de paquets (`brew upgrade git`, `sudo apt update && sudo apt upgrade git` ou `winget upgrade --id Git.Git`).

## Références

Voici les sources officielles utilisées pour cette page :

- Git — [Downloads](https://git-scm.com/downloads)
- Pro Git (2e édition) — [Installation de Git](https://git-scm.com/book/fr/v2/D%c3%a9marrage-rapide-Installation-de-Git)
- Homebrew — [Installation](https://docs.brew.sh/Installation)
- Microsoft Learn — [Installer winget](https://learn.microsoft.com/fr-fr/windows/package-manager/winget/install)
