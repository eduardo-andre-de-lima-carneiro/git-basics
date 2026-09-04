# 2.3 Repositórios locais e remotos

## `git init` vs. `git clone`

Comece um projeto novo localmente com [`git init`](https://git-scm.com/docs/git-init):

```bash
git init
```

Isso cria um subdiretório `.git` na pasta atual e a transforma em um repositório Git sem commits e sem remoto configurado. Copie um projeto existente — histórico incluído — com [`git clone`](https://git-scm.com/docs/git-clone):

```bash
git clone <repository-url>
```

O `git clone` cria um novo diretório, copia todo o histórico, faz checkout da branch padrão e configura automaticamente um remoto chamado `origin` apontando para a origem. Use `git init` quando um projeto ainda não existe como repositório Git; use `git clone` quando ele já existe, seja em uma plataforma de hospedagem ou em um caminho local.

## O que o `.git/` realmente contém

Ambos os comandos deixam você com um diretório `.git/` contendo os dados reais do repositório — os arquivos de trabalho que você vê são apenas um instantâneo obtido a partir dele. Ele inclui:

- `objects/` — o armazenamento endereçado por conteúdo dos commits, trees e blobs (o histórico propriamente dito).
- `refs/heads/` e `refs/tags/` — ponteiros para as pontas das branches e para as tags.
- `HEAD` — qual branch (ou commit) está atualmente em checkout.
- `config` — a configuração local do repositório (escopo `--local`, veja [2.2](02-configure.md)).
- Após um clone, `refs/remotes/origin/` mais `remote.origin.url` e `remote.origin.fetch` em `config`, registrando de onde o repositório foi clonado.

Apagar o `.git/` apaga todo o histórico do repositório; os arquivos de trabalho que restarem deixam de ser rastreados pelo Git.

## URLs de remoto: HTTPS vs. SSH

Uma URL de remoto assume uma das duas formas comuns:

```bash
# HTTPS
https://github.com/OWNER/REPOSITORY.git

# SSH
git@github.com:OWNER/REPOSITORY.git
```

O HTTPS funciona em qualquer rede sem configuração local extra e autentica com um token de acesso pessoal em vez da senha da sua conta; é o ponto de partida mais simples. O SSH autentica com um par de chaves registrado na plataforma e é mais conveniente para pushes frequentes depois de configurado, já que não pede um token a cada vez. Ambas as formas funcionam tanto com `git clone` quanto com `git remote add`. A configuração específica de cada plataforma para tokens e chaves SSH é abordada no [Capítulo 4: Integração com plataformas](../04-platform-integration/01-integration-fundamentals.md#choose-https-or-ssh); use a forma que já corresponde a como você se autentica na plataforma.

## Inspecionar e gerenciar remotos

```bash
git remote -v
```

Lista cada remoto configurado e sua URL de fetch e push. Um repositório recém-clonado mostra `origin`; adicione outro com `git remote add <name> <url>`, ou altere um existente com `git remote set-url <name> <url>` (por exemplo, trocando o `origin` de HTTPS para SSH sem clonar de novo).

## Armadilhas comuns

- **Executar `git clone` em um diretório que já existe.** O Git recusa clonar em um diretório não vazio, então `git clone <url>` dentro de uma pasta de projeto existente falha; clone em um novo diretório ou informe um nome de diretório de destino como segundo argumento.
- **Executar `git init` dentro de um repositório já clonado.** Isso reinicializa o `.git/` no lugar — normalmente inofensivo (histórico e configuração existentes são preservados) — mas raramente é o que você pretendia fazer; verifique `git status` ou procure por um `.git/` existente antes, se não tiver certeza se a pasta já é um repositório.
- **Assumir que um clone sempre usa `origin`.** `origin` é apenas o nome convencional que o Git atribui automaticamente; um repositório pode ter zero, um ou vários remotos com quaisquer nomes.

## Exercício

Crie um diretório vazio, execute `git init` dentro dele e depois `git remote -v`, confirmando que nada é exibido (nenhum remoto configurado ainda). Em outro diretório, clone qualquer repositório público via HTTPS e execute `git remote -v` novamente, confirmando que `origin` agora aparece com uma URL de fetch e uma de push.

## Referências

Estas são as fontes oficiais consultadas para esta página:

- Manual de referência do Git — [git-init](https://git-scm.com/docs/git-init)
- Manual de referência do Git — [git-clone](https://git-scm.com/docs/git-clone)
- Pro Git (2ª edição) — [Obtendo um Repositório Git](https://git-scm.com/book/pt-br/v2/Fundamentos-do-Git-Obtendo-um-Reposit%c3%b3rio-Git)
