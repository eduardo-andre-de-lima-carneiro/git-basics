# 5.3 Visual Studio

O Visual Studio (a IDE completa do Windows, não o VS Code) tem suporte a Git embutido pelo menu **Git** e por duas janelas acopladas.

## Fluxo principal

- **Git > Clone Repository** ou **Create Git Repository** inicia um repositório, oferecendo modelos de `.gitignore` e de licença.
- A janela **Git Changes** mostra as mudanças não preparadas e preparadas, a caixa de mensagem de commit e os botões **Commit** / **Commit and Push**.
- A janela **Git Repository** mostra o grafo de branches, os commits de entrada e de saída, e permite fetch, pull, push, merge, rebase e gerenciamento de branches.
- O seletor de branch na barra de status troca e cria branches.
- Conflitos de merge abrem no **Merge Editor**, com caixas de seleção para aceitar a mudança de entrada, a atual ou ambas.

## Autenticação

O Visual Studio usa o **Git Credential Manager**, instalado junto com ele, para guardar os tokens das plataformas no Windows Credential Store. Faça login em **Git > Settings** ou pelo seletor de conta; evite colocar credenciais em URLs de remotos.

## Nota sobre o Team Explorer

Versões antigas roteavam o Git pelo **Team Explorer**. As versões atuais usam o menu Git dedicado e as janelas descritas acima; é essa a experiência mais recente que vale aprender.

## Exercício

Em um repositório de prática aberto no Visual Studio, faça uma mudança, prepare-a em **Git Changes**, confirme o commit e abra a janela **Git Repository** para verificar que o novo commit aparece no grafo.
