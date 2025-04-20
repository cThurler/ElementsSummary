# Tipos Primitivos

Tipos primitivos são os blocos básicos de construção em linguagens de programação. Eles representam valores simples e diretos, como números, caracteres e valores lógicos. Em linguagens como C, esses tipos têm tamanhos fixos (ou quase fixos) e estão diretamente relacionados à forma como são armazenados na memória.

---

## Inteiros

### `int`
- **Tamanho**: geralmente 4 bytes (32 bits)
`*Sinal: 1 bit (positivo ou negativo)`
`*Magnitude: 31 bits (para representar o valor absoluto do número)`
- **Intervalo**: -2.147.483.648 a 2.147.483.647 (em sistemas de 32 bits)
- **Descrição**: representa números inteiros, positivos ou negativos.
- **Alocação em memória**: armazenado em um bloco contínuo de 4 bytes.

*Porque ele precisa de 4 bytes?*
O tipo `int` é um tipo numérico usado para armazenar inteiros. O tamanho de um `int` em muitos sistemas modernos é **4 bytes (32 bits)**. Isso se deve à arquitetura de processadores modernos (de 32 ou 64 bits), que trabalham de forma mais eficiente com inteiros de 32 bits. O processador pode manipular esses valores de maneira otimizada, sem desperdício de espaço, e a alocação de 4 bytes proporciona uma boa relação entre capacidade e desempenho.


### `short`
- **Tamanho**: 2 bytes (16 bits)
`*Sinal: 1 bit (positivo ou negativo)`
`*Magnitude: 15 bits (para representar o valor absoluto do número)`
- **Intervalo**: -32.768 a 32.767
- **Descrição**: utilizado para poupar espaço quando serão armazenados números pequenos.

O tipo `short` armazena inteiros menores e é alocado com **2 bytes**. O motivo para isso é a necessidade de otimizar o uso de memória quando os valores que precisam ser armazenados são pequenos. Embora o `short` ocupe menos espaço do que o `int`, sua capacidade de armazenar valores é mais limitada.

### `long`
- **Tamanho**: 4 ou 8 bytes, dependendo da arquitetura
`*Sinal: 1 bit (positivo ou negativo)`
`*Magnitude: 63 bits (para representar o valor absoluto do número)`
- **Descrição**: utilizado quando o intervalo do `int` é insuficiente.

O tipo `long` armazena inteiros maiores. Em sistemas de 32 bits, ele geralmente ocupa **4 bytes**, mas em sistemas de 64 bits ele ocupa **8 bytes**. Isso ocorre porque em sistemas de 64 bits, os processadores são projetados para trabalhar de forma mais eficiente com números maiores, e o aumento do tamanho de 4 para 8 bytes oferece maior capacidade e intervalo de valores.

>*Quando o sistema for de 64 bits, o long passa a ocupar 8 bytes, enquanto o int continua com 4 bytes. Isso confere ao long uma maior capacidade de armazenar números inteiros em arquiteturas de 64 bits. Portanto, a diferença de tamanho de memória entre int e long só se torna relevante em sistemas de 64 bits, onde o long ocupa 8 bytes, enquanto o int continua com 4 bytes.<br>Ou seja, o long **em um sistema 32bits** o long **não traz uma funcionalidade adicional em termos de capacidade de armazenamento** em relação ao int, já que ambos ocupam 4 bytes e têm o mesmo intervalo de valores.*

---

## Caracteres

### `char`
- **Tamanho**: 1 byte (8 bits)
- **Intervalo**: -128 a 127 (ou 0 a 255 se `unsigned`)
- **Descrição**: armazena um único caractere (como 'A', 'b', '1')
- **Representação**: normalmente baseado na tabela ASCII

*Porque ele precisa de somente 1 byte?*
O tipo `char` é usado para armazenar caracteres. Em sistemas baseados no padrão **ASCII**, cada caractere é representado por 7 ou 8 bits. Como resultado, o tipo `char` é alocado com **1 byte**. Esse tipo é eficiente para armazenar caracteres de texto em operações de leitura e escrita.


### `string`
- **Tamanho**: variável (dependente do número de caracteres)
- **Descrição**: uma sequência de caracteres, representada como um array de `char` em C, terminada com o caractere nulo (`'\0'`).
- **Representação**: uma string é uma cadeia de caracteres, como `"Olá"`, armazenada na memória com um caractere nulo (`'\0'`) no final.

*Porque a string tem tamanho variável?*  
A string tem tamanho variável porque seu comprimento depende do número de caracteres armazenados nela, e cada caractere é representado por um tipo `char`. A string é terminada com o caractere nulo (`'\0'`), que indica seu final na memória.

*O tamanho é simplesmente a quantidade de caracteres em bytes. <br> Uma string com N caracteres tem tamanho N bytes.*

*Sentenças ou palavras são simplesmente sequências de caracteres.*

---

## Ponto flutuante

### `float`
- **Tamanho**: 4 bytes (32 bits)
- **Precisão**: ~7 casas decimais significativas
`*Sinal: 1 bit (positivo ou negativo)`
`*Expoente: 8 bits (para determinar a magnitude do número)`
`*Mantissa: 23 bits (para representar a precisão do número)`

O tipo `float` é usado para armazenar números de ponto flutuante com precisão simples. Ele é alocado com **4 bytes**, de acordo com o padrão **IEEE 754**. O tamanho de 4 bytes é eficiente para operações aritméticas e permite a representação de números decimais com uma precisão limitada. Esse tamanho oferece um equilíbrio entre precisão e desempenho.

*Divisão entre parte inteira e parte decimal:*
Os 4 bytes de um `float` são divididos entre a parte inteira e a parte decimal do número. O valor é representado em **formato binário**, onde a parte inteira ocupa uma parte do número e a parte decimal ocupa outra. A precisão de um `float` é limitada a cerca de 7 casas decimais, o que significa que ele pode armazenar números com até 7 dígitos significativos, mas não necessariamente com precisão total em todas as casas decimais. Essa limitação vem da forma como o número é representado internamente no padrão IEEE 754.

Exemplo:
Se você armazenar o número `12.345678` em um `float`, ele pode ser arredondado para algo como `12.34567` devido à limitação de precisão.

*Como se guarda a posição da vírgula?*
Em vez de armazenar a vírgula ou ponto diretamente, o número é armazenado de forma científica, semelhante a notação científica, onde o número é expresso como: `1.2345 * 10^1`
Por conta disso, floats tem uma faixa de valores menor e uma precisão limitada quando comparado a tipos inteiros (mesmo que ambos utilizem 4 bytes), devido a necessidade de guardar o número em notação científica.


### `double`
- **Tamanho**: 8 bytes (64 bits)
- **Precisão**: ~15 casas decimais significativas
`*Sinal (1 bit): Determina se o número é positivo ou negativo.`
`*Expoente (11 bits): Define o expoente da base 2, ou seja, determina a escala do número.`
`*Mantissa (52 bits): Armazena a parte significativa do número.`

O tipo `double` armazena números de ponto flutuante com precisão dupla e é alocado com **8 bytes**. O aumento para 8 bytes permite uma maior precisão e a capacidade de armazenar valores ainda maiores. O `double` é utilizado em cálculos científicos e financeiros, onde é necessária uma maior exatidão.

*Mas e processadores 32bits?*
Quando você usa um tipo double, que é de 64 bits (8 bytes), um processador 32 bits precisa usar mais de um ciclo de CPU para lidar com esses 64 bits, o que pode impactar o desempenho, já que o processador não pode processar diretamente esse tipo de dado em um único ciclo.

A faixa de valores do tipo double **também é afetado** pela forma como ele usa a notação científica para armazenar números, assim como o float.

> Ambos os tipos são armazenados com sinal, expoente e mantissa, de acordo com o padrão IEEE 754.

---

## Booleanos

### `bool` ou `boolean`
- **Tamanho**: 1 byte (em geral)
- **Valores**: 0 (falso) ou 1 (verdadeiro)
- **Representação**: representa verdadeiro ou falso.

O tipo `boolean` é utilizado para armazenar valores lógicos (verdadeiro ou falso) e é alocado com **1 byte**. Embora teoricamente apenas 1 bit fosse necessário, sistemas modernos alocam 1 byte para garantir eficiência no armazenamento e no processamento, além de facilitar a manipulação em arquiteturas de 8 bits ou superiores.
 
A alocação de 1 bit para cada valor booleano poderia poderia causar desperdício de espaço (fragmentação interna). A memória poderia ser alocada de forma ineficiente, com muitos "buracos" ou espaços não utilizados.

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
| `boolean`  | 1                | Verdadeiro ou falso           |