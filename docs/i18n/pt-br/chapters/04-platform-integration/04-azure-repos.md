# 4.4 Azure Repos

O Azure Repos hospeda repositórios Git dentro de projetos do Azure DevOps e se conecta naturalmente ao Azure Boards, Pipelines, Test Plans e Artifacts.

## Conecte e publique

Crie ou selecione um repositório em um projeto do Azure DevOps e, depois, execute localmente:

```bash
git remote add origin https://dev.azure.com/ORGANIZATION/PROJECT/_git/REPOSITORY
git push -u origin main
```

A URL exata pode ser copiada pela ação Clone do repositório. Use a autenticação do Microsoft Entra, SSH ou um personal access token com escopo adequado, de acordo com a política da sua organização.

## Integrações úteis

- Pull requests oferecem suporte a revisores, políticas de branch, itens de trabalho vinculados e validação de builds.
- Azure Pipelines pode compilar, testar, analisar e fazer deploy a partir de eventos do repositório.
- Azure Boards vincula commits e pull requests a itens de trabalho para garantir rastreabilidade.
- Políticas de branch podem exigir revisores, builds bem-sucedidos e resolução de comentários.
- Azure Artifacts fornece feeds para pacotes e dependências de build.

Conceda permissões por meio de grupos sempre que possível. Proteja conexões de serviço e grupos de variáveis, e separe a aprovação de deploys em produção dos direitos de contribuição no código.
