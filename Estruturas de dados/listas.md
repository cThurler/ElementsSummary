# Listas
Listas são como uma corrente, cada elo da corrente (ou nó) carrega uma carga (o valor) e sabe quem é o próximo da fila (o próximo nó).

Diferente dos arrays, que são como prateleiras fixas onde os objetos ficam lado a lado e numerados, as listas não têm um tamanho fixo e os elementos não precisam estar grudados na memória. Eles apenas precisam saber pra onde ir depois.

Em c, podemos definir um nó como uma struct, assim:
```c 
struct No {
    int valor;
    struct No* proximo; 
    };
```
>Temos um campos para armazenar dados (neste caso valor), </br> e também sempre teremos um outro campo para armazenar o endereço do próximo nó. 

E se tivermos 3 nós conectados:

<pre> [10] → [20] → [30] → NULL </pre>

Se você quiser inserir um novo nó entre duas outras, é só pegar o nó anterior e mudar a direção da setinha dela. Isso é fácil porque nada está colado, os elementos são independentes e apenas apontam uns pros outros.

Diferente de um array, onde, pra colocar algo no meio, você precisa tirar todos os elementos seguintes e empurrar pra frente.

## Por que usar listas?
- Flexibilidade: ideal quando você não sabe quantos elementos vai ter.
- Inserção/remoção rápida: você só atualiza alguns ponteiros, sem mover o resto.

(Também existem outros tipos de listas, como listas de caminho duplo ou as que fazem um loop.)

### Alguns pontos negativos:
- Se você quiser o elemento indíce 50, vai ter que passar por todos os 49 elementos anteriores. Não tem como “pular direto” como nos arrays.
- Como cada elemento precisa armazenar um ponteiro, você usa um pouco mais de memória.