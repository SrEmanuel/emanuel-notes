20250326-2032
Status: #idea
Tags: [[Race Conditions]]

Condições de corridas no contexto de processos no sistema operacional ocorrem quando temos dois processos acessando mais de um recurso crítico ao mesmo tempo, podendo ocasionar conflitos entre os dois.

Vejamos o exemplo: em um [[Spool de Impressão]], temos um local teórico com diversos espaços que irão armazenar, como se fossem em uma fila, os arquivos a serem imprimidos. 
No Spool, há uma variável de controle chamada de `proximo_slot_livre`. Em um contexto dois processos $A$ e $B$, ao mesmo tempo, acessam o spool e verificam o valor do próximo slot livre.

Pense no seguinte código:

```c

int imprimir(){
	const slotLivre = pegarSlotLivre();
	armazenarArquivo(slotLivre);
	bloquearSlot(splotLivre);
}

```

Agora pense que, o processo $A$ iniciou o processo de enviar o arquivo para ser impresso. Obteve o slot livre e armazenou o arquivo, mas - contudo -  o [[Escalonador de Processos]] realizou uma [[preempção]]  para o processo $B$ e o processo $A$ não pôde terminar o último comando de bloquear o slot. Não haveríamos nenhum problema, se o próximo processo não tentasse imprimir, correto?

Contudo, o processo $B$ deseja imprimir, e realiza a solicitação e executando o mesmo processo até o final, bloqueando o slot. Mas o [[Escalonador de Processos]] novamente realiza uma preempção ao processo $A$. O ponto aqui é que o processo $A$ **já executou** a linha de verificação do slot livre e, não sabe que o slot que ele obteve está "ocupado" pelo processo $B$. Dessa forma, ele irá **sobre escrever** o valor nesse slot, fazendo o conteúdo escrito por $B$ se perder e nunca ser impresso.

A solução para essa questão é a definição de uma [[Região Crítica em Sistemas Operacionais]], que irá impedir que mais de um processo acessem o mesmo valor ao mesmo tempo, podendo ocasionar conflitos.

