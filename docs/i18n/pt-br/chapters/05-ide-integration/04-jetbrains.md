# 5.4 IDEs da JetBrains

IntelliJ IDEA, PyCharm, WebStorm, PhpStorm, Rider, GoLand e Android Studio compartilham a mesma integração com Git no menu **Git** (ou **VCS**).

## Fluxo principal

- **Git > Clone** cria o repositório local; **VCS > Enable Version Control Integration** inicia um em um projeto existente.
- A janela **Commit** lista as mudanças, agrupa-as em changelists e prepara arquivos ou hunks. Uma caixa de mensagem e os botões **Commit** / **Commit and Push** ficam abaixo dela.
- A aba **Log** da janela **Git** mostra o grafo completo de branches, com filtros por branch, usuário e caminho.
- O widget de branch na barra de status troca, cria e compara branches.
- **Update Project** executa fetch mais merge ou rebase, conforme a sua configuração.
- Conflitos abrem um resolvedor de três painéis com **Accept Left**, **Accept Right** e edição manual no painel de resultado.

## Rebase interativo

Clique com o botão direito em um commit no **Log** e escolha **Interactively Rebase from Here** para reordenar, combinar (squash), editar ou descartar commits por um diálogo, em vez de um arquivo de texto.

## Shelve versus stash

**Shelve** é um recurso da JetBrains que reserva mudanças dentro da IDE. **Stash** é o comando do Git. Ambos funcionam; prefira stash se colegas em outros editores precisarem ver o mesmo estado salvo pelo Git.

## Exercício

Em um repositório de prática, faça duas edições não relacionadas, separe-as em dois changelists na janela **Commit** e confirme-as separadamente. Verifique os dois commits na aba **Log**.
