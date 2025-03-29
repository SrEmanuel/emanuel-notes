#SistemaOperacional 
## Tipos de Escalonamento de processos
 
 Há dois [[Tipos de escalonadores (Preemptivos vs Não  Preemptivos)]].
 Eles separam dois tipos de algoritmos específicos que irão selecionar qual o próximo software a ser executado na CPU.

> [!] **O tipo do escalonador varia de acordo com qual tipo de sistema que ele está sendo executado: não será aplicado um escalonador focado em sistemas de trabalho em lote em um sistema de multiusuário, bem como não irá ser usado um escalonador de sistemas de servidores em sistemas operacionais de nós-sensores.**


## Características gerais de um escalonador

#### Características Gerais

- Justiça: cada processo deve receber uma parcela justa de tempo da CPU;
- Balanceamento: diminuir a ociosidade do sistema;
- Políticas do sistema - prioridade de processos.
- 
> ([[Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy).pdf#page=126&selection=140,0,141,30&color=yellow|Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy), p.107]])
> Algumas metas do algoritmo de escalonamento sob diferentes circunstâncias.

#### Características específicas de Sistemas em Batch:

- Vazão: maximizar o número de jobs executados por hora;
- Tempo de retorno: tempo no qual o processo espera para ser finalizado;
- Eficiência: CPU deve estar 100% do tempo ocupada.




