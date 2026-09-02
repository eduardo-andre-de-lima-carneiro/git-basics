# Git Básico

> Aprenda Git entendendo o que ele é, praticando o que ele faz e ganhando confiança um pequeno passo de cada vez.

Git Básico é um curso prático e guiado para quem está começando a usar Git, está migrando do Subversion ou procura um modelo mental mais claro para o controle de versão no dia a dia.

[Comece o curso](menu.md) | [Trilha de aprendizagem](learning-path.md) | [Escolha seu idioma](#idiomas) | [Contribua](../../../CONTRIBUTING.md)

## Por que este curso existe

A documentação do Git pode ser tecnicamente precisa e ainda assim parecer difícil de começar. Este projeto transforma as ideias essenciais em um caminho guiado: explicações curtas, comandos reais, resultados visíveis e exercícios que podem ser praticados em um repositório temporário.

O objetivo não é decorar uma lista de comandos. É entender o estado do seu projeto, fazer mudanças intencionais e se recuperar com tranquilidade quando algo der errado.

## O que você vai aprender

- Como o controle de versão protege e explica o histórico de um projeto.
- Como a árvore de trabalho, a área de preparação, os commits, as branches e os remotos do Git se relacionam.
- Como instalar e configurar o Git para projetos pessoais ou de equipe.
- Como inspecionar as mudanças antes de criar um commit.
- Como criar branches, sincronizar com repositórios remotos e colaborar com segurança.
- Como escolher o comando de recuperação adequado para uma mudança indesejada.

## Mapa do curso

| Capítulo                                                                         | Foco                                                   | Você vai praticar                                                       |
| -------------------------------------------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------------------------- |
| [1. Conceitos básicos](chapters/01-basic-concepts/README.md)                     | As ideias por trás do controle de versão e do Git      | Pensar em snapshots, histórico e estados do projeto                     |
| [2. Instalação e configuração](chapters/02-installation-configuration/README.md) | Preparar o Git para uso                                | Verificar a instalação, a identidade, os padrões e os repositórios      |
| [3. Comandos e operações](chapters/03-commands-operations/README.md)             | Construir um fluxo de trabalho diário confiável        | Commits, branches, remotos, merges, exercícios e recuperação            |
| [4. Integração com plataformas](chapters/04-platform-integration/README.md)      | Conectar o Git a plataformas de colaboração hospedadas | Pull requests, merge requests, permissões, automação e entregas seguras |

## Uma primeira prática rápida

Depois de instalar o Git, crie um repositório descartável para praticar:

```bash
mkdir git-practice
cd git-practice
git init
printf "My first Git file\n" > notes.txt
git add notes.txt
git commit -m "Add first practice file"
git log --oneline
```

Você acabou de criar um repositório, preparar uma mudança, registrar um commit e inspecionar seu histórico. O Capítulo 1 explica o que aconteceu em cada etapa.

## Como usar a documentação

1. Comece pelo [menu da documentação](menu.md).
2. Leia o Capítulo 1 antes de mergulhar na memorização de comandos.
3. Siga as etapas de configuração do Capítulo 2.
4. Pratique o Capítulo 3 em um repositório descartável.
5. Explore o Capítulo 4 para conhecer a plataforma usada pela sua equipe.
6. Consulte o [glossário](glossary.md) sempre que um termo não for familiar.

Cada lição é um arquivo Markdown independente, conectado por links relativos para que possa ser lida diretamente no GitHub.

## Idiomas

O curso está disponível em quatro idiomas:

- [English](../../../README.md)
- [Français](../fr/README.md)
- [Português (Brasil)](README.md)
- [Español](../es/README.md)

## Valores do projeto

- **Prático:** os exemplos devem levar a algo que o aprendiz possa observar.
- **Acessível:** explique a ideia antes de apresentar o comando.
- **Seguro:** use repositórios descartáveis e deixe claras as operações destrutivas.
- **Aberto:** mantenha a documentação gratuita, reutilizável e fácil de aprimorar.

## Contribuição

Encontrou uma explicação confusa, um exercício faltando ou um link quebrado? Leia o [guia de contribuição](../../../CONTRIBUTING.md) e ajude a tornar melhor a primeira experiência de outra pessoa com Git.

## Origem

Este curso nasceu de uma experiência em DevSecOps, apoiando equipes que estavam migrando do Subversion para o Git. A documentação oficial e os sites de referência eram úteis, mas algumas pessoas precisavam de um caminho mais guiado e prático para entrar no assunto. O Git Básico foi criado para oferecer esse caminho e facilitar o compartilhamento do aprendizado.

O projeto é intencionalmente colaborativo. Comentários, correções, exemplos e traduções são bem-vindos.
