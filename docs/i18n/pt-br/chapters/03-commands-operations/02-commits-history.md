# 3.2 Commits e Histórico

Comandos de inspeção úteis incluem:

```bash
git log --oneline --decorate --graph
git show <commit>
git diff <commit-a> <commit-b>
```

## Lendo a saída

- [`git log --oneline`](https://git-scm.com/docs/git-log) é um atalho para `--pretty=oneline --abbrev-commit`: uma linha por commit, com um hash curto em vez do hash completo de 40 caracteres.
- `--decorate` imprime os nomes de referência — pontas de branch e tags — que apontam para cada commit exibido, para que você veja onde `main`, `HEAD` ou uma tag estão atualmente no grafo.
- `--graph` desenha um grafo em texto à esquerda da saída, mostrando como as branches divergiram e se uniram; é mais útil combinado com `--oneline --decorate`.
- O [`git show <commit>`](https://git-scm.com/docs/git-show) exibe a mensagem de log de um único commit junto com seu diff completo — a forma mais rápida de inspecionar uma mudança sem listar o histórico ao redor dela.
- `git diff <commit-a> <commit-b>` compara dois commits arbitrários diretamente, independentemente da estrutura de branches entre eles.

## Commits focados e mensagens

Prefira commits focados que representem uma única mudança lógica — um commit que mistura uma correção de bug com uma passada de formatação é mais difícil de revisar, reverter ou acompanhar depois com `git log --follow`. O histórico fica mais fácil de navegar quando as mensagens de commit usam uma descrição imperativa e específica ("Corrige checagem de nulo no parser", não "correções").

Uma convenção bastante usada para estruturar essa mensagem é o [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/): um prefixo `type(scope): description` (`fix:`, `feat:`, `docs:`, …) que torna o histórico fácil de escanear com `git log --oneline` e permite que ferramentas gerem changelogs automaticamente. É opcional aqui, mas vale adotar se seu projeto ainda não tem uma convenção de mensagens.

## Armadilhas comuns

- Um hash abreviado vindo de `--oneline` é inequívoco apenas em relação aos objetos que existem atualmente no seu repositório; não o fixe em documentação que deva sobreviver à branch.
- Reescrever a mensagem ou o conteúdo de um commit já enviado a uma branch compartilhada exige um force-push e coordenação com quem já buscou esse commit — veja [3.5 Desfazer alterações com segurança](05-undo.md) antes de fazer isso.

## Exercício

Em um repositório de prática, faça três pequenos commits. Rode `git log --oneline --decorate --graph --all` e identifique os nomes de referência exibidos. Use `git show` no commit do meio para ver apenas o diff dele, depois `git diff` entre o primeiro e o último commit para ver a mudança acumulada.

## Referências

- Manual do Git — [git-log](https://git-scm.com/docs/git-log)
- Manual do Git — [git-show](https://git-scm.com/docs/git-show)
- Manual do Git — [git-diff](https://git-scm.com/docs/git-diff)
- Pro Git (2ª ed.) — [Viewing the Commit History](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)
- [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/)
