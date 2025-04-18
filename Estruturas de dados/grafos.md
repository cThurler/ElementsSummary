# Grafos

Grafos são estruturas de dados usadas para representar relações entre elementos. Eles consistem em **vértices** (ou nós) e **arestas** (ou ligações) que conectam esses vértices.

Diferente das árvores, que têm uma hierarquia clara, os grafos são mais flexíveis e podem conter ciclos (voltas), múltiplas conexões e até direções nas arestas.


Imagine cidades conectadas por estradas:

```
[A] --- [B]
 |      /  \
 |    [C]  [D]
  \     \  /
   ---- [E]
```

- A, B, C, D, E são **vértices**.
- As linhas entre eles são **arestas**.

## Representação em C

Uma forma comum de representar grafos em C é usando uma **matriz de adjacência** ou **lista de adjacência**.

### Matriz de adjacência

```c
#define TAM 5

int grafo[TAM][TAM] = {0};

// Conectando o vértice 0 com o vértice 1
grafo[0][1] = 1;
grafo[1][0] = 1;
```

> Aqui `grafo[i][j] = 1` indica que existe uma conexão entre os vértices `i` e `j`.

### Lista de adjacência (mais eficiente para grafos esparsos)

```c
struct No {
    int destino;
    struct No* proximo;
};

struct ListaAdj {
    struct No* cabeca;
};

struct Grafo {
    int numVertices;
    struct ListaAdj* lista;
};
```

## Tipos de grafos

- **Não direcionado**: as conexões não têm direção.
- **Direcionado (dígrafos)**: as conexões têm um sentido (ex: fluxo de dados).
- **Ponderado**: cada aresta tem um peso (ex: distância, custo).
- **Cíclico**: há ciclos.
- **A-cíclico**: não há ciclos.

### Aplicações no mundo real

- Mapas e rotas (GPS).
- Redes sociais (conexões entre pessoas).
- Redes de computadores.
- Análise de dependência entre tarefas.
- Modelagem de fluxo de trabalho ou decisões.

### Por que usar grafos?

- Representam relações complexas entre elementos.
- Permitem modelar situações com múltiplos caminhos possíveis.
- São base para algoritmos importantes como busca em largura/profundidade, Dijkstra, Prim, etc.