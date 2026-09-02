# 4.6 Checklist de integração segura

Antes de considerar uma integração pronta, verifique o seguinte:

- A URL remota está correta e não contém um secret.
- A autenticação usa chaves SSH, tokens ou uma identidade de aplicação com escopo limitado.
- A branch padrão está protegida contra pushes diretos acidentais.
- Pull requests ou merge requests exigem revisão apropriada e verificações automatizadas aprovadas.
- Os secrets de CI/CD estão armazenados no gerenciador de secrets da plataforma.
- A análise de dependências, secrets e vulnerabilidades está habilitada quando apropriado.
- O deploy em produção exige uma aprovação separada ou um ambiente protegido.
- Os webhooks validam suas assinaturas e enviam somente os dados necessários.
- Os acessos são revisados quando uma pessoa, token, runner ou serviço muda de função.

A integração é bem-sucedida quando torna a entrega mais rastreável e repetível sem facilitar o uso indevido de credenciais ou alterações em produção.
