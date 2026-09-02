# 3.4 Remotos e sincronização

Sincronize de forma explícita:

```bash
git fetch origin
git log --oneline main..origin/main
git push -u origin feature/example
```

Faça o fetch primeiro quando precisar entender o que mudou remotamente. Envie apenas commits que você revisou.
