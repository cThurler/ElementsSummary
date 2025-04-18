# Tipos Primitivos

Tipos primitivos são os blocos básicos de construção em linguagens de programação. Eles representam valores simples e diretos, como números, caracteres e valores lógicos. Em linguagens como C, esses tipos têm tamanhos fixos (ou quase fixos) e estão diretamente relacionados à forma como são armazenados na memória.

---

## Inteiros

### `int`
- **Tamanho**: geralmente 4 bytes (32 bits)
- **Intervalo**: -2.147.483.648 a 2.147.483.647 (em sistemas de 32 bits)
- **Descrição**: representa números inteiros, positivos ou negativos.
- **Alocação em memória**: armazenado em um bloco contínuo de 4 bytes.

*Porque ele precisa de 4 bytes?*
O tipo `int` é um tipo numérico usado para armazenar inteiros. O tamanho de um `int` em muitos sistemas modernos é **4 bytes (32 bits)**. Isso se deve à arquitetura de processadores modernos (de 32 ou 64 bits), que trabalham de forma mais eficiente com inteiros de 32 bits. O processador pode manipular esses valores de maneira otimizada, sem desperdício de espaço, e a alocação de 4 bytes proporciona uma boa relação entre capacidade e desempenho.


### `short`
- **Tamanho**: 2 bytes (16 bits)
- **Intervalo**: -32.768 a 32.767

O tipo `short` armazena inteiros menores e é alocado com **2 bytes**. O motivo para isso é a necessidade de otimizar o uso de memória quando os valores que precisam ser armazenados são pequenos. Embora o `short` ocupe menos espaço do que o `int`, sua capacidade de armazenar valores é mais limitada.

### `long`
- **Tamanho**: 4 ou 8 bytes, dependendo da arquitetura
- **Descrição**: utilizado quando o intervalo do `int` é insuficiente.

O tipo `long` armazena inteiros maiores. Em sistemas de 32 bits, ele geralmente ocupa **4 bytes**, mas em sistemas de 64 bits ele ocupa **8 bytes**. Isso ocorre porque em sistemas de 64 bits, os processadores são projetados para trabalhar de forma mais eficiente com números maiores, e o aumento do tamanho de 4 para 8 bytes oferece maior capacidade e intervalo de valores.

---

## Caracteres

### `char`
- **Tamanho**: 1 byte (8 bits)
- **Intervalo**: -128 a 127 (ou 0 a 255 se `unsigned`)
- **Descrição**: armazena um único caractere (como 'A', 'b', '1')
- **Representação**: normalmente baseado na tabela ASCII

*Porque ele precisa de somente 1 byte?*
O tipo `char` é usado para armazenar caracteres. Em sistemas baseados no padrão **ASCII**, cada caractere é representado por 7 ou 8 bits. Como resultado, o tipo `char` é alocado com **1 byte**. Esse tipo é eficiente para armazenar caracteres de texto em operações de leitura e escrita.

---

## Ponto flutuante

### `float`
- **Tamanho**: 4 bytes (32 bits)
- **Precisão**: ~7 casas decimais significativas

### `double`
- **Tamanho**: 8 bytes (64 bits)
- **Precisão**: ~15 casas decimais significativas

> Ambos os tipos são armazenados com sinal, expoente e mantissa, de acordo com o padrão IEEE 754.

---

## Booleanos

### `_Bool` (em C)
- **Tamanho**: 1 byte (em geral)
- **Valores**: 0 (falso) ou 1 (verdadeiro)
- **Representação**: desde o C99, `_Bool` representa verdadeiro/falso.

> Para uso mais legível, é comum incluir o cabeçalho `#include <stdbool.h>` e utilizar os nomes `bool`, `true` e `false`.

---

## Alocação e alinhamento

- Cada tipo primitivo é armazenado em blocos de memória cujo tamanho é definido pelo compilador/sistema.
- Alguns sistemas alinham variáveis em endereços múltiplos do seu tamanho (por exemplo, um `int` de 4 bytes pode começar sempre em um endereço múltiplo de 4).
- Isso garante maior eficiência no acesso à memória, mas pode causar **desperdício de espaço** quando combinamos tipos de tamanhos diferentes em structs.

---

## Resumo

| Tipo       | Tamanho (bytes) | Valor típico                 |
|------------|------------------|------------------------------|
| `char`     | 1                | Caracteres (A, B, C...)       |
| `int`      | 4                | Inteiros                      |
| `short`    | 2                | Inteiros menores              |
| `long`     | 4 ou 8           | Inteiros maiores              |
| `float`    | 4                | Números com ponto decimal     |
| `double`   | 8                | Números decimais precisos     |
| `_Bool`    | 1                | Verdadeiro ou falso           |

---

Compreender os tipos primitivos ajuda a entender melhor como a memória é usada pelo seu programa e como otimizar tanto espaço quanto desempenho.

