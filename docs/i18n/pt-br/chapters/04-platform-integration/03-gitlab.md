# 4.3 GitLab

O GitLab oferece repositórios Git com merge requests, Issues, pipelines de CI/CD, Package Registry e painéis de segurança em uma única plataforma.

## Conecte e publique

Crie um projeto no GitLab e, depois, execute localmente:

```bash
git remote add origin https://gitlab.com/GROUP/PROJECT.git
git push -u origin main
```

Use os nomes reais do seu grupo, projeto e branch padrão. Revise o remoto com `git remote -v` antes de fazer push.

## Autenticação

Para HTTPS, o GitLab aceita [qualquer string não vazia como usuário e um personal access token como senha](https://docs.gitlab.com/user/profile/personal_access_tokens/). Um token é *obrigatório*, não opcional, assim que a autenticação de dois fatores ou SSO é habilitada na conta. Novos tokens precisam ter uma data de expiração; o GitLab aplica um padrão de 365 dias se você não definir uma, e administradores no plano Ultimate podem impor um limite máximo menor.

Para quem trabalha com frequência pela linha de comando, uma [chave SSH](https://docs.gitlab.com/user/ssh/) evita reinserir um token a cada push. O GitLab recomenda o tipo de chave Ed25519 em vez de RSA: `ssh-keygen -t ed25519 -C "<comment>"`. Chaves recém-adicionadas são verificadas contra uma lista de chaves conhecidas como comprometidas antes de o GitLab aceitá-las.

O GitLab também oferece suporte a [autenticação de dois fatores](https://docs.gitlab.com/user/profile/account/two_factor_authentication/) — passkeys, apps OTP, chaves de segurança WebAuthn ou códigos por e-mail — que um grupo ou uma instância autogerenciada pode exigir de todos os membros.

## Integrações úteis

- Merge requests reúnem revisão, aprovações, discussões e resultados dos pipelines.
- `.gitlab-ci.yml` define jobs de CI/CD, estágios, artefatos e regras de deploy.
- [Branches protegidas](https://docs.gitlab.com/user/project/repository/branches/protected/) e ambientes controlam quem pode fazer merge ou deploy.
- Deploy tokens, project access tokens e runners dão suporte à automação.
- Webhooks e integrações notificam rastreadores de issues, ferramentas de chat e sistemas de segurança.

Use variáveis de CI/CD mascaradas e protegidas para credenciais. Mantenha os runners atualizados, restrinja runners privilegiados e conceda aos tokens apenas os escopos necessários para seus jobs.

## Armadilhas comuns

- Esquecer que o GitLab aplica silenciosamente uma expiração de 365 dias a um personal access token criado sem uma — um token que parece ter "sem expiração" vai parar de funcionar um ano depois mesmo assim.
- Registrar uma chave de segurança WebAuthn em um hostname do GitLab (por exemplo, uma instância autogerenciada) e esperar que ela também funcione no `gitlab.com` — os registros WebAuthn são vinculados ao hostname, então cada um precisa do seu próprio registro.
- Fazer commits sem nunca configurar a assinatura de commits e depois se surpreender que o selo "verificado" de uma branch protegida nunca aparece; o GitLab verifica a assinatura contra uma chave já adicionada à conta.

## Exercício

Gere uma chave SSH Ed25519, adicione a chave pública à sua conta do GitLab e, depois, clone um projeto via SSH e confirme que o `git push` não pede mais um token.

## Referências

- GitLab Docs — [Personal access tokens](https://docs.gitlab.com/user/profile/personal_access_tokens/)
- GitLab Docs — [Chaves SSH](https://docs.gitlab.com/user/ssh/)
- GitLab Docs — [Autenticação de dois fatores](https://docs.gitlab.com/user/profile/account/two_factor_authentication/)
- GitLab Docs — [Branches protegidas](https://docs.gitlab.com/user/project/repository/branches/protected/)
- GitLab Docs — [Commits assinados](https://docs.gitlab.com/user/project/repository/signed_commits/)
