# 3.1 O fluxo de trabalho diário

Use um ciclo pequeno e observável:

```bash
git status
git add path/to/file
git diff --staged
git commit -m "Describe the change"
git status
```

Revise a diferença preparada antes de fazer o commit. Esse hábito impede que arquivos não relacionados entrem em um commit.
