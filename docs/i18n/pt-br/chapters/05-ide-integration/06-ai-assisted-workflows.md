# 5.6 Fluxos assistidos por IA

Esta seção é opcional. Muitos editores agora oferecem assistentes de IA que podem rascunhar mensagens de commit, resumir um diff, explicar um conflito ou sugerir a descrição de um pull request.

## Onde isso aparece

- **Visual Studio Code** e **Visual Studio**: o [GitHub Copilot pode gerar uma mensagem de commit](https://docs.github.com/pt/copilot/responsible-use/copilot-commit-message-generation) a partir das mudanças preparadas e rascunhar o texto do pull request. O VS Code também expõe isso na [visão Source Control](https://code.visualstudio.com/docs/sourcecontrol/overview).
- **IDEs da JetBrains**: o [AI Assistant](https://www.jetbrains.com/help/idea/ai-assistant.html) oferece "Generate Commit Message" na janela **Commit**.
- Clientes independentes, como o GitKraken, expõem auxiliares parecidos para mensagens de commit.

## Como usar com segurança

- Trate o texto gerado como um primeiro rascunho. Leia o diff você mesmo e edite a mensagem para que ela diga *por quê*, não apenas *o quê*.
- Nunca deixe um assistente preparar ou confirmar mudanças que você não revisou.
- Assuma que o diff e o conteúdo dos arquivos podem ser enviados a um serviço externo. Não use esses recursos em repositórios com segredos ou código restrito sem a aprovação da sua organização.
- Mantenha as convenções de mensagem que a sua equipe já combinou; um assistente não as conhece a menos que seja informado.

## Exercício

Prepare uma pequena mudança em um repositório de prática e peça uma mensagem de commit ao assistente do seu editor. Reescreva-a com suas próprias palavras para explicar o motivo da mudança e então confirme o commit.

## Referências

- GitHub Docs — [Commit message generation (uso responsável do Copilot)](https://docs.github.com/pt/copilot/responsible-use/copilot-commit-message-generation)
- Visual Studio Code — [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)
- JetBrains — [AI Assistant](https://www.jetbrains.com/help/idea/ai-assistant.html)
