# Pilhas

As pilhas são estruturas de dados fundamentais em ciência da computação e programação. Elas seguem o princípio LIFO (Last-In-First-Out), o que significa que o último elemento adicionado à pilha é o primeiro a ser removido. Pilhas são amplamente utilizadas para gerenciar o fluxo de execução de programas, armazenar temporariamente dados e resolver uma variedade de problemas algorítmicos.

#

Algumas das características fundamentais das listas encadeadas são:

* Princípio LIFO (O último elemento adicionado é o primeiro a ser removido.)
* Tamanho Variável
* Uso para Armazenamento Temporário
* Alocação Não Contígua (Assim como as Listas Encadeadas elas podem ser implementadas sem alocação contígua de memória)

## Operações Básicas

Uma pilha suporta várias operações básicas, segue as principais:

1. **push:** Adicionar um elemento ao topo da pilha.
2. **pop:** Remover o elemento do topo da pilha.
3. **top (ou Peek):** Obter o elemento no topo da pilha sem removê-lo.
4. **isEmpty:** Verificar se a pilha está vazia.
5. **size:** Obter o número de elementos na pilha.

## Implementação de Pilhas em C

As pilhas podem ser implementadas em C de várias maneiras, mas a implementação mais comum é usando uma lista encadeada ou um array. Vamos explorar uma implementação básica usando lista encadeada.

### Definindo a Estrutura do Nó:

```c
struct Node {
    int data;
    struct Node* next;
};
```

Aqui definimos a estrutura `Node` que armazena o dado do nó e um ponteiro referente para o próximo nó na pilha.

### Criando a Estrutura da Pilha:

```c
struct Stack {
    struct Node* top;
};
```

A estrutura `Stack` consiste apenas de um ponteiro para o nó no topo da pilha.

### Criando uma Pilha Vazia:

```c
struct Stack* createStack() {
    struct Stack* stack = (struct Stack*)malloc(sizeof(struct Stack));
    stack->top = NULL;
    return stack;
}
```

Esta função aloca memória para uma nova pilha e a inicializa com o topo apontando para NULL, indicando que a pilha está vazia.

### Função para Verificar se a Pilha está Vazia:

```c
int isEmpty(struct Stack* stack) {
    return stack->top == NULL;
}
```

Esta função retorna 1 se a pilha estiver vazia e 0 caso contrário.

### Empilhando um Elemento:

```c
int pop(struct Stack* stack) {
    if (isEmpty(stack)) {
        printf("A pilha está vazia.\n");
        return INT_MIN; // Valor mínimo de um inteiro
    }
    struct Node* temp = stack->top;
    int data = temp->data;
    stack->top = temp->next;
    free(temp);
    return data;
}
```

A função `pop` remove o elemento do topo da pilha, libera a memória associada a ele e retorna o valor do elemento removido. Antes de realizar a operação de desempilhar, ela verifica se a pilha está vazia para evitar erros.

### Função para Obter Elemento do Topo:

```c
int top(struct Stack* stack) {
    if (isEmpty(stack)) {
        printf("A pilha está vazia.\n");
        return INT_MIN;
    }
    return stack->top->data;
}
```

A função `top` retorna o valor do elemento no topo da pilha sem removê-lo. Também verifica se a pilha está vazia antes de acessar o elemento.

### Função para Obter o Tamanho da Pilha:

```c
int size(struct Stack* stack) {
    int count = 0;
    struct Node* current = stack->top;
    while (current != NULL) {
        count++;
        current = current->next;
    }
    return count;
}
```

A função `size` conta o número de elementos na pilha percorrendo todos os nós a partir do topo. Ela retorna o tamanho da pilha.

#

Finalizando, agora podemos entender como as pilhas são uma estrutura de dados poderosa e versátil usadas em programação para resolver uma variedade de problemas. É importante entender como implementar e usar pilhas corretamente, pois elas desempenham um papel fundamental em muitos algoritmos e aplicações.
