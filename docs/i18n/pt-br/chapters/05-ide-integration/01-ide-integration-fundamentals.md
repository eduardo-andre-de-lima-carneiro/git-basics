# 5.1 Fundamentos da integração com IDEs

A integração de Git de um editor é uma visão sobre o mesmo repositório que a linha de comando usa. Ela executa `git status`, `git diff` e `git log` por você e transforma as ações comuns em botões, marcações na margem e painéis.

## O que a integração acrescenta

- Um painel de controle de versão que lista arquivos alterados, preparados e não rastreados.
- Marcações na margem que mostram linhas adicionadas, alteradas e removidas.
- Um diff visual de um arquivo ou de um único bloco de linhas (um "hunk").
- Uma caixa de commit para a mensagem, com a preparação feita ao clicar em arquivos ou hunks.
- Um indicador de branch na barra de status para trocar e criar branches.
- Uma visão de três painéis para resolver conflitos de merge.

## Quando ainda usar o terminal

Recorra à linha de comando quando precisar de controle exato ou de uma operação incomum: detalhes de rebase interativo, `git reflog`, `git bisect`, filtros personalizados de `git log` ou automação. O editor e o terminal atuam sobre o mesmo diretório `.git`, então você pode alternar entre eles livremente.

## Configuração compartilhada

- Configure a identidade uma vez com [`git config`](https://git-scm.com/docs/git-config) `--global user.name` e `user.email` (veja [2.2 Configurar identidade e padrões](../02-installation-configuration/02-configure.md)).
- Deixe um [credential helper](https://git-scm.com/docs/gitcredentials) ou o keychain do sistema guardar os tokens para que o editor não pergunte a cada push.
- Decida se pastas específicas do editor, como `.vscode/` ou `.idea/`, devem ficar no repositório; se não, adicione-as ao [`.gitignore`](https://git-scm.com/docs/gitignore).
- Mantenha a [assinatura de commits](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work) (SSH ou GPG) configurada no próprio Git para que os commits feitos pelo editor também sejam assinados.

## Exercício

Abra um repositório de prática existente no seu editor. Altere uma linha em um arquivo e confirme que o painel de controle de versão do editor e o `git status` em um terminal relatam a mesma mudança.

## Referências

- Manual do Git — [git-config](https://git-scm.com/docs/git-config)
- Manual do Git — [gitcredentials](https://git-scm.com/docs/gitcredentials)
- Manual do Git — [gitignore](https://git-scm.com/docs/gitignore)
- Pro Git (2ª ed.) — [Signing Your Work](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work)
