# 4.5 Bitbucket e Atlassian

O Bitbucket, da Atlassian, oferece repositórios Git com pull requests e Pipelines. Ele pode conectar o trabalho do repositório a issues do Jira e a outros serviços da Atlassian.

## Conecte e publique

Crie um repositório no Bitbucket Cloud e, depois, execute localmente:

```bash
git remote add origin https://bitbucket.org/WORKSPACE/REPOSITORY.git
git push -u origin main
```

Use a URL de clone fornecida pelo seu workspace do Bitbucket. O Bitbucket Data Center usa URLs e políticas de autenticação específicas da organização.

## Autenticação

A autenticação por HTTPS do Bitbucket Cloud mudou em 2026: os [app passwords](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/) foram descontinuados em um cronograma em fases que terminou em julho de 2026 e não funcionam mais. O método atual para scripts, ferramentas de CI e a linha de comando do Git é um [API token](https://support.atlassian.com/bitbucket-cloud/docs/using-api-tokens/), criado a partir da sua conta Atlassian e usado junto com o seu nome de usuário do Bitbucket como credencial do Git. Se uma página, tutorial ou ferramenta ainda disser para criar um "app password", trate essa instrução como desatualizada.

Uma chave SSH ([Ed25519 recomendada](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-linux/)) não é afetada pela descontinuação dos app passwords e continua sendo uma boa opção para quem trabalha com frequência pela linha de comando.

Habilite a [verificação em duas etapas](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/) na conta — por meio de um app autenticador ou uma chave de segurança — independentemente de qual credencial Git você usa no dia a dia.

## Integrações úteis

- Pull requests oferecem revisão, aprovações, tarefas e verificações de merge.
- `bitbucket-pipelines.yml` define as etapas de build e deploy do Bitbucket Pipelines.
- A integração com o Jira vincula branches, commits e pull requests a itens de trabalho.
- Ambientes de deploy podem restringir variáveis e releases de produção.
- [Permissões de branch](https://support.atlassian.com/bitbucket-cloud/docs/use-branch-permissions/) restringem quem pode fazer push ou merge em uma determinada branch; apps do Marketplace e webhooks conectam o Bitbucket a outras ferramentas de engenharia.

Use tokens de acesso do repositório ou do workspace com as menores permissões necessárias. Mantenha as chaves de issue do Jira nos nomes de branches ou nas mensagens de commit somente quando essa convenção for adotada pela equipe, e nunca coloque secrets nesses campos.

## Armadilhas comuns

- Seguir um tutorial antigo que manda criar um "app password" — a partir de meados de 2026 esse fluxo não existe mais; crie um API token em vez disso.
- Uma integração (ferramenta de CI, gerenciador de pacotes, cliente Git) ainda configurada com um app password salvo quebrando silenciosamente quando o cronograma de descontinuação chegou à remoção total, sem aviso local prévio.
- Presumir que um API token se comporta exatamente como o antigo app password: ele autentica Git e chamadas de API, mas não pode ser usado para fazer login no próprio bitbucket.org.

## Exercício

Crie um API token do Bitbucket e, depois, use-o junto com o seu nome de usuário do Bitbucket para autenticar um `git push` via HTTPS. Confirme, nas configurações de segurança da sua conta, que nenhum app password ainda está listado como ativo.

## Referências

- Atlassian Support — [App passwords](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)
- Atlassian Support — [Usando API tokens](https://support.atlassian.com/bitbucket-cloud/docs/using-api-tokens/)
- Atlassian Support — [Habilitar a verificação em duas etapas](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/)
- Atlassian Support — [Configurar chaves SSH pessoais](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-linux/)
- Atlassian Support — [Usar permissões de branch](https://support.atlassian.com/bitbucket-cloud/docs/use-branch-permissions/)
