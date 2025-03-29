20250327-1957
Status: #idea
Tags: [[Região Crítica em Sistemas Operacionais]] [[Exclusão Mútua]]

As técnicas de exclusão mútua com espera ocupada são estratégias
utilizadas para a solução de [[Race Conditions em processos nos Sistemas Operacionais]].

Elas trabalham com o conceito de **espera ocupada**, em que os processos que necessitam o acesso a uma [[Região Crítica]], ficam em uma espera, verificando a todo o momento se o processo que está na região crítica liberou o acesso.

Dentro do contexto da exclusão mútua com espera ocupada, há algumas estratégias que podem ser adotadas para solucionar o problema.

1. [[Espera ocupada - Desabilitando Interrupções]]
2. [[Espera ocupada - Variáveis tipo trava]]
3. [[Espera ocupada - Alternância explícita]]
4. [[Espera ocupada - Solução de Peterson]]
5. [[Espera ocupada - Instrução TSL]]


	


---
# References