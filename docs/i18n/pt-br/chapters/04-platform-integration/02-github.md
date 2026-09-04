# 4.2 GitHub

O GitHub combina repositórios Git hospedados com pull requests, Issues, Actions, Projects, Packages e recursos de segurança.

## Conecte e publique

Crie um repositório vazio no GitHub e, depois, execute localmente:

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
git push -u origin main
```

Substitua `OWNER`, `REPOSITORY` e `main` pelos seus valores. Não inicialize o repositório do GitHub com um segundo README quando o repositório local já tiver um, a menos que você planeje reconciliar os históricos.

## Autenticação

O GitHub [removeu a autenticação por senha para operações Git em agosto de 2021](https://docs.github.com/pt/authentication/keeping-your-account-and-data-secure/about-authentication-to-github); o prompt de HTTPS agora espera um token, não a senha da sua conta. Escolha uma das opções:

- **Um [personal access token](https://docs.github.com/pt/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)** usado no lugar da senha. O GitHub recomenda os tokens *fine-grained* mais recentes — com escopo para repositórios e permissões específicas — em vez dos tokens *classic*, que concedem escopos amplos e abrangentes para toda a conta, como `repo`. Um token classic sem uso é revogado automaticamente após um ano; um token fine-grained precisa receber uma expiração no momento da criação.
- **Uma [chave SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh)** — o GitHub recomenda gerar uma chave Ed25519 — adicionada à sua conta uma vez, depois do que `git push`/`git pull` não pedem mais credenciais.
- **GitHub CLI (`gh auth login`) ou Git Credential Manager**, que a própria documentação do GitHub sugere antes de gerar um token manualmente, já que essas ferramentas gerenciam o armazenamento e a renovação do token para você.

O GitHub também [exige autenticação de dois fatores (2FA)](https://docs.github.com/pt/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication) para contas que contribuem com código, usando um app TOTP, uma chave de segurança física ou o GitHub Mobile.

## Integrações úteis

- Pull requests oferecem revisão, discussão, aprovações obrigatórias e verificações de status.
- GitHub Actions pode testar, analisar, empacotar e fazer deploy a partir de pushes ou pull requests.
- [Regras de proteção de branch](https://docs.github.com/pt/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches) podem exigir revisões, verificações aprovadas e commits assinados.
- Ambientes podem restringir deploys e proteger secrets de produção.
- Webhooks e a API conectam eventos do repositório a sistemas externos.

Use personal access tokens granulares com o menor privilégio necessário ou GitHub Apps. Armazene secrets de automação nos secrets do repositório ou do ambiente, nunca em arquivos de workflow ou no código-fonte.

## Armadilhas comuns

- Um PAT classic colado em um script com o escopo `repo` completo, quando o script só faz push para um único repositório — o vazamento desse token compromete todos os repositórios que a conta pode acessar. Use um token fine-grained com escopo para o único repositório em questão.
- Definir a expiração de um PAT e esquecer dela: no dia em que ele expira, o `git push` falha com um erro de autenticação que parece um remoto quebrado, e não uma credencial vencida.
- Gerar uma chave SSH sem senha (passphrase) em uma máquina compartilhada. O GitHub consegue verificar que a chave veio de você, mas não consegue proteger um arquivo de chave privada que qualquer pessoa com acesso ao disco pode ler.

## Exercício

Crie um personal access token fine-grained com escopo para um repositório de prática, com permissão **Contents: Read and write** e uma expiração curta (7 dias). Use-o uma vez para fazer `git push` via HTTPS, depois revogue-o antecipadamente e confirme que o próximo push falha com um erro de autenticação.

## Referências

- GitHub Docs — [Sobre a autenticação no GitHub](https://docs.github.com/pt/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)
- GitHub Docs — [Gerenciando seus personal access tokens](https://docs.github.com/pt/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)
- GitHub Docs — [Conectando-se ao GitHub com SSH](https://docs.github.com/pt/authentication/connecting-to-github-with-ssh)
- GitHub Docs — [Sobre a autenticação de dois fatores](https://docs.github.com/pt/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication)
- GitHub Docs — [Sobre branches protegidas](https://docs.github.com/pt/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
