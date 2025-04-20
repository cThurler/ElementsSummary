# Arrays

Um array ou um vetor é uma estrutura de dados que armazena elementos em sequência, se comportando/navegando através de um índice.

O indíce começa sempre em 0.

<pre>int numeros[5] = {10, 20, 30, 40, 50};</pre>

## Propriedades de arrays fixos

Quando você declara um array, o sistema operacional (ou o runtime da linguagem) reserva um bloco contínuo de memória suficiente para armazenar todos os elementos, um após o outro, como se fosse uma prateleira com espaços numerados.

Ou seja, em um array não dinâmico, podemos calcular o endereço do próximo elemento a partir do  elemento atual, 

<pre> *endereço_base + (índice * tamanho_do_tipo)* </pre>

por isso o acesso se torna bem rápido.

Supondo que cada int ocupa 4 bytes, a memória poderia, por exemplo, ficar assim:

| Endereço | Conteúdo |
|-------------|-------------|
| 0x1000     | 10     |
| 0x1004     | 20     |
| 0x1008     | 30     |
| 0x100C     | 40     |
```c 
int numeros[5] = {10, 20, 30, 40, 50}; 
```

> A ideia aqui é que o compilador sabe que </br>para acessar o numeros[2], basta ir até </br>**endereço_base + 2 × sizeof(int) → 0x1000 + 8 = 0x1008**. 

Esse modelo de organização permite acessos extremamente rápidos, porque não há necessidade de procurar elemento por elemento. O ponteiro inicial e o tamanho do tipo já te levam direto ao valor desejado.

No nível mais baixo (por exemplo, em C), arrays são essencialmente ponteiros para o primeiro elemento. Então, isso:
```c
int *ponteiro = numeros; 
printf("%d", *(ponteiro + 2)); // imprime 30 
```

Está acessando a terceira posição do array via aritmética de ponteiros. Isso reforça a ideia de que os elementos estão em posições de memória ordenadas e calculáveis.

<br>

**Mesmo que você use malloc para alocar o array, o bloco de memória ainda será contínuo.** Exemplo:

```c
int* numeros = malloc(5 * sizeof(int));
```
### Por que importa esse arranjo contíguo?
Porque ele determina as características fundamentais dos arrays:

Inserir ou remover elementos no meio de um array é caro, pois é necessário mover todos os elementos seguintes.

Arrays são ideais para leitura rápida, mas não para escrita dinâmica.

Se você quiser um container com crescimento ou remoção mais flexível, precisa de estruturas como listas ligadas, que abrem mão do armazenamento contíguo em troca de flexibilidade.

## Propriedades de arrays dinamicos em linguagens de alto nível

**Essas estruturas se comportam como arrays, mas internamente não garantem um único bloco fixo para sempre.**

Em arrays fixos alocados, os elementos ainda ficam em posições contíguas, e o acesso por índice continua valendo via aritmética de ponteiros. (como visto anteriormente)

Já em estruturas de alto nível que crescem automaticamente (como listas em Python ou ArrayList em Java), o comportamento simula arrays, mas internamente pode envolver realocação e cópias. Nesse caso, o acesso por índice ainda é rápido, mas o bloco de memória pode mudar com o tempo.

Como eles funcionam:
- Inicialmente, alocam um bloco contínuo.
- Quando o tamanho estoura, realocam tudo em um novo bloco maior (geralmente dobrando o tamanho).
- Copiam os elementos do antigo para o novo bloco.
- Continuam como um array até encher de novo.