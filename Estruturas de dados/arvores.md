# Árvores

Árvores são estruturas de dados hierárquicas. Diferente de arrays, listas, filas e pilhas (que são estruturas lineares), uma árvore se ramifica em várias direções, formando uma estrutura de níveis e subníveis.

Na prática, uma árvore é composta por **nós** conectados. Cada nó pode ter um ou mais filhos.

## Árvore Binária

A **árvore binária** é o tipo mais comum. Nela, cada nó pode ter até dois filhos: um à esquerda e um à direita.

```
      [10]
     /    \
   [5]    [15]
  /  \     \
[2]  [7]   [20]
```

- O nó 10 é a **raiz** da árvore (ponto de partida).
- Os nós 5 e 15 são **filhos** de 10.
- Os nós 2, 7 e 20 são **folhas**, pois não possuem filhos.

## Estrutura em C

```c
struct No {
    int valor;
    struct No* esquerdo;
    struct No* direito;
};
```

> Cada nó armazena um valor e dois ponteiros, um para o filho da esquerda e outro para o filho da direita.

## Termos importantes

- **Raiz**: o primeiro nó da árvore.
- **Filho**: um nó conectado abaixo de outro.
- **Pai**: o nó acima de um filho.
- **Folha**: nó sem filhos.
- **Altura**: distância do nó mais profundo até a raiz.
- **Subárvore**: qualquer nó pode ser considerado raiz de sua própria árvore.

## Aplicações no mundo real

- Organização de arquivos e pastas.
- Árvores de decisão.
- Estruturas de busca em bancos de dados.
- Representação de expressões matemáticas.
- Planejamento de tarefas com dependências.


## Por que usar árvores?

- Organizam dados de forma hierárquica.
- Permitem buscas rápidas em árvores balanceadas.
- Representam relações estruturais com caminhos bem definidos.

Algumas variações de árvores: Árvores rubro-negras, árvores balanceadas e árvores binárias de busca.