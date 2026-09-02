# 1.4 O modelo mental do Git

Pense em três lugares:

1. Árvore de trabalho: arquivos que estão sendo editados.
2. Área de staging: o próximo instantâneo que está sendo preparado.
3. Histórico do repositório: instantâneos confirmados por commits.

O fluxo básico é `edit -> git add -> git commit`. `git status` mostra as diferenças entre esses lugares e deve ser seu comando de diagnóstico mais frequente.
