20250327-1300
Status: #idea
Tags: [[Região Crítica]]

Uma região crítica no sistema operacional é uma área de acesso a memória, recursos etc, que tem um controle de entrada para evitar conflitos de [[Race Conditions em processos nos Sistemas Operacionais]].

O seu principal objetivo é de fazer uma área em que dois processos não podem ler e escrever dados compartilhados ao mesmo tempo. Sempre alguém deverá ter prioridade na leitura / escrita.

Há diversas formas de se realizar a implementação de região crítica e de solucionar o problema de [[Race Conditions em processos nos Sistemas Operacionais]].
#### Formas de solução de Race Conditions

As formas de solução de Race Conditions no sistema operacional utilizam o conceito de [[Exclusão Mútua]], em que é garantido que somente um processo tem acesso a um recurso computacional.

1. [[Exclusão Mútua com espera ocupada]]
2. [[Solução de Software com bloqueios]]



---
# References