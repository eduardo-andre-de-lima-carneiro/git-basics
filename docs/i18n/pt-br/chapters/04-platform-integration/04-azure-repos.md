# 4.4 Azure Repos

O Azure Repos hospeda repositórios Git dentro de projetos do Azure DevOps e se conecta naturalmente ao Azure Boards, Pipelines, Test Plans e Artifacts.

## Conecte e publique

Crie ou selecione um repositório em um projeto do Azure DevOps e, depois, execute localmente:

```bash
git remote add origin https://dev.azure.com/ORGANIZATION/PROJECT/_git/REPOSITORY
git push -u origin main
```

A URL exata pode ser copiada pela ação Clone do repositório.

## Autenticação

A orientação da própria Microsoft agora coloca os personal access tokens por último, não em primeiro lugar: a [documentação do Azure DevOps](https://learn.microsoft.com/pt-br/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate) diz para "evitar usar PATs quando um método de autenticação mais seguro estiver disponível" e recomenda o login com Microsoft Entra ID (via Git Credential Manager) ou um service principal / managed identity para qualquer coisa automatizada. Se um [personal access token](https://learn.microsoft.com/pt-br/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate) ainda for a opção certa — um script pontual, uma ferramenta que não consegue fazer login via Entra — dê a ele o menor escopo e a expiração mais curta que a tarefa permitir; a cadência de rotação recomendada pela própria Microsoft é de 90 dias para um PAT pessoal e 30 dias para um PAT privilegiado.

O [SSH](https://learn.microsoft.com/pt-br/azure/devops/repos/git/use-ssh-keys-to-authenticate) também é suportado, com uma particularidade específica da plataforma: o Azure Repos aceita apenas chaves **RSA**, não as chaves Ed25519 que o GitHub e o GitLab agora recomendam — reutilizar uma chave Ed25519 existente do GitHub/GitLab aqui falha. Gere uma chave RSA separada para o Azure Repos: `ssh-keygen -t rsa -b 3072`.

## Integrações úteis

- Pull requests oferecem suporte a revisores, [políticas de branch](https://learn.microsoft.com/pt-br/azure/devops/repos/git/branch-policies?view=azure-devops), itens de trabalho vinculados e validação de builds.
- Azure Pipelines pode compilar, testar, analisar e fazer deploy a partir de eventos do repositório.
- Azure Boards vincula commits e pull requests a itens de trabalho para garantir rastreabilidade.
- Políticas de branch podem exigir revisores, builds bem-sucedidos e resolução de comentários — diferente do GitHub ou do GitLab, as políticas de branch do Azure Repos não têm uma opção nativa de "exigir commits assinados".
- Azure Artifacts fornece feeds para pacotes e dependências de build.

Conceda permissões por meio de grupos sempre que possível. Proteja conexões de serviço e grupos de variáveis, e separe a aprovação de deploys em produção dos direitos de contribuição no código.

## Armadilhas comuns

- Gerar uma chave Ed25519 por hábito (porque funcionou no GitHub) e receber uma rejeição confusa do Azure Repos, que aceita apenas chaves RSA para SSH.
- Deixar um personal access token com uma expiração longa padrão para um pipeline de CI em vez de rotacioná-lo — um token sem rotação parado por meses é fácil de um administrador identificar no log de auditoria, mas só se alguém verificar.
- Tratar um PAT como uma credencial de serviço de longo prazo. A Microsoft recomenda explicitamente migrar cargas de trabalho automatizadas para um service principal ou managed identity.

## Exercício

Crie um personal access token com escopo **Code (Read & write)** para um projeto, com expiração de 7 dias. Use-o para autenticar um `git push` via HTTPS e, depois, verifique no log de auditoria da organização o evento `PatCreated` correspondente.

## Referências

- Microsoft Learn — [Usar personal access tokens para autenticação](https://learn.microsoft.com/pt-br/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate)
- Microsoft Learn — [Usar autenticação por chave SSH](https://learn.microsoft.com/pt-br/azure/devops/repos/git/use-ssh-keys-to-authenticate)
- Microsoft Learn — [Definir e gerenciar políticas de branch](https://learn.microsoft.com/pt-br/azure/devops/repos/git/branch-policies?view=azure-devops)
- Microsoft Learn — [Sobre autenticação, autorização e políticas de segurança](https://learn.microsoft.com/pt-br/azure/devops/organizations/security/about-security-identity)
