# 4.1 Fundamentos da integração

As plataformas hospedadas acrescentam serviços de colaboração e entrega ao redor de um repositório Git. Os comandos locais continuam familiares; a plataforma fornece identidade, permissões, revisão, automação e visibilidade do projeto.

## O fluxo comum

1. Crie ou selecione um repositório remoto.
2. Conecte o repositório local com `git remote add origin <repository-url>`.
3. Envie uma branch com `git push -u origin <branch-name>`.
4. Abra um pull request ou merge request para revisão.
5. Deixe as verificações obrigatórias serem executadas antes do merge.
6. Exclua a branch de curta duração depois que a alteração for integrada.

## Escolha HTTPS ou SSH

HTTPS é simples para começar e normalmente usa um personal access token em vez da senha da conta. SSH usa um par de chaves e é conveniente para quem trabalha frequentemente pela linha de comando. Nunca coloque tokens, chaves privadas ou credenciais em um repositório.

## O que configurar

No mínimo, defina a branch padrão, as regras de proteção de branches, os requisitos de revisão, as verificações de status, o vínculo com issues e quem pode fazer push ou merge. Essas políticas fazem parte do processo de entrega da equipe, e não são apenas elementos decorativos da plataforma.
