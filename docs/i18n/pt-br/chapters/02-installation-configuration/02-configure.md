# 2.2 Configurar identidade e padrões

Defina o nome e o e-mail que o Git registrará nos novos commits:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

`user.name` e `user.email` ficam gravados em cada commit que você faz e não podem ser alterados retroativamente sem reescrever o histórico, então defina-os antes do seu primeiro commit. `init.defaultBranch` afeta apenas os repositórios criados depois, com `git init`; ele não renomeia branches em repositórios que você já tem.

Consulte a configuração efetiva, e de qual arquivo cada valor veio, com:

```bash
git config --list --show-origin
```

## Níveis de escopo da configuração

O Git lê a configuração de vários arquivos e os combina, com um escopo mais específico sobrepondo um menos específico. Do menor para o maior nível de precedência:

| Escopo | Flag | Aplica-se a | Local típico |
| --- | --- | --- | --- |
| Sistema | `--system` | Todos os usuários da máquina | `/etc/gitconfig` (Linux/macOS); `C:\ProgramData\Git\config` (Windows) |
| Global | `--global` | O usuário atual, em todos os repositórios | `~/.gitconfig` ou `$XDG_CONFIG_HOME/git/config` (Linux/macOS); `%USERPROFILE%\.gitconfig` (Windows) |
| Local | `--local` (padrão) | Somente o repositório atual | `.git/config` dentro do repositório |
| Worktree | `--worktree` | Um worktree de um repositório com múltiplos worktrees | `.git/config.worktree` (usado apenas quando `extensions.worktreeConfig` está habilitado) |

Local sobrepõe global, que sobrepõe sistema; worktree, quando habilitado, sobrepõe os três. Executar `git config` sem uma flag de escopo grava em `--local`, então execute-o de dentro de um repositório apenas quando quiser definir um valor só para aquele repositório. Veja a [referência do `git-config`](https://git-scm.com/docs/git-config#FILES) para as regras completas de descoberta de arquivos, incluindo como o `$XDG_CONFIG_HOME` é resolvido.

## Configuração do editor

O Git abre um editor externo para mensagens de commit, rebase interativo e tarefas semelhantes, controlado por `core.editor`. Este curso detalha a configuração de editor e ferramenta de merge em [Configuração de editor e ferramenta de merge](../05-ide-integration/07-editor-and-mergetool-config.md); um exemplo mínimo:

```bash
git config --global core.editor "code --wait"
```

## Armadilhas comuns

- **Esquecer o `user.email`.** Sem ele, o Git recusa o commit ou usa um endereço adivinhado a partir do seu usuário e nome de máquina, gerando commits atribuídos à pessoa errada — um problema especialmente em máquinas compartilhadas ou de CI. Confirme com `git config --get user.email` antes do primeiro commit em um ambiente novo.
- **Definir a identidade apenas globalmente em uma máquina compartilhada.** Se várias pessoas ou papéis usam a mesma conta (por exemplo, um runner de CI), defina `user.name`/`user.email` com `--local` por repositório, em vez de depender de uma única identidade global.
- **Confundir a precedência dos escopos.** Um valor definido com `--local` sempre prevalece sobre a mesma chave definida com `--global`, mesmo que o valor global tenha sido definido mais recentemente. Use `git config --list --show-origin` quando uma configuração parecer não fazer efeito.

## Exercício

Execute `git config --global user.name "Your Name"`, `git config --global user.email "you@example.com"` e `git config --global init.defaultBranch main`. Depois execute `git config --list --show-origin` e confirme que os três valores aparecem com seu arquivo de configuração global como origem.

## Referências

Estas são as fontes oficiais consultadas para esta página:

- Manual de referência do Git — [git-config](https://git-scm.com/docs/git-config)
- Pro Git (2ª edição) — [Configuração inicial do Git](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-Configura%c3%a7%c3%a3o-inicial-do-Git)
- Pro Git (2ª edição) — [Configuração do Git](https://git-scm.com/book/pt-br/v2/Customizando-o-Git-Configura%c3%a7%c3%a3o-do-Git)
