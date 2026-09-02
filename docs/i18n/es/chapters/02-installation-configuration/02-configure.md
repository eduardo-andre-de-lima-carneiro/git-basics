# 2.2 Configurar la identidad y los valores predeterminados

Define el nombre y el correo electrónico que Git registra en los commits nuevos:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

Revisa la configuración efectiva con `git config --list --show-origin`.
