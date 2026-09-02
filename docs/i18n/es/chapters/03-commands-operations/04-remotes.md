# 3.4 Remotos y sincronización

Sincroniza de forma explícita:

```bash
git fetch origin
git log --oneline main..origin/main
git push -u origin feature/example
```

Haz fetch primero cuando necesites entender qué cambió en el remoto. Publica únicamente commits que hayas revisado.
