# 1.2 Por que Git

O Git é distribuído: cada clone contém o histórico do projeto necessário para a maioria das operações locais. Isso torna commits, comparações e criação de branches rápidos e disponíveis offline.

O Git também oferece pontos de verificação explícitos chamados commits. Um bom commit responde: o que mudou e por quê?

## De onde o Git veio

O Git foi criado em 2005 por Linus Torvalds e pela comunidade do kernel Linux, depois que a ferramenta proprietária usada pelo projeto do kernel, o BitKeeper, deixou de estar disponível gratuitamente. Os objetivos de design eram velocidade, um design simples, forte suporte a desenvolvimento não linear (branches), ser totalmente distribuído e conseguir lidar com projetos grandes, como o próprio kernel Linux, com eficiência. Veja a [breve história do Git](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-Uma-Breve-Hist%C3%B3ria-do-Git) no livro Pro Git para a história completa.

## Instantâneos, não diffs

Diferente de sistemas que armazenam uma lista de alterações por arquivo, o Git armazena um instantâneo (snapshot) de todo o projeto a cada commit; um arquivo que não mudou é simplesmente ligado à versão idêntica anterior, em vez de ser duplicado. Todo objeto recebe um checksum antes de ser armazenado — historicamente com SHA-1, com SHA-256 disponível como opção mais recente através da [transição de função hash](https://git-scm.com/docs/hash-function-transition) do Git — de modo que corrupção silenciosa ou adulteração seja detectável. Veja [What is Git?](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-O-que-%C3%A9-Git%3F) no livro Pro Git.

## Git vs. Subversion vs. Mercurial

| | Git | Subversion (SVN) | Mercurial |
|---|---|---|---|
| Modelo | [Distribuído](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-Sobre-Controle-de-Vers%C3%A3o) | [Centralizado](https://subversion.apache.org/) | [Distribuído](https://www.mercurial-scm.org/) |
| Custo de branching | Uma branch é um ponteiro móvel para um commit — [quase instantâneo de criar](https://git-scm.com/book/pt-br/v2/Ramifica%C3%A7%C3%A3o-Branching-no-Git-Branches-em-Poucas-Palavras) | Uma [cópia barata no lado do servidor](https://svnbook.red-bean.com/en/1.7/svn.branchmerge.using.html), mas criá-la e usá-la ainda exige o servidor central | Barato; branches e bookmarks vivem no clone local |
| Capacidade offline | Total — commit, diff, log e branch funcionam sem rede | Limitada — a maioria das operações precisa contatar o servidor | Total — "cada clone contém todo o histórico do projeto" |
| Uso típico hoje | Escolha padrão para a maioria dos projetos novos; usado por [96% dos desenvolvedores profissionais](https://git-scm.com/about) (pesquisa Stack Overflow de 2022) | Ainda encontrado em algumas empresas que querem controle de acesso centralizado sobre o histórico | Nicho; principalmente implantações legadas, amplamente superado pelo Git |

## Armadilhas comuns

- **Um commit não é um diff.** O Git registra o instantâneo completo que estava na staging area no momento do commit, não apenas o que mudou — é isso que torna o checkout de um commit antigo uma operação direta na árvore de arquivos, em vez de reaplicar uma cadeia de patches. Veja [Gravando Alterações no Repositório](https://git-scm.com/book/pt-br/v2/Fundamentos-do-Git-Gravando-Altera%C3%A7%C3%B5es-no-Reposit%C3%B3rio).

## Ideia principal

O Git não é apenas um sistema de backup de arquivos. Ele é uma ferramenta para construir, inspecionar e compartilhar uma linha do tempo de alterações intencionais.

## Referências

Esta página se baseia nas seguintes fontes oficiais:

- Pro Git (2ª ed.) — [Uma Breve História do Git](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-Uma-Breve-Hist%C3%B3ria-do-Git)
- Pro Git (2ª ed.) — [What is Git?](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-O-que-%C3%A9-Git%3F)
- Manual de referência do Git — [Transição de função hash do Git](https://git-scm.com/docs/hash-function-transition)
- git-scm.com — [About Git](https://git-scm.com/about)
- Apache Subversion — [subversion.apache.org](https://subversion.apache.org/)
- Mercurial — [mercurial-scm.org](https://www.mercurial-scm.org/)
