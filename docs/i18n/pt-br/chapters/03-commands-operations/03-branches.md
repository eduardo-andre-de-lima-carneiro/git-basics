# 3.3 Branches e colaboração

Branches são nomes móveis que apontam para commits. Crie seu trabalho separado da base compartilhada:

```bash
git switch -c feature/example
git switch main
git merge feature/example
```

Antes de fazer o merge, inspecione o histórico e resolva os conflitos de forma deliberada. Um conflito é um pedido de decisão humana, não uma falha de comando a ser escondida.
