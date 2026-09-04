# 4.1 Fundamentos da integração

As plataformas hospedadas acrescentam serviços de colaboração e entrega ao redor de um repositório Git. Os comandos locais continuam familiares; a plataforma fornece identidade, permissões, revisão, automação e visibilidade do projeto.

## O fluxo comum

1. Crie ou selecione um repositório remoto.
2. Conecte o repositório local com [`git remote add origin <repository-url>`](https://git-scm.com/docs/git-remote).
3. Envie uma branch com `git push -u origin <branch-name>`.
4. Abra um pull request ou merge request para revisão.
5. Deixe as verificações obrigatórias serem executadas antes do merge.
6. Exclua a branch de curta duração depois que a alteração for integrada.

## Escolha HTTPS ou SSH

HTTPS é simples para começar. Toda plataforma relevante hoje autentica operações Git por HTTPS com um token ou um login federado em vez de uma senha de conta — o GitHub removeu a autenticação por senha para o Git em agosto de 2021, e as demais plataformas deste capítulo seguiram o mesmo padrão, cada uma com seu mecanismo atual (veja as páginas de cada plataforma a seguir). SSH usa um par de chaves, evita reinserir credenciais a cada operação e também pode assinar commits. Nunca coloque tokens, chaves privadas ou credenciais em um repositório, e não presuma que uma página lida há algum tempo ainda descreve o padrão de hoje — essas plataformas mudam seus padrões de autenticação com mais frequência do que a maioria dos comandos do Git muda.

## Comparação entre plataformas

A tabela reflete a documentação de cada plataforma, verificada ao vivo em vez de recordada de memória. Limites numéricos (assentos, armazenamento, minutos de CI) mudam com frequência e foram deixados de fora de propósito — consulte a página de preços atual de cada plataforma para isso.

| Plataforma | Modelo de hospedagem | Autenticação padrão para Git via HTTPS | Nome da unidade de revisão | Repositórios privados no plano gratuito |
| --- | --- | --- | --- | --- |
| [GitHub](https://docs.github.com/pt) | SaaS (GitHub.com) ou autogerenciado (GitHub Enterprise Server) | Personal access token, chave SSH ou um helper de credenciais como GitHub CLI / Git Credential Manager — senhas de conta são rejeitadas | Pull request | Sim |
| [GitLab](https://docs.gitlab.com/) | SaaS (GitLab.com) ou autogerenciado (GitLab Self-Managed) | Personal access token (obrigatório quando 2FA ou SSO está habilitado) ou chave SSH | Merge request | Sim |
| [Azure Repos](https://learn.microsoft.com/pt-br/azure/devops/repos/) | SaaS (Azure DevOps Services) ou autogerenciado (Azure DevOps Server) | Login com Microsoft Entra ID via Git Credential Manager, preferido em vez de um personal access token com escopo limitado | Pull request | Sim |
| [Bitbucket](https://support.atlassian.com/bitbucket-cloud/) | SaaS (Bitbucket Cloud) ou autogerenciado (Bitbucket Data Center) | API token ou chave SSH — app passwords foram totalmente descontinuados em 2026 | Pull request | Sim |

## O que configurar

No mínimo, defina a branch padrão, as regras de proteção de branches, os requisitos de revisão, as verificações de status, o vínculo com issues e quem pode fazer push ou merge. Essas políticas fazem parte do processo de entrega da equipe, e não são apenas elementos decorativos da plataforma.

## Armadilhas comuns

- Reutilizar um único token de longa duração e com escopo amplo em todas as ferramentas. Se ele vazar, todas as integrações que o usavam ficam comprometidas de uma vez — dê a cada token um escopo para um único propósito.
- Esquecer que um token tem data de expiração. Um push que funcionou ontem pode falhar hoje com um erro de autenticação assim que o token expira — trate isso como algo rotineiro, não como um bug, e rotacione o token.
- Presumir que o HTTPS ainda pede uma senha de conta. Nenhuma das quatro plataformas deste capítulo faz isso; o prompt pede um token ou um login gerenciado por CLI.

## Referências

- Manual de referência do Git — [git-remote](https://git-scm.com/docs/git-remote)
- GitHub Docs — [Sobre a autenticação no GitHub](https://docs.github.com/pt/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)
- GitLab Docs — [Personal access tokens](https://docs.gitlab.com/user/profile/personal_access_tokens/)
- Microsoft Learn — [Usar personal access tokens para autenticação](https://learn.microsoft.com/pt-br/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate)
- Atlassian Support — [App passwords (Bitbucket Cloud)](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)
