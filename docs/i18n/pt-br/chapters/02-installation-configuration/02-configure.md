# 2.2 Configurar identidade e padrões

Defina o nome e o e-mail que o Git registrará nos novos commits:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

Consulte a configuração efetiva com `git config --list --show-origin`.
