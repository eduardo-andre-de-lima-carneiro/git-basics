# 1.3 O modelo distribuído do Git

Um repositório individual normalmente tem uma árvore de trabalho, um histórico local e repositórios remotos opcionais. Um remoto é um ponto de colaboração, não a definição do Git. Veja a [visão geral sobre controle de versão](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-Sobre-Controle-de-Vers%C3%A3o) do livro Pro Git para entender como isso difere de um VCS centralizado.

## Operações comuns

As operações comuns têm finalidades diferentes:

- [`clone`](https://git-scm.com/docs/git-clone/pt_BR) copia um repositório, incluindo todo o seu histórico.
- [`fetch`](https://git-scm.com/docs/git-fetch/pt_BR) baixa o histórico remoto sem alterar o trabalho local — ele apenas atualiza as branches de rastreamento remoto (ex.: `origin/main`).
- [`pull`](https://git-scm.com/docs/git-pull/pt_BR) executa `fetch` e depois integra o resultado na branch atual (merge ou rebase, dependendo da configuração).
- [`push`](https://git-scm.com/docs/git-push/pt_BR) publica commits locais em um remoto.

## Armadilhas comuns

- **"Distribuído" não significa "sem servidor central na prática."** O próprio Git não exige um repositório central — qualquer clone pode agir como remoto para qualquer outro — mas a maioria das equipes ainda designa um remoto (frequentemente hospedado no GitHub, GitLab ou similar) como a fonte de verdade compartilhada, por convenção, e não porque o Git exija isso tecnicamente.
- **`fetch` é seguro, `pull` pode surpreender.** Como `pull` também faz merge ou rebase, execute [`git fetch`](https://git-scm.com/docs/git-fetch/pt_BR) primeiro se quiser inspecionar as mudanças recebidas antes que elas toquem sua branch de trabalho.
- **O nome de um remoto é apenas um rótulo.** [`git remote`](https://git-scm.com/docs/git-remote/pt_BR) mostra os nomes curtos (como `origin`) mapeados para URLs reais; o nome não tem nenhum significado especial para o Git além desse mapeamento.

## Exercício

Execute `git remote -v` em um clone existente para ver as URLs por trás dos nomes de seus remotos. Depois execute `git fetch` e compare `git log main` com `git log origin/main` — a diferença é exatamente o que `pull` traria.

## Referências

Esta página se baseia nas seguintes fontes oficiais:

- Pro Git (2ª ed.) — [Sobre Controle de Versão](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-Sobre-Controle-de-Vers%C3%A3o)
- Manual de referência do Git — [git-clone](https://git-scm.com/docs/git-clone/pt_BR)
- Manual de referência do Git — [git-fetch](https://git-scm.com/docs/git-fetch/pt_BR)
- Manual de referência do Git — [git-pull](https://git-scm.com/docs/git-pull/pt_BR)
- Manual de referência do Git — [git-push](https://git-scm.com/docs/git-push/pt_BR)
- Manual de referência do Git — [git-remote](https://git-scm.com/docs/git-remote/pt_BR)
