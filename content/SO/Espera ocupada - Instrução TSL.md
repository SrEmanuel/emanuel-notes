20250329-2014
Status: #idea
Tags: [[Exclusão Mútua com espera ocupada]]

A instrução TSL é uma forma de também trabalhar com exclusão mútua, mas também usando a técnica de espera ocupada. Ela é muito parecida com a técnicas de [[Espera ocupada - Variáveis tipo trava|variáveis de trava]], contudo tem um auxílio importante do hardware.

O macete dessa técnica consiste na característica **atômica** de uma função em **linguagem de máquina** de não ter **preempção** durante a execução de uma instrução assembly, pois ela é o nível mais baixo. Ou seja, não há como ter uma condição de corrida durante a execução de uma instrução assembly, pois somente ela está sendo executada naquele ciclo de clock no processador.

Para tirar vantagem da característica atômica, a instrução TSL já verifica e define o valor de LOCK para 1, independentemente do que esteja setado lá. Assim, antes mesmo de verificar se tem alguém usando a região crítica, a instrução já travou a variável de controle. Após isso, o código pode verificar se o valor de LOCK era 1 anteriormente. Caso seja, ele entra em loop esperando esse valor voltar para 0.

Essa técnica é interessante pois nunca haverá uma condição de corrida. Mesmo com um sistema de mais de um processador, o conjunto de CPUs tem técnicas para travar o barramento de acesso a memória implementados.

> [!PDF|yellow] [[Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy).pdf#page=105&selection=83,2,93,13&color=yellow|Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy), p.86]]
> > As operações de leitura e armazenamento da palavra são seguramente indivisíveis — nenhum outro processador pode acessar a palavra na memória até que a instrução tenha terminado. A CPU executando a instrução TSL impede o acesso ao barramento de memória para proibir que outras CPUs acessem a memória até ela terminar.
> 
> 


---
# References