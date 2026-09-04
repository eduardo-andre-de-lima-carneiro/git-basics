# 3.5 Desfazer Alterações com Segurança

O Git tem três comandos diferentes de "desfazer", e eles atuam em três lugares diferentes. Escolher o certo depende de onde a mudança indesejada está e se mais alguém já a viu.

## Tabela de decisão: restore vs. revert vs. reset

| Comando | Atua sobre | Reescreve histórico publicado? | Uso típico | Segurança / recuperação |
| --- | --- | --- | --- | --- |
| [`git restore <arquivo>`](https://git-scm.com/docs/git-restore) | Árvore de trabalho (destino padrão) | Não — não é uma operação de histórico | Descartar edições indesejadas e não commitadas em um arquivo | O conteúdo descartado se vai; o Git não mantém reflog de edições da árvore de trabalho, então faça backup do que precisar antes |
| `git restore --staged <arquivo>` | Apenas a área de preparação (índice) | Não | Retirar da preparação um arquivo adicionado por engano, mantendo suas edições na árvore de trabalho | Seguro — a árvore de trabalho não é tocada, nada se perde |
| [`git revert <commit>`](https://git-scm.com/docs/git-revert) | Histórico, adicionando um novo commit | Não — grava um novo commit que reverte a mudança em vez de alterar commits existentes | Desfazer o efeito de um commit que já foi enviado ou compartilhado | Seguro em branches compartilhadas; pode exigir resolução de conflito se commits posteriores tocaram as mesmas linhas |
| [`git reset [--soft\|--mixed\|--hard] <commit>`](https://git-scm.com/docs/git-reset) | `HEAD` e o índice; `--hard` também sobrescreve a árvore de trabalho | Sim — move o ponteiro da branch, descartando commits do histórico dela | Desfazer commits locais e ainda não publicados, ou retirar tudo da preparação de uma vez | Nunca use em commits que outra pessoa já tem; commits descartados costumam ficar recuperáveis por um tempo via [`git reflog`](https://git-scm.com/docs/git-reflog), mas o `--hard` também descarta edições não commitadas da árvore de trabalho, que o reflog não consegue trazer de volta |

Os três modos de `reset` diferem em até onde desfazem: `--soft` move apenas o `HEAD` (índice e árvore de trabalho intocados — útil para agrupar commits recentes antes de recommitar), `--mixed` (o padrão) também reseta o índice, de modo que nada fica preparado, e `--hard` ainda sobrescreve a árvore de trabalho para igualá-la ao commit alvo.

## Por que essa ordem de preferência importa

Prefira `restore` e `revert` por padrão, porque nenhum dos dois pode alterar histórico do qual outras pessoas dependem. Recorra ao `reset` só quando tiver certeza de que os commits em questão ainda são privados — a documentação oficial é explícita: não faça reset descartando commits que você já deu a outra pessoa, porque o histórico local dela vai divergir silenciosamente do seu.

## Armadilhas comuns

- Confundir `git restore <arquivo>` (árvore de trabalho) com `git restore --staged <arquivo>` (índice) é o erro mais comum — a flag muda qual camada é afetada, não apenas quanto é desfeito.
- `git reset --hard` é o único comando desta tabela que pode destruir trabalho não commitado sem caminho de recuperação. Rode `git status` imediatamente antes dele.
- Rode `git status` antes e depois de qualquer comando de recuperação — é a forma mais barata de confirmar que você mudou a camada que pretendia.

## Exercício

Em um repositório de prática: (1) edite um arquivo sem prepará-lo, depois descarte a edição com `git restore`; (2) prepare um arquivo, depois retire-o da preparação com `git restore --staged` e confirme que a edição ainda está presente; (3) faça commit de uma mudança, depois desfaça seu efeito com `git revert` e confirme que agora existem dois commits; (4) faça mais um commit, desfaça-o localmente com `git reset --mixed HEAD~1`, confirme com `git status` que a mudança agora está fora da preparação, e depois encontre o commit descartado de novo com `git reflog`.

## Referências

- Manual do Git — [git-restore](https://git-scm.com/docs/git-restore)
- Manual do Git — [git-revert](https://git-scm.com/docs/git-revert)
- Manual do Git — [git-reset](https://git-scm.com/docs/git-reset)
- Manual do Git — [git-reflog](https://git-scm.com/docs/git-reflog)
- Pro Git (2ª ed.) — [Reset Demystified](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified)
