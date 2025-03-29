#SistemaOperacional #Escalonadores

Há dois tipos de #Algoritmos de escalonamento de processos: os preemptivos e não preemptivos

## Algoritmos #preemptivos

Os algoritmos preemptivos são aqueles que se se tem total conhecimento do tempo que um processo irá levar para executar, uma vez que ele irá rodar por um tempo determinado e **pode ser interrompido** pela CPU durante a sua execução.

Esse tipo de algoritmo conta com a ajuda do relógio da CPU, que irá gerar um sinal de **interrupção** que irá avisar a CPU que deve-se executar o código relacionado ao gerenciamento de processos pelo Kernel.

> ([[Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy).pdf#page=125&selection=15,17,25,29&color=yellow|Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy), p.106]])
> Um algoritmo de escalonamento não preemptivo escolhe um processo para ser executado e então o deixa ser executado até que ele seja bloqueado (seja em E/S ou esperando por outro processo), ou libera voluntariamente a CPU.

## Algoritmos #não-preemptivos

Quando se há um escalonador com algoritmos não preemptivos, a execução do processo acontece de forma inteira, até a sua finalização completa. **Somente** após isso, o kernel recebe o controle novamente da CPU para decidir qual processo deve ser executado em seguida.

Esse tipo de algoritmo deve levar em consideração um ponto importante: não há como parar um processo após a sua execução. Dessa forma, o [[Escalonador de Processos]] deve decidir de forma certeira qual será o algoritmo a ser executado.

> ([[Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy).pdf#page=125&selection=33,0,39,32&color=yellow|Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy), p.106]])
> Por outro lado, um algoritmo de escalonamento preemptivo escolhe um processo e o deixa executar por no máximo um certo tempo fixado.

> ([[Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy).pdf#page=125&selection=39,33,47,15&color=yellow|Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy), p.106]])
> Se ele ainda estiver executando ao fim do intervalo de tempo, ele é suspenso e o escalonador escolhe outro processo para executar (se algum estiver disponível). Realizar o escalonamento preemptivo exige que uma interrupção de relógio ocorra ao fim do intervalo para devolver o controle da CPU de volta para o escalonador. Se nenhum relógio estiver disponível, o escalonamento não preemptivo é a única solução
