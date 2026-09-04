# 2.1 Instalar o Git

Recomenda-se o Git 2.23 ou mais recente para os exemplos de `git switch` e `git restore` usados adiante. Versões mais antigas podem exigir comandos equivalentes, como `git checkout`. Instale o Git usando o gerenciador de pacotes ou instalador recomendado para o seu sistema operacional, listados abaixo, ou explore todas as opções na [página oficial de downloads](https://git-scm.com/downloads).

## Windows

Instale com o [winget](https://learn.microsoft.com/pt-br/windows/package-manager/winget/install), que já vem com o Windows 10/11 moderno:

```bash
winget install --id Git.Git -e --source winget
```

Alternativamente, baixe o instalador em [git-scm.com/downloads/win](https://git-scm.com/downloads/win). Durante a instalação, mantenha a opção padrão "Git from the command line and also from 3rd-party software" para que o `git` seja adicionado ao `PATH`; caso contrário, comandos posteriores deste curso falharão com "command not found" em um terminal recém-aberto.

## macOS

Se você usa o [Homebrew](https://docs.brew.sh/Installation), instale com:

```bash
brew install git
```

O macOS também oferece o Git através das Xcode Command Line Tools:

```bash
xcode-select --install
```

As command line tools instalam um Git funcional, mas geralmente mais antigo que o do Homebrew. Se precisar de uma versão recente específica, prefira o Homebrew e execute `brew upgrade git` periodicamente.

## Linux

Use o gerenciador de pacotes da sua distribuição. No Debian e no Ubuntu:

```bash
sudo apt install git
```

No Fedora e em outras distribuições baseadas em `dnf`:

```bash
sudo dnf install git
```

Os repositórios das distribuições podem ficar meses atrás do lançamento mais recente do Git. Se precisar de uma versão mais nova no Ubuntu, adicione o [PPA git-core](https://git-scm.com/downloads/linux) antes de instalar; no Fedora, o `dnf` geralmente acompanha o upstream de perto o suficiente para que isso raramente seja necessário.

## Verificar a instalação

```bash
git --version
```

A versão exata pode variar. O comando deve mostrar uma versão, e não um erro. Se aparecer "command not found" logo após uma instalação no Windows, reabra o terminal (ou reinicie) para que o `PATH` atualizado tenha efeito.

## Depois de instalar

Um Git recém-instalado não tem identidade nem nome de branch padrão configurados. Antes de fazer seu primeiro commit, configure-os conforme descrito em [Configurar identidade e padrões](02-configure.md) — um `user.email` não configurado gera commits atribuídos a um endereço genérico em vez de você.

## Armadilhas comuns

- **Instalar a partir de uma fonte não oficial.** Use apenas os gerenciadores de pacotes e o instalador acima, ou a [página oficial de downloads](https://git-scm.com/downloads); pacotes "instalador do Git" não oficiais encontrados em buscas podem estar desatualizados ou ser inseguros.
- **Múltiplas instalações do Git.** Instalar o Git por mais de um método (por exemplo, Xcode tools e Homebrew) pode deixar um `git` mais antigo antes no `PATH`. Execute `which git` (macOS/Linux) ou `where git` (Windows) para confirmar qual binário realmente é executado.
- **Pular a verificação de versão.** Sempre execute `git --version` logo após instalar — é a forma mais simples de confirmar que a instalação funcionou antes de investigar qualquer outro problema.

## Exercício

Instale o Git para o seu sistema operacional usando o método acima e execute `git --version`, confirmando que a versão relatada é 2.23 ou mais recente. Se for uma versão mais antiga, atualize usando o mesmo gerenciador de pacotes (`brew upgrade git`, `sudo apt update && sudo apt upgrade git` ou `winget upgrade --id Git.Git`).

## Referências

Estas são as fontes oficiais consultadas para esta página:

- Git — [Downloads](https://git-scm.com/downloads)
- Pro Git (2ª edição) — [Instalando o Git](https://git-scm.com/book/pt-br/v2/Primeiros-Passos-Instalando-o-Git)
- Homebrew — [Installation](https://docs.brew.sh/Installation)
- Microsoft Learn — [Instalar o winget](https://learn.microsoft.com/pt-br/windows/package-manager/winget/install)
