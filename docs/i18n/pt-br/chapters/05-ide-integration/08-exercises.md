# 5.8 Exercícios práticos

Faça estes em um repositório temporário, usando o seu editor para as ações de Git e um terminal para verificar.

1. Prepare um único hunk (não o arquivo inteiro) a partir da visão de diff do editor, confirme o commit e verifique com `git show`.
2. Crie e mude para uma branch pela barra de status, faça um commit e volte para a anterior.
3. Configure o seu editor como `core.editor`, execute `git commit` sem `-m` e escreva a mensagem no editor.
4. Crie um conflito de merge em uma linha, resolva-o com a visão de três painéis do editor e finalize o merge.
5. Configure `merge.tool` e repita o exercício 4 usando `git mergetool` em vez do painel embutido.
6. Faça um commit assinado pelo editor e verifique-o com `git log --show-signature`.

Para cada exercício, registre a ação feita no editor e a saída de comando que confirmou o resultado.

## Referências

- Manual do Git — [git-mergetool](https://git-scm.com/docs/git-mergetool)
- Manual do Git — [git-difftool](https://git-scm.com/docs/git-difftool)
- Pro Git (2ª ed.) — [Signing Your Work](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work)
