# Filas e Pilhas
Filas e pilhas são estruturas de dados lineares. Ambas armazenam elementos em sequência, mas a forma como os elementos são inseridos e removidos é diferente em cada uma.

**Fila (Queue)**
Uma fila segue o princípio **FIFO** – First In, First Out, ou seja, o primeiro elemento a entrar é o primeiro a sair.

É como uma fila de pessoas esperando atendimento. Quem chegou primeiro, sai primeiro.

<pre>[1] [2] [3] [4]</pre>

Se inserirmos um novo elemento 5, ele será adicionado no fim da fila:

<pre>[1] [2] [3] [4] [5]</pre>

E se removemos um elemento, será o 1, pois ele foi o primeiro a entrar.


<pre>[2] [3] [4] [5]</pre>

Exemplo simples de uma fila em C:
```c
<pre>
struct Fila {
    int dados[100];
    int inicio;
    int fim;
};
</pre>
```

>Esse exemplo usa um array fixo para simular uma fila. Para algo mais flexível, seria possível usar ponteiros e alocação dinâmica.

Aplicações no mundo real:
- Fila de impressão.
- Tarefas agendadas para execução.
- Processamento por ordem de chegada.
---

**Pilha (Stack)**
A pilha segue o princípio LIFO – Last In, First Out, ou seja, o último elemento a entrar é o primeiro a sair.
É como uma pilha de pratos. Você coloca um prato em cima da pilha e também retira sempre o que está no topo.

<pre>
[1] 
[2] 
[3] 
[4]</pre>

Se você empilhar o número 5, ele vai para o topo. Se remover, o 5 será o primeiro a sair.

```c
<pre>
struct Pilha {
    int dados[100];
    int topo;
};
</pre>
```
>O campo topo armazena o índice do elemento mais recente da pilha.

Aplicações no mundo real:
- Histórico de navegação em um navegador.
- Chamadas de função em execução (call stack).
- Desfazer/refazer em editores de texto.