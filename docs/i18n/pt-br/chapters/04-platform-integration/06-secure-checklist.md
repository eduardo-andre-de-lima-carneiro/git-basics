# 4.6 Checklist de integração segura

Antes de considerar uma integração pronta, verifique o seguinte:

- A URL remota está correta e não contém um secret.
- A autenticação usa chaves SSH, tokens ou uma identidade de aplicação com escopo limitado — nunca uma senha de conta; todas as plataformas deste capítulo removeram ou estão removendo a autenticação por senha para Git via HTTPS.
- A autenticação de dois fatores ou multifator está habilitada em toda conta humana com acesso de push ou merge, não apenas em contas de administrador.
- Personal access tokens têm o escopo mais restrito que a tarefa exige, uma expiração curta e um plano de rotação — um token que "simplesmente funciona para sempre" é um token que ninguém está monitorando.
- Chaves SSH usam um algoritmo moderno (Ed25519 quando a plataforma aceita; o Azure Repos é a exceção e exige RSA) e são rotacionadas ou removidas quando uma pessoa muda de função ou sai da equipe.
- A branch padrão está protegida contra pushes diretos acidentais.
- Pull requests ou merge requests exigem revisão apropriada e verificações automatizadas aprovadas.
- A assinatura de commits (GPG, SSH ou o método suportado pela plataforma) está habilitada onde a equipe quer um selo verificado como prova de autoria, entendendo que nem toda plataforma aplica isso da mesma forma — GitHub e GitLab podem exigir commits assinados como uma política de branch, enquanto o Azure Repos atualmente não tem um equivalente nessa política de branch.
- Os secrets de CI/CD estão armazenados no gerenciador de secrets da plataforma, nunca em um arquivo de workflow ou em um script.
- A análise de dependências, secrets e vulnerabilidades está habilitada quando apropriado.
- O deploy em produção exige uma aprovação separada ou um ambiente protegido.
- Os webhooks validam suas assinaturas e enviam somente os dados necessários.
- Os acessos são revisados quando uma pessoa, token, runner ou serviço muda de função — e imediatamente quando alguém sai.

## Proteções no nível da conta

Cada plataforma documenta seu próprio requisito e configuração atuais:

- O GitHub [exige 2FA](https://docs.github.com/pt/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication) para contas que contribuem com código, e oferece suporte à [assinatura de commits com GPG, SSH ou S/MIME](https://docs.github.com/pt/authentication/managing-commit-signature-verification/about-commit-signature-verification).
- O GitLab oferece suporte a [2FA imposto por grupo ou por instância](https://docs.gitlab.com/user/profile/account/two_factor_authentication/) e a [commits assinados via SSH, GPG ou X.509](https://docs.gitlab.com/user/project/repository/signed_commits/).
- O Azure DevOps vincula a autenticação multifator ao provedor de identidade da organização: um [login com Microsoft Entra ID herda as políticas de MFA e de Acesso Condicional do Entra](https://learn.microsoft.com/pt-br/azure/devops/organizations/security/about-security-identity), e contas com uma conta Microsoft podem habilitar 2FA diretamente.
- O Bitbucket Cloud oferece suporte à [verificação em duas etapas](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/) por meio de um app autenticador ou uma chave de segurança, independentemente de qual credencial Git (API token ou chave SSH) a conta usa.

## Armadilhas comuns

- Tratar "2FA é exigido para a organização" como equivalente a "2FA está habilitado para todo membro" — uma configuração de imposição e a adesão individual são duas verificações diferentes, e uma pode ficar atrasada em relação à outra.
- Exigir commits assinados no GitHub ou no GitLab, mas nunca mostrar aos colaboradores como configurar a assinatura SSH ou GPG localmente, de forma que a exigência bloqueia pushes legítimos em vez de detectar um problema real.
- Auditar tokens e chaves apenas uma vez, na configuração do projeto, e nunca mais. Rotação é uma tarefa recorrente, não um item de checklist único.

A integração é bem-sucedida quando torna a entrega mais rastreável e repetível sem facilitar o uso indevido de credenciais ou alterações em produção.

## Referências

- GitHub Docs — [Sobre a autenticação de dois fatores](https://docs.github.com/pt/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication)
- GitHub Docs — [Sobre a verificação de assinatura de commit](https://docs.github.com/pt/authentication/managing-commit-signature-verification/about-commit-signature-verification)
- GitLab Docs — [Autenticação de dois fatores](https://docs.gitlab.com/user/profile/account/two_factor_authentication/)
- GitLab Docs — [Commits assinados](https://docs.gitlab.com/user/project/repository/signed_commits/)
- Microsoft Learn — [Sobre autenticação, autorização e políticas de segurança](https://learn.microsoft.com/pt-br/azure/devops/organizations/security/about-security-identity)
- Atlassian Support — [Habilitar a verificação em duas etapas](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/)
