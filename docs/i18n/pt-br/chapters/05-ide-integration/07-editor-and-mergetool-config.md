# 5.7 Configuração de editor e ferramenta de merge

O Git usa três configurações para entregar trabalho a um programa externo: `core.editor` para texto, `merge.tool` para resolução de conflitos e `diff.tool` para visualizar mudanças.

## Definir o editor de commit

```bash
git config --global core.editor "code --wait"     # VS Code
git config --global core.editor "codium --wait"   # VSCodium
```

Para uma IDE da JetBrains, use o lançador de linha de comando dela, por exemplo `git config --global core.editor "idea --wait"` depois que o lançador estiver instalado.

## Configurar uma ferramenta de merge

```bash
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait --merge $REMOTE $LOCAL $BASE $MERGED'
git config --global mergetool.keepBackup false
```

Quando ocorrer um conflito, execute:

```bash
git mergetool
```

O Git abre a ferramenta configurada para cada arquivo em conflito. Depois de salvar e fechar, marque o resultado com `git add` e continue o merge ou o rebase.

## Configurar uma ferramenta de diff

```bash
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'
git difftool HEAD~1 HEAD
```

O Visual Studio e as IDEs da JetBrains também se registram como ferramentas de merge e de diff durante a instalação na maioria das plataformas; consulte a documentação delas para o nome exato de `merge.tool`.

## Exercício

Configure `merge.tool`, crie um conflito em um repositório de prática editando a mesma linha em duas branches, execute `git mergetool`, resolva-o no editor e finalize com `git commit`.
