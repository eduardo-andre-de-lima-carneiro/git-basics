# 3.4 Remotos e Sincronização

Sincronize explicitamente:

```bash
git fetch origin
git log --oneline main..origin/main
git push -u origin feature/example
```

## Fetch, pull e push não são a mesma operação

- O [`git fetch`](https://git-scm.com/docs/git-fetch) baixa commits e atualiza suas referências de rastreamento remoto (`origin/main`, por exemplo), mas nunca toca na sua árvore de trabalho ou nas branches locais. É sempre seguro executá-lo.
- `git log --oneline main..origin/main` mostra então exatamente quais commits existem em `origin/main` mas ainda não na sua `main` local — um passo de revisão antes de integrar qualquer coisa.
- O [`git pull`](https://git-scm.com/docs/git-pull) executa `git fetch` e depois integra o resultado na sua branch atual. **Seu modo de integração padrão é `--ff-only`**: se sua branch local divergiu do remoto (os dois lados têm commits novos), o `git pull` simples falha em vez de criar silenciosamente um commit de merge. Passe `--rebase` para reaplicar seus commits locais sobre o histórico buscado em vez de mesclar, ou `--no-rebase` para permitir um commit de merge.
- O [`git push -u origin <branch>`](https://git-scm.com/docs/git-push) envia a branch e grava o relacionamento de rastreamento upstream (`branch.<nome>.remote` / `branch.<nome>.merge`) em um único passo. Depois disso, `git push` e `git pull` simples nessa branch sabem qual branch remota usar sem que você precise nomeá-la de novo.

## Armadilhas comuns

- `git pull --rebase` reescreve os commits que reaplica. Isso é seguro para commits que só você tem — é inseguro assim que alguém mais já buscou esses commits, porque o histórico dela e o seu deixam de bater. Reserve `--rebase` para branches que você ainda não compartilhou, e prefira um merge (ou `git pull --no-rebase`) quando outras pessoas já dependem dos seus commits.
- Como o padrão do `git pull` agora é falhar em vez de mesclar em caso de divergência, não presuma que a descrição de um tutorial antigo ("pull sempre mescla") ainda corresponde à sua versão do Git — verifique `pull.rebase` e `pull.ff` em `git config --list` se o comportamento parecer inconsistente entre máquinas.
- Faça fetch antes de fazer push ao trabalhar em uma branch compartilhada; enviar sem antes checar `main..origin/main` arrisca um push rejeitado ou um conflito evitável.

## Exercício

Em um repositório de prática com um remoto configurado, rode `git fetch origin` e depois `git log --oneline main..origin/main` para ver o que mudou remotamente antes de mexer em qualquer coisa localmente. Envie uma branch nova com `git push -u origin <branch>` e depois confirme o relacionamento de rastreamento com `git branch -vv`.

## Referências

- Manual do Git — [git-fetch](https://git-scm.com/docs/git-fetch)
- Manual do Git — [git-pull](https://git-scm.com/docs/git-pull)
- Manual do Git — [git-push](https://git-scm.com/docs/git-push)
- Pro Git (2ª ed.) — [Working with Remotes](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes)
