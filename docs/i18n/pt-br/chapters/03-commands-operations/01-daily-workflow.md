# 3.1 O Fluxo de Trabalho Diário

Toda mudança passa por três lugares antes de estar segura: a **árvore de trabalho** (working tree, os arquivos que você edita), a **área de preparação** ou índice (o que entrará no próximo commit) e o **histórico do repositório** (commits já registrados). Use um ciclo pequeno e observável para se mover deliberadamente entre eles:

```bash
git status
git add path/to/file
git diff --staged
git commit -m "Describe the change"
git status
```

## O que cada comando realmente verifica

- O [`git status`](https://git-scm.com/docs/git-status) informa três grupos: mudanças preparadas para o commit, mudanças não preparadas e arquivos não rastreados. Saber em qual grupo um arquivo está diz exatamente o que o próximo `git add` ou `git commit` fará com ele.
- O [`git diff`](https://git-scm.com/docs/git-diff) sem argumentos compara a árvore de trabalho com o índice — ele mostra edições que você *poderia* preparar, mas ainda não preparou.
- `git diff --staged` (sinônimo de `--cached`) compara o índice com o `HEAD` — ele mostra exatamente o que o próximo commit vai conter, por isso revisá-lo antes do `git commit` captura erros que o `git diff` sozinho não mostraria.
- O [`git add`](https://git-scm.com/docs/git-add) copia o conteúdo do arquivo para o índice. É um retrato do momento em que você o executa: edite o arquivo de novo depois, e será preciso rodar `git add` outra vez para incluir essas novas edições.

## Preparando parte de um arquivo

`git add path/to/file` prepara o arquivo inteiro. Quando apenas parte das suas edições pertence a este commit, prepare blocos (hunks) individuais:

```bash
git add -p path/to/file
```

Isso percorre cada trecho alterado e pergunta se deve prepará-lo, permitindo dividir edições não relacionadas no mesmo arquivo em commits separados e focados.

## Armadilhas comuns

- `git add .` prepara tudo dentro do diretório atual, incluindo arquivos que você mexeu por motivos não relacionados (prints de depuração, configuração local, arquivos residuais do editor). Prefira nomear os caminhos explicitamente, ou use `git add -p`, e mantenha fora do controle os arquivos que nunca devem ser preparados usando o [`.gitignore`](https://git-scm.com/docs/gitignore).
- Fazer commit sem checar `git diff --staged` é a forma mais comum de mudanças não relacionadas acabarem em um commit — a área de preparação pode conter, em silêncio, mais do que você lembra de ter adicionado.

## Exercício

Em um repositório de prática, edite dois arquivos não relacionados. Prepare apenas um trecho de um dos arquivos com `git add -p`, confirme com `git status` e `git diff --staged` que a área de preparação contém exatamente esse trecho, faça o commit e depois verifique que as outras edições continuam intactas com `git status`.

## Referências

- Manual do Git — [git-status](https://git-scm.com/docs/git-status)
- Manual do Git — [git-diff](https://git-scm.com/docs/git-diff)
- Manual do Git — [git-add](https://git-scm.com/docs/git-add)
- Manual do Git — [gitignore](https://git-scm.com/docs/gitignore)
- Pro Git (2ª ed.) — [Recording Changes to the Repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)
