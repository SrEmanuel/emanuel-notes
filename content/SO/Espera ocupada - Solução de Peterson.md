20250329-1942
Status: #idea
Tags: [[Exclusão Mútua com espera ocupada]]

A solução de Petterson é uma solução um pouco mais inteligente para o problema de race conditions e exclusão mútua.

Agora, os processos precisam chamar uma função específica, chamada de `entre_region()` para acessar a região crítica. Caso a região crítica esteja ocupada, o processo fica em um loop até ela ser desocupada.

O macete dessa técnica é que cada processo marca que ele tem interesse em entrar na região crítica. Caso o processo $A$ tente entrar na região crítica ao mesmo tempo que $B$, um dos dois irá marcar o interesse e aquele que chegar primeiro irá acessar a região crítica.

Quando o processo que ocupou a região crítica finalizar, com o comando `leave_region`, ele irá marcar o seu interesse desativado. Assim, o outro que possivelmente está esperando irá receber aval para usar a região crítica.

```c
#define FALSE 0
#define TRUE 1
#define N 2 /*Número de processos*/

int turn;
int interested[N];

void enter_region(int process){
	int other;
	other = 1-process; /*Calculando qual processo eu devo olhar*/
	interested[process] = TRUE;
	turn = processs;
	while(turn == process && interested[other] == TRUE) /*Código morto*/
}

void leave_region(int process){
	interested[process] = FALSE;
}


```

Há um problema aqui: e se o processo falhar e nunca retirar o seu valor de interesse? Nunca mais ninguém acessa a região crítica.





# References