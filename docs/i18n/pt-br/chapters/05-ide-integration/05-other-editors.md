# 5.5 Outros editores

Os mesmos conceitos de Git aparecem em muitas outras ferramentas. Esta é uma orientação breve, não um guia completo de cada uma.

- **Xcode** tem um menu e um navegador **Source Control** para commit, push, pull, branch e resolução de conflitos em projetos macOS.
- **Eclipse** usa o plugin **EGit**, que adiciona uma visão **Git Staging** e uma visão **History**.
- **Sublime Merge** é um cliente Git independente dos criadores do Sublime Text, com grafo de commits rápido e preparação por hunk; o Sublime Text se integra a ele.
- **Vim e Neovim** costumam usar o `vim-fugitive` para comandos e o `gitsigns` (Neovim) ou o `vim-gitgutter` para marcações na margem.
- **Emacs** conta com o **Magit**, uma interface guiada pelo teclado que espelha a maioria dos comandos do Git.
- **GitHub Desktop** e **GitKraken** são clientes gráficos que combinam bem com qualquer editor.

Seja qual for a ferramenta, ela está chamando o Git. Se um painel e o `git status` divergirem, atualize o painel ou confie na linha de comando.

## Exercício

Escolha uma ferramenta desta lista que você normalmente não usa. Abra um repositório de prática nela, faça um commit e verifique o resultado com `git log --oneline` em um terminal.
