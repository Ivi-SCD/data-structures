## Filas 

As filas são estruturas de dados lineares que seguem o **princípio FIFO (First-In-First-Out), ou seja, o primeiro elemento inserido na fila é o primeiro a ser removido**. As filas são amplamente utilizadas em programação para gerenciar dados de forma ordenada e eficiente. Elas são especialmente úteis quando se deseja manter a ordem de chegada dos elementos.

#

Algumas das características fundamentais das Filas são:

* Princípio FIFO (Primeiro elemento adicionado será o primeiro a ser removido).
* Uso Comum para Gerenciamento de Tarefas (Frequentemente usada em S.O's para o gerenciamento de tarefas)
* Espera em Linha (Várias tarefas ou processos precisam esperar sua vez para serem executados)
* Tamanho Variável
* Alocação Não Contígua

## Operações Básicas

Uma fila suporta várias operações básicas, segue as principais:

1. **enqueue:** Adicionar um elemento na frente da fila.
2. **dequeue:** Remover o elemento na frente da fila.
3. **front** Obter o elemento no topo da fila sem removê-lo.
4. **isEmpty:** Verificar se a fila está vazia.
5. **size:** Obter o número de elementos na fila.

## Implementação de Filas em C

As filas podem ser implementadas em C usando um array ou uma lista encadeada. Vamos explorar uma implementação básica usando uma lista encadeada.

### Definindo a Estrutura do Nó:

```c
struct Node {
    int data;
    struct Node* next;
};
```

Aqui, definimos uma estrutura `Node`` que armazena o dado do nó e um ponteiro para o próximo nó na fila.

### Criando a Estrutura de Fila:

```c
struct Queue {
    struct Node* front;
    struct Node* rear;
};
```

A estrutura `Queue` consiste de dois ponteiros: `front` (frente da fila) e `rear` (final da fila).

### Criando uma Fila Vazia: 

```c
struct Queue* createQueue() {
    struct Queue* queue = (struct Queue*)malloc(sizeof(struct Queue));
    queue->front = queue->rear = NULL;
    return queue;
}
```

Esta função aloca memória para uma nova fila e a inicializa com os ponteiros `front` e `rear` apontando para NULL, indicando que a fila está vazia.

### Função para Verificar se a Fila está Vazia:

```c
int isEmpty(struct Queue* queue) {
    return queue->front == NULL;
}
```

Esta função retorna 1 se a fila estiver vazia e 0 caso contrário.

### Função para Enfileirar um Elemento: 

```c
void enqueue(struct Queue* queue, int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;

    if (isEmpty(queue)) {
        queue->front = queue->rear = newNode;
    } else {
        queue->rear->next = newNode;
        queue->rear = newNode;
    }
}
```

A função `enqueue` cria um novo nó com o dado especificado e o adiciona ao final da fila. Se a fila estiver vazia, ela atualiza tanto `front` quanto `rear` para apontar para o novo nó.

### Função para Desenfileirar um Elemento:

```c
int dequeue(struct Queue* queue) {
    if (isEmpty(queue)) {
        printf("A fila está vazia.\n");
        return INT_MIN; // Valor mínimo de um inteiro
    }
    struct Node* temp = queue->front;
    int data = temp->data;

    if (queue->front == queue->rear) {
        queue->front = queue->rear = NULL;
    } else {
        queue->front = queue->front->next;
    }

    free(temp);
    return data;
}
```

A função `dequeue` remove o elemento da frente da fila, atualiza o ponteiro `front` e retorna o valor do elemento removido. Ela verifica se a fila está vazia antes de realizar a operação de desenfileirar.

### Função para Obter o Tamanho da Fila:

```c
int size(struct Queue* queue) {
    int count = 0;
    struct Node* current = queue->front;
    while (current != NULL) {
        count++;
        current = current->next;
    }
    return count;
}

A função `size` conta o número de elementos na fila percorrendo todos os nós a partir da frente. Ela retorna o tamanho da fila.

```

### Função para obter o elemento da frente:

```c
int front(struct Queue* queue) {
    if (isEmpty(queue)) {
        printf("A fila está vazia.\n");
        return INT_MIN;
    }
    return queue->front->data;
}
```

A função `front` retorna o valor do elemento na frente da fila sem removê-lo. Também verifica se a fila está vazia antes de acessar o elemento.

#

Compreendemos então a importância e versatilidade  das listas, as quais desempenham um papel fundamental em muitas aplicações de programação. Elas são especialmente úteis quando se precisa manter a ordem de chegada dos elementos e são amplamente utilizadas em sistemas operacionais, processamento de tarefas em segundo plano, algoritmos de busca e etc.