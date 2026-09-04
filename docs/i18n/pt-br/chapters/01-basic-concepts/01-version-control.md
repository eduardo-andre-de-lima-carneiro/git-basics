# 1.1 Sistemas de controle de versão

O controle de versão registra as alterações feitas nos arquivos ao longo do tempo. Ele permite que uma equipe compare revisões, identifique autores, restaure estados anteriores e trabalhe em alterações separadas sem sobrescrever o trabalho de outras pessoas.

## O problema que ele resolve

Sem controle de versão, nomes como `project-final-final-2` acabam se tornando o histórico. O Git mantém esse histórico em um repositório estruturado.

## Três gerações de controle de versão

Os sistemas de controle de versão se dividem em três categorias amplas, descritas na [visão geral sobre controle de versão](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-Sobre-Controle-de-Vers%C3%A3o) do livro Pro Git:

- **VCS local** (ex.: RCS) mantém um banco de patches em uma única máquina. Não há colaboração, e nenhuma proteção caso essa máquina se perca.
- **VCS centralizado** (ex.: CVS, Subversion) armazena todo o histórico em um servidor; os clientes fazem checkout de cópias de trabalho. A colaboração funciona, mas o servidor é um ponto único de falha — se ele cair, ou seu banco de dados corromper sem backup, o histórico do projeto pode ser perdido.
- **VCS distribuído** (ex.: Git, Mercurial) dá a cada clone o histórico completo. Qualquer clone pode restaurar o projeto se um servidor for perdido, e a maioria das operações do dia a dia não precisa da rede.

## Armadilhas comuns

- **Controle de versão não é um serviço de backup.** Um backup copia arquivos; o controle de versão também registra *por que* algo mudou e permite comparar, identificar o autor (blame) e reverter alterações individuais.
- **Um repositório não é o mesmo que uma única cópia com checkout feito.** Apagar sua cópia de trabalho não apaga o histórico que já está commitado e armazenado com segurança em outro lugar (localmente ou em um remoto).

## Prática

Crie um pequeno arquivo de texto, altere-o duas vezes e anote o que você precisaria saber para recuperar a primeira versão. Essa lista representa o valor oferecido pelo controle de versão.

## Referências

Esta página se baseia nas seguintes fontes oficiais:

- Pro Git (2ª ed.) — [Sobre Controle de Versão](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-Sobre-Controle-de-Vers%C3%A3o)
- Manual de referência do Git — [git-scm.com/docs](https://git-scm.com/docs)
