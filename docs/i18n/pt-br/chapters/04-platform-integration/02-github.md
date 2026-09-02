# 4.2 GitHub

O GitHub combina repositórios Git hospedados com pull requests, Issues, Actions, Projects, Packages e recursos de segurança.

## Conecte e publique

Crie um repositório vazio no GitHub e, depois, execute localmente:

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
git push -u origin main
```

Substitua `OWNER`, `REPOSITORY` e `main` pelos seus valores. Não inicialize o repositório do GitHub com um segundo README quando o repositório local já tiver um, a menos que você planeje reconciliar os históricos.

## Integrações úteis

- Pull requests oferecem revisão, discussão, aprovações obrigatórias e verificações de status.
- GitHub Actions pode testar, analisar, empacotar e fazer deploy a partir de pushes ou pull requests.
- A proteção de branches pode exigir revisões, verificações aprovadas e commits assinados.
- Ambientes podem restringir deploys e proteger secrets de produção.
- Webhooks e a API conectam eventos do repositório a sistemas externos.

Use personal access tokens granulares com o menor privilégio necessário ou GitHub Apps. Armazene secrets de automação nos secrets do repositório ou do ambiente, nunca em arquivos de workflow ou no código-fonte.
