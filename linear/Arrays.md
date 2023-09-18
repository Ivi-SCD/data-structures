## Arrays

#

Arrays são uma das **estruturas de dados mais fundamentais e amplamente utilizadas na programação**. 
Eles representam c**oleções ordenadas de elementos do mesmo tipo, armazenados em memória de forma 
contígua e acessíveis por meio de um índice**. 

#

Irei passar por alguns conceitos teóricos sobre o uso de Arrays e depois irei apresentar alguns exemplos 
utilizando a linguagem C!

#

Os arrays possuem algumas características fundamentais como:

* Coleção de Dados Homogêneas (Mesmo Tipo)
* Índices e Acessos (Iniciando a partir do 0)
* Tamanho Fixo (Uma vez definido não pode ser alterado)
* Memória Contígua (O Sistema Operacional e o Compilador conseguem calcular a localização de cada elemento 
* com base no índice)
* Eficiência no Acesso

Sabendo dessas principais características entendemos que os arrays são uma estrutura de dados simples porém 
poderosa que pode oferecer um acesso eficiente e indexado a elementos de mesmo tipo. Eles são fundamentais 
para a programação e são a base para muitas outras estruturas de dados. No entanto, é importante estar ciente 
de suas limitações e considerar outras estruturas de dados quando necessário.

### Declaração de Arrays

Para declarar um array em C, você precisa **especificar o tipo de dados dos elementos e o tamanho do array**. 
A sintaxe básica é a seguinte:

```c
tipo_de_dados nome_do_array[tamanho];
``````

Aqui estão alguns exemplos de declaração de arrays:

```c
int numeros[5];         // Um array de inteiros com 5 elementos
char caracteres[10];    // Um array de caracteres com 10 elementos
float valores[3];       // Um array de valores de ponto flutuante com 3 elementos
```

### Inicialização de Arrays:

Você pode inicializar um array durante a declaração ou posteriormente, usando índices. Veja como inicializar 
arrays:

```c
int numeros[5] = {1, 2, 3, 4, 5};        // Inicialização durante a declaração
char vogais[] = {'a', 'e', 'i', 'o', 'u'}; // O tamanho é inferido automaticamente
```

### Acesso a Elementos de um Array:

Os elementos de um array são acessados usando seus índices, que começam em 0. Por exemplo, para acessar o 
primeiro elemento de um array, você usa o índice 0.

```c
int primeiro_numero = numeros[0];   // Acessando o primeiro elemento
char segunda_vogal = vogais[1];     // Acessando o segundo elemento
```

### Manipulação de Arrays:

Você pode manipular arrays em C usando loops, como o `for`, para percorrer todos os elementos do array 
e realizar operações. Aqui está um exemplo de como preencher e imprimir os elementos de um array de inteiros:

```c
#include <stdio.h>

int main() {
    int numeros[5]; // Declarando um array de inteiros com 5 elementos

    // Preenchendo o array com valores
    for (int i = 0; i < 5; i++) {
        numeros[i] = i + 1;
    }

    // Imprimindo os valores do array
    printf("Valores do array: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", numeros[i]);
    }
    printf("\n");

    return 0;
}
```

Este programa preenche um array de inteiros com os valores de 1 a 5 e, em seguida, imprime esses valores
 na tela.

### Tamanho dos Arrays:

Em C, não existe uma função embutida para obter o tamanho de um array. Você precisa controlar o tamanho 
do array manualmente ou usar uma variável constante para armazenar o tamanho, como no exemplo anterior.

```c
int tamanho = sizeof(numeros) / sizeof(numeros[0]);
```

Isso divide o tamanho total do array pelo tamanho de um único elemento, dando o número de elementos no 
array.

Para melhor compreensão do que está acontecendo:

1. `sizeof(numeros)` retorna o tamanho total em bytes do array `numeros`. Neste caso, se `int` tiver 4 
bytes, isso retornará 5 * 4 = 20 bytes (supondo que int tenha 4 bytes).

2. `sizeof(numeros[0])` retorna o tamanho em bytes de um único elemento do array. Neste caso, também 
será 4 bytes.

3. Dividir o tamanho total do array pelo tamanho de um único elemento (`20 / 4`) resulta no tamanho do 
array, que é 5.


Portanto, a variável `tamanho` agora conterá o valor 5, que é o tamanho do array `numeros`.

Essa técnica funciona, mas pode ser propensa a erros se você esquecer de atualizar o tamanho quando o 
array for alterado. Também não funciona bem com arrays que foram passados como argumentos de função, 
pois eles perdem suas informações de tamanho no processo.

#

E por fim esses foram os conceitos básicos relacionados a arrays em C. Eles são uma estrutura de dados 
simples, porém poderosa, frequentemente usada em programação para armazenar e manipular conjuntos de dados, 
além de também ser usado em conjunto para a explicação de outras estruturas de dados mais complexas.




