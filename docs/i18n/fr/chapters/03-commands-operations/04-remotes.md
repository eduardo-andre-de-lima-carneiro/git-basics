# 3.4 Dépôts distants et synchronisation

Synchronisez explicitement :

```bash
git fetch origin
git log --oneline main..origin/main
git push -u origin feature/example
```

Récupérez d'abord les changements lorsque vous devez comprendre ce qui a changé à distance. Ne publiez que les commits que vous avez examinés.
