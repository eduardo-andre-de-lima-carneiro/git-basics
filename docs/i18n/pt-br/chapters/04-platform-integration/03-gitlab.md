# 4.3 GitLab

O GitLab oferece repositórios Git com merge requests, Issues, pipelines de CI/CD, Package Registry e painéis de segurança em uma única plataforma.

## Conecte e publique

Crie um projeto no GitLab e, depois, execute localmente:

```bash
git remote add origin https://gitlab.com/GROUP/PROJECT.git
git push -u origin main
```

Use os nomes reais do seu grupo, projeto e branch padrão. Revise o remoto com `git remote -v` antes de fazer push.

## Integrações úteis

- Merge requests reúnem revisão, aprovações, discussões e resultados dos pipelines.
- `.gitlab-ci.yml` define jobs de CI/CD, estágios, artefatos e regras de deploy.
- Branches e ambientes protegidos controlam quem pode fazer merge ou deploy.
- Deploy tokens, project access tokens e runners dão suporte à automação.
- Webhooks e integrações notificam rastreadores de issues, ferramentas de chat e sistemas de segurança.

Use variáveis de CI/CD mascaradas e protegidas para credenciais. Mantenha os runners atualizados, restrinja runners privilegiados e conceda aos tokens apenas os escopos necessários para seus jobs.
