# 3.5 Desfazer alterações com segurança

Escolha o comando de acordo com o local onde a alteração indesejada existe:

- Árvore de trabalho: `git restore <file>`. Esse comando descarta permanentemente as alterações não commitadas da árvore de trabalho; faça uma cópia antes do que ainda puder ser necessário.
- Área de staging: `git restore --staged <file>`.
- Histórico publicado: prefira `git revert <commit>`.
- Commit local não publicado: considere `git reset` somente depois de verificar as consequências.

Execute `git status` antes e depois dos comandos de recuperação.
