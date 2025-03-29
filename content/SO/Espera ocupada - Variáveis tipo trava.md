20250327-2122
Status: #idea
Tags: [[Exclusão Mútua com espera ocupada]]

Essa técnica de espera ocupada é uma das mais simples, mas que não funciona.

Ela simplesmente define uma variável global `trava`. Caso trava seja 1, então há alguém na região crítica. Caso 0, não há ninguém na região.

Quando o processo ele quer entrar na região crítica, ele deve olhar para o valor dessa variável, verificar se ela é zero, e depois alternar para 1.

Contudo, essa solução sofre do mesmo problema dito lá em [[Race Conditions em processos nos Sistemas Operacionais]], que é: e se o escalonador realizar a preempção no exato momento que o processo leu o valor 0 para a variável de trava? O outro processo que recebeu CPU time também verá 0 e, assim, teremos **dois processos** acessando a CPU ao mesmo tempo. Isso não pode!!

> [!PDF|yellow] [[Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy).pdf#page=103&selection=121,1,128,31&color=yellow|Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy), p.84]]
> > Infelizmente, essa ideia contém exatamente a mesma falha fatal que vimos no diretório de spool. Suponha que um processo lê a trava e vê que ela é 0. Antes que ele possa configurar a trava para 1, outro processo está escalonado, executa e configura a trava para 1. Quando o primeiro processo executa de novo, ele também configurará a trava para 1, e dois processos estarão nas suas regiões críticas ao mesmo tempo
> 
> 




---
# References