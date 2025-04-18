# Tabelas Hash

Tabelas hash (ou hash tables) são como índices de livros, são estruturas de dados que associam **chaves** a **valores**. A principal característica é que elas permitem acesso muito rápido aos dados, geralmente em tempo constante, desde que a função hash seja eficiente.

## Como funciona?

Imagine uma caixa com vários compartimentos numerados. A função hash é o que decide em qual compartimento (índice) cada chave será colocada.


## Estrutura

```c
struct Hash {
    int chave;
    char valor[50];
};

struct TabelaHash {
    struct Hash dados[TAM];
};
```

> Essa estrutura é simplificada. Na prática, você precisa tratar colisões (quando duas chaves diferentes geram o mesmo índice).

Por exemplo, se quisermos guardar o valor "João" usando a chave 123, aplicamos a função hash nessa chave:

```
função_hash(123) → 7
```

Isso quer dizer que "João" será armazenado na posição 7 da tabela de hashs.
>João é o valor de um hash, no qual sua chave é 123


## Colisões

Quando duas chaves resultam no mesmo índice, é necessário lidar com isso. Existem estratégias como:

- **Encadeamento (chaining)**: cada posição da tabela é uma lista ligada de elementos.
- **Endereçamento aberto (open addressing)**: procura-se outra posição livre dentro da tabela.

## Aplicações no mundo real

- Dicionários e mapas.
- Indexação de bancos de dados.
- Compiladores (armazenamento de identificadores e palavras-chave).
- Sistemas de cache.

## Por que usar tabelas hash?

- Acesso muito rápido aos dados.
- Ideal para buscas, inserções e remoções frequentes.
- Fácil de escalar com boas funções hash.
