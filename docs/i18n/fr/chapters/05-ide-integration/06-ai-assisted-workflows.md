# 5.6 Flux assistés par IA

Cette section est facultative. De nombreux éditeurs proposent désormais des assistants IA capables de rédiger des messages de commit, de résumer un diff, d'expliquer un conflit ou de suggérer la description d'une pull request.

## Où cela apparaît

- **Visual Studio Code** et **Visual Studio** : GitHub Copilot peut générer un message de commit à partir des changements préparés et rédiger le texte de la pull request.
- **IDE JetBrains** : l'AI Assistant propose « Generate Commit Message » dans la fenêtre **Commit**.
- Des clients autonomes comme GitKraken exposent des aides similaires pour les messages de commit.

## Comment l'utiliser en toute sécurité

- Traitez le texte généré comme un premier jet. Lisez le diff vous-même et modifiez le message pour qu'il dise *pourquoi*, pas seulement *quoi*.
- Ne laissez jamais un assistant préparer ou valider des changements que vous n'avez pas relus.
- Supposez que le diff et le contenu des fichiers peuvent être envoyés à un service externe. N'utilisez pas ces fonctions sur des dépôts contenant des secrets ou du code restreint sans l'accord de votre organisation.
- Conservez les conventions de message déjà convenues par votre équipe ; un assistant ne les connaît pas sauf si on les lui indique.

## Exercice

Préparez un petit changement dans un dépôt d'exercice et demandez un message de commit à l'assistant de votre éditeur. Réécrivez-le avec vos propres mots pour expliquer la raison du changement, puis validez le commit.
