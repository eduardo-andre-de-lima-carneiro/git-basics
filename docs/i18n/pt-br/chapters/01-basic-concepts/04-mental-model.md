# 1.4 O modelo mental do Git

Pense em três lugares:

1. Árvore de trabalho: arquivos que estão sendo editados.
2. Área de staging: o próximo instantâneo que está sendo preparado.
3. Histórico do repositório: instantâneos confirmados por commits.

O fluxo básico é `edit -> git add -> git commit`. `git status` mostra as diferenças entre esses lugares e deve ser seu comando de diagnóstico mais frequente.

## Por que o staging é uma etapa separada

A área de staging (também chamada de índice) permite montar um commit usando apenas parte das suas alterações — por exemplo, colocar em staging uma correção já pronta com `git add`, enquanto deixa uma edição não relacionada e ainda em andamento fora do staging, na árvore de trabalho. O que acaba entrando no commit é exatamente o que estava em staging no momento em que você executou `git commit`, não o que o arquivo se parece depois disso. Veja [Gravando Alterações no Repositório](https://git-scm.com/book/pt-br/v2/Fundamentos-do-Git-Gravando-Altera%C3%A7%C3%B5es-no-Reposit%C3%B3rio) no livro Pro Git.

## Armadilhas comuns

- **Um commit não é um diff.** Cada commit aponta para um instantâneo completo da árvore do projeto, não para uma delta em relação ao commit anterior; o Git calcula diffs sob demanda, comparando dois instantâneos. É por isso que fazer checkout de um commit antigo é uma troca direta na árvore de arquivos, e não a reaplicação de uma cadeia de patches. Veja [What is Git?](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-O-que-%C3%A9-Git%3F).
- **Staged e modified não são o mesmo estado.** Se você editar um arquivo novamente depois do `git add`, o `git status` vai mostrá-lo como staged e modified ao mesmo tempo — a cópia em staging fica congelada no momento em que você executou `add`, e é preciso um novo `git add` para atualizá-la.

## Prática

Altere um arquivo, execute `git add`, depois altere o mesmo arquivo novamente sem colocá-lo em staging de novo. Execute `git status`, depois `git diff` (árvore de trabalho vs. staging) e `git diff --staged` (staging vs. último commit), para ver os três lugares divergirem.

## Referências

Esta página se baseia nas seguintes fontes oficiais:

- Pro Git (2ª ed.) — [Gravando Alterações no Repositório](https://git-scm.com/book/pt-br/v2/Fundamentos-do-Git-Gravando-Altera%C3%A7%C3%B5es-no-Reposit%C3%B3rio)
- Pro Git (2ª ed.) — [What is Git?](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-O-que-%C3%A9-Git%3F)
- Manual de referência do Git — [git-status](https://git-scm.com/docs/git-status/pt_BR)
- Manual de referência do Git — [git-diff](https://git-scm.com/docs/git-diff/pt_BR)
