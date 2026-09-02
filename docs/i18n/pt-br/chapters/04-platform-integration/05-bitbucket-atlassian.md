# 4.5 Bitbucket e Atlassian

O Bitbucket, da Atlassian, oferece repositórios Git com pull requests e Pipelines. Ele pode conectar o trabalho do repositório a issues do Jira e a outros serviços da Atlassian.

## Conecte e publique

Crie um repositório no Bitbucket Cloud e, depois, execute localmente:

```bash
git remote add origin https://bitbucket.org/WORKSPACE/REPOSITORY.git
git push -u origin main
```

Use a URL de clone fornecida pelo seu workspace do Bitbucket. O Bitbucket Data Center usa URLs e políticas de autenticação específicas da organização.

## Integrações úteis

- Pull requests oferecem revisão, aprovações, tarefas e verificações de merge.
- `bitbucket-pipelines.yml` define as etapas de build e deploy do Bitbucket Pipelines.
- A integração com o Jira vincula branches, commits e pull requests a itens de trabalho.
- Ambientes de deploy podem restringir variáveis e releases de produção.
- Marketplace e webhooks conectam o Bitbucket a outras ferramentas de engenharia.

Use tokens de acesso do repositório ou do workspace com as menores permissões necessárias. Mantenha as chaves de issue do Jira nos nomes de branches ou nas mensagens de commit somente quando essa convenção for adotada pela equipe, e nunca coloque secrets nesses campos.
