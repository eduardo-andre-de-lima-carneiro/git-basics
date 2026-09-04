# 3.6 Exercícios Práticos

Complete estes exercícios em um diretório temporário:

1. Inicialize um repositório, crie um arquivo e faça dois commits focados. Entre os commits, use `git status` e `git diff --staged` para confirmar exatamente o que cada commit vai conter antes de rodar `git commit`.
2. Crie uma branch, mude a mesma linha de forma diferente nas duas branches e resolva o conflito de merge deliberadamente, em vez de aceitar automaticamente um dos lados.
3. Adicione um remoto, busque seu histórico e compare as branches local e remota com `git log --oneline main..origin/main` antes de integrar qualquer coisa.
4. Pratique restaurar uma edição não preparada com `git restore`, retirar um arquivo da preparação com `git restore --staged` e reverter um commit publicado com `git revert` — usando a [tabela de decisão de 3.5](05-undo.md) para escolher o comando certo em cada caso.

Para cada exercício, registre o comando usado, o estado antes dele e o resultado mostrado pelo `git status`.

## Referências

- Manual do Git — [git-status](https://git-scm.com/docs/git-status)
- Manual do Git — [git-log](https://git-scm.com/docs/git-log)
- Manual do Git — [git-restore](https://git-scm.com/docs/git-restore)
- Manual do Git — [git-revert](https://git-scm.com/docs/git-revert)
