
Todos os programas de computadores executam dentro de um outro programa, chamado de sistema operacional. O sistema operacional é responsável pelo gerenciamento de todos os recursos de hardware do computador, atuando como o intermediador de operações de entrada e saída de dados e como interface mais simples com o hardware.

Dentro desse contexto, há dois modos de operação de softwares existentes: o modo núcleo e o modo usuário.

> ([[Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy).pdf#page=123&selection=23,0,24,22&color=yellow|Livro SO -Sistemas_Operacionais_Modernos_Tanenbaum (copy), p.104]])
> Com o advento dos computadores pessoais, a situação mudou de duas maneiras


#### Modo núcleo (ou modo supervisor)

O modo núcleo é o modo de acesso **irrestrito** a todos os recursos computacionais da máquina. Somente o #SistemaOperacional pode executar nesse modo.
Nesse modo o software (geralmente o sistema operacional) pode acessar todos os recursos da máquina e executar qualquer instrução que o conjunto de hardware pode executar.

#### Modo de usuário

O modo de usuário é o modo comum no qual os programas de computadores comuns são executados. Ele tem acesso limitado a certas instruções na máquina, tendo que utilizar o Sistema Operacional como ponte de comunicação para operações mais complexas, como Entrada e Saída de dados.



