20250329-1800
Status: #idea
Tags: [[Exclusão Mútua com espera ocupada]]

O método da alternância explícita diz que cada um dos processos implementados irão chavear o acesso a região crítica um para o outro, de forma explícita, realmente alterando o valor de uma **variável** interna para um valor.

Por exemplo, pensemos em uma situação que há dois processos ($A$ e $B$) que acessam regiões críticas, com base no código a seguir:

```c
while(true){
	while(turn != 0) /*Loop caso o turn seja 1: outro processo na região crítica*/
	critical_region(); 
	turn = 1;
	noncritical_region();
	...
}

```

O processo $A$ inicia o processo de entrar na região crítica olhando a variável compartilhada $turn$, caso essa variável não seja igual ao seu ID (ou seja, 0), ela ficará em um loop esperando que o seu valor mude.

> Nota: aliais, é por isso que chamamos esses métodos de espera ocupada. Há um gasto de ciclos de clock e $quantumn$ esperando o processo que está ocupando a região crítica terminar. Literalmente tempo gasto à toa.

Quando o valor do turn permitir que o processo execute a região crítica, ele entrará e realizará o trabalho desejado, retornando novamente a variável o valor do próximo processo.

Contudo há um problema crucial aqui: a necessidade de esperar pelo o outro processo para ter acesso à região.
Pensemos na seguinte situação:

1. O processo $A$ executou o seu acesso à região crítica de forma bem rápida e iniciou o seu acesso a operações não-críticas. Ele passou a vez para o processo $B$.
2. O processo $B$ por sua vez também realizou o aceso bem rápido e iniciou o acesso a região não crítica, passando a vez para $A$.
3. Contudo, o processo $B$ precisa realizar novamente um acesso à região crítica, mas o processo $A$ ainda não realizou a sua excução e, assim, não trocou o valor da variável compartilhada para o processo $B$. Dessa forma, o processo $B$ ficará esperando até o $A fazer o acesso à região crítica e liberar o seu acesso.

Assim concluímos que a técnica de alternância explícita não funciona muito bem quando se tem processos com velocidades diferentes.


---
# References