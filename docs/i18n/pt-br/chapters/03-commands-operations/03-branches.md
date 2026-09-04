# 3.3 Branches e Colaboração

Branches são nomes móveis que apontam para commits. Crie o trabalho longe da base compartilhada:

```bash
git switch -c feature/example
git switch main
git merge feature/example
```

## O que `switch -c` e `merge` realmente fazem

- O [`git switch -c <nome>`](https://git-scm.com/docs/git-switch) cria a nova branch e troca para ela em um único passo transacional — equivalente a `git branch <nome>` seguido de `git switch <nome>`, exceto que a branch nunca fica meio criada se a troca falhar.
- O [`git merge`](https://git-scm.com/docs/git-merge) se comporta de forma diferente dependendo do formato do histórico:
  - **Fast-forward:** se a ponta da branch atual é ancestral da branch que está sendo mesclada — nenhum commit local divergiu — o Git apenas move o ponteiro da branch para frente. Nenhum commit de merge é criado.
  - **Commit de merge:** se as duas branches têm commits que a outra não tem, o Git cria um novo commit com dois pais para combiná-las. Passe `--no-ff` para forçar um commit de merge mesmo quando um fast-forward seria possível, se você quiser manter a existência da branch visível no histórico.

## Conflito é uma decisão, não uma falha

Antes de mesclar, inspecione o histórico e resolva os conflitos deliberadamente. Um conflito significa que as mesmas linhas mudaram dos dois lados e o Git não consegue adivinhar qual versão — ou combinação — está correta; é um pedido de decisão humana, não uma falha de comando para esconder aceitando um dos lados às cegas.

## Armadilhas comuns

- Branches de vida longa acumulam divergência e produzem conflitos maiores e mais difíceis de resolver. Mesclar a `main` na branch de feature periodicamente (ou fazer rebase dela, para trabalho ainda não publicado) mantém o merge final pequeno.
- `git merge --no-ff` versus um fast-forward simples muda permanentemente a aparência do seu histórico — combine uma convenção com a equipe em vez de misturar os dois de forma inconsistente.

## Exercício

Em um repositório de prática, crie uma branch, faça um commit e mescle-a de volta na `main` sem nenhum outro commit no meio — confirme com `git log --oneline --graph` que nenhum commit de merge foi criado (um fast-forward). Depois crie uma segunda branch, faça um commit também na `main` e mescle de novo — confirme que desta vez um commit de merge aparece.

## Referências

- Manual do Git — [git-switch](https://git-scm.com/docs/git-switch)
- Manual do Git — [git-branch](https://git-scm.com/docs/git-branch)
- Manual do Git — [git-merge](https://git-scm.com/docs/git-merge)
- Pro Git (2ª ed.) — [Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
