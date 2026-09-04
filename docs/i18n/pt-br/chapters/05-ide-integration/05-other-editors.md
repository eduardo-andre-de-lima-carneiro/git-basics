# 5.5 Outros editores

Os mesmos conceitos de Git aparecem em muitas outras ferramentas. Esta é uma orientação breve, não um guia completo de cada uma.

- O [**Xcode**](https://developer.apple.com/documentation/xcode/source-control-management) tem um menu e um navegador **Source Control** para commit, push, pull, branch e resolução de conflitos em projetos macOS.
- O **Eclipse** usa o plugin [**EGit**](https://wiki.eclipse.org/EGit/User_Guide), que adiciona uma visão **Git Staging** e uma visão **History**.
- O [**Sublime Merge**](https://www.sublimemerge.com/docs/) é um cliente Git independente dos criadores do Sublime Text, com grafo de commits rápido e preparação por hunk; o Sublime Text se integra a ele.
- **Vim e Neovim** costumam usar o [`vim-fugitive`](https://github.com/tpope/vim-fugitive) para comandos e o [`gitsigns.nvim`](https://github.com/lewis6991/gitsigns.nvim) (Neovim) ou o `vim-gitgutter` para marcações na margem.
- O **Emacs** conta com o [**Magit**](https://magit.vc/), uma interface guiada pelo teclado que espelha a maioria dos comandos do Git.
- O [**GitHub Desktop**](https://docs.github.com/pt/desktop) e o **GitKraken** são clientes gráficos que combinam bem com qualquer editor.

Seja qual for a ferramenta, ela está chamando o Git. Se um painel e o `git status` divergirem, atualize o painel ou confie na linha de comando.

## Exercício

Escolha uma ferramenta desta lista que você normalmente não usa. Abra um repositório de prática nela, faça um commit e verifique o resultado com `git log --oneline` em um terminal.

## Referências

- Apple Developer — [Source control management in Xcode](https://developer.apple.com/documentation/xcode/source-control-management)
- Eclipse — [EGit User Guide](https://wiki.eclipse.org/EGit/User_Guide)
- [Documentação do Sublime Merge](https://www.sublimemerge.com/docs/)
- GitHub — [tpope/vim-fugitive](https://github.com/tpope/vim-fugitive)
- GitHub — [lewis6991/gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim)
- [Magit — a Git porcelain inside Emacs](https://magit.vc/)
- GitHub Docs — [GitHub Desktop](https://docs.github.com/pt/desktop)
