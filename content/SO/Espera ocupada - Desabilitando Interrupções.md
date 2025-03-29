20250327-2004
Status: #idea
Tags: [[Exclusão Mútua com espera ocupada]] | [[Escalonador de Processos]]

Essa estratégia consiste na desabilitação da [[preempção]] do escalonador quando um processo irá modificar uma região crítica. Ou seja, quando o programa vai realizar o início de operações de risco a CPU não irá mais chavear o seu acesso entre o processo, o escalonador e outros processo.

Antes de iniciar qualquer operação crítica, o processo irá ir e desabilitar a preempção e irá reabilitá-la após todo o processo realizado corretamente.

Essa solução de fato resolve o problema de [[Race Conditions]] de cara. Contudo, há alguns pontos que impedem a viabilidade dessa solução:

1. Caso o processo realize a desabilitação da preempção, mas nunca mais o reabilite, a CPU nunca irá mudar de contexto. (pense caso o processo sofra uma falha durante o acesso à região crítica! Nunca mais teremos outro processo executando!).
2. A desabilitação da preempção só ocorre em um core. Em um sistema **multicore**, com vários processo rolando ao mesmo tempo, teríamos de desabilitar **todos os cores** para funcionar.
3. Não é interessante que essa operação seja implementada pelos programas de usuário.

> [!] Apesar dessa técnica, no ponto 3, não ser adequada para programas de usuário implementarem, o kernel realiza tais operações de desabilitação da preempção. Ele tem essa autoridade.

> [!PDF|yellow] [[Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy).pdf#page=103&selection=97,0,107,53&color=yellow|Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy), p.84]]
> > A possibilidade de alcançar a exclusão mútua desabilitando interrupções — mesmo dentro do núcleo — está se tornando menor a cada dia por causa do número cada vez maior de chips multinúcleo mesmo em PCs populares. Dois núcleos já são comuns, quatro estão presentes em muitas máquinas, e oito, 16, ou 32 não ficam muito atrás. Em um sistema multinúcleo (isto é, sistema de multiprocessador) desabilitar as interrupções de uma CPU não evita que outras CPUs interfiram com as operações que a primeira está realizando. Em consequência, esquemas mais sofisticados são necessários
> 
> 


---
# References