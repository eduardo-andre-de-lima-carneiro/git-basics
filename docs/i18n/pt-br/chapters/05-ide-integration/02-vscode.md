# 5.2 Visual Studio Code

O Visual Studio Code vem com [suporte a controle de versão Git](https://code.visualstudio.com/docs/sourcecontrol/overview) ativado quando o Git está instalado e no `PATH`.

## Fluxo principal

- A visão **Source Control** (Ctrl/Cmd+Shift+G) lista as mudanças. Passe o mouse sobre um arquivo e clique em **+** para prepará-lo, ou prepare um único bloco a partir do editor de diff.
- Digite uma mensagem na caixa de commit e pressione Ctrl/Cmd+Enter para confirmar.
- O nome da branch na barra de status, no canto inferior esquerdo, abre o menu de troca e criação de branches.
- **Sync Changes** executa `git pull` e depois `git push` para a branch atual.
- A visão **Timeline**, na parte inferior do Explorer, mostra o histórico de commits de um arquivo.

## Usar o VS Code como editor do Git

```bash
git config --global core.editor "code --wait"
```

A opção `--wait` faz o Git pausar até você fechar a aba, o que é necessário para mensagens de commit e rebase interativo.

## Extensões úteis

- [**GitLens**](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) adiciona blame linha a linha, um grafo de commits e navegação pelo histórico.
- [**GitHub Pull Requests and Issues**](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github) permite criar, revisar e mesclar pull requests sem sair do editor.

Instale extensões apenas de publicadores em que você confia e revise as permissões que elas solicitam.

## Exercício

Defina `core.editor` como `code --wait` e execute `git commit` sem `-m` em um repositório de prática. Escreva a mensagem na aba do VS Code, salve e feche; confirme o commit com `git log --oneline`.

## Referências

- Visual Studio Code — [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)
- Visual Studio Marketplace — [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- Visual Studio Marketplace — [GitHub Pull Requests and Issues](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)
- Manual do Git — [git-config](https://git-scm.com/docs/git-config)
