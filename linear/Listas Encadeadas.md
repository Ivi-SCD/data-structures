## Listas Encadeadas

Uma lista encadeada é uma estrutura de dados que **consiste em uma coleção de elementos** chamados nós, onde cada nó contém dois campos principais: um campo de dados que armazena o valor do elemento e um campo de ponteiro que aponta para o próximo nó na lista. Essa estrutura permite a c**onstrução de listas de elementos de maneira dinâmica**, ou seja, você pode adicionar e remover elementos facilmente.

#

Algumas das características fundamentais das listas encadeadas são:

* Estruturas Dinâmicas (Crescimento ou encolhimento conforme o necessário)
* Elementos - Nós (Elementos individuais são chamados de nós)
* Conexão por Ponteiros (Os nós são conectados por ponteiros)
* Inserção e Remoção eficiente
* Acesso Sequencial (Precisa percorrer a lista do inicio ao fim para obter um elemento específico)
* Tamanho Variável
* Alocação Não Contígua (Ao contrário dos arrays, as listas encadeadas não exigem alocação contígua de memória para armazenar elementos,)


### Nó de uma Lista Encadeada:

```c
struct Node {
    int data;
    struct Node* next;
}
```

Esse código define uma Struct chamada de `Node` com um atributo onde armazenará o dado referente ao nó e um ponteiro para o próximo nó. 

### Criação de uma Lista Encadeada:

Para criar listas encadeadas, você precisa definir um ponteiro para o nó inicial(cabeça da lista). A cabeça da lista é definida como NULL para indicar uma lista vazia.

```c
struct Node* head = NULL;
```

Esse código cria uma variável chamada `head` que é um ponteiro para uma estrutura `Node` (provavelmente definida anteriormente no código), e inicializa esse ponteiro como `NULL`. O objetivo principal desse código é criar uma lista encadeada vazia.


### Inserção de Elementos:

Para adicionar um elemento à lista encadeada, você aloca dinamicamente um novo nó, atribui o valor desejado ao campo de dados e ajusta os ponteiros para que o novo nó aponte para o próximo nó da lista.

```c
struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
newNode->data = 42;          // Valor do elemento
newNode->next = head;       // O próximo nó é a antiga cabeça da lista
head = newNode;             // Atualiza a cabeça para o novo nó
```

Esse código cria um novo nó e o adiciona ao início de uma lista encadeada. Após a execução, um novo nó é criado, preenchido com o valor 42 e inserido no início da lista encadeada. Isso é comum em listas encadeadas, onde a inserção no início é uma operação eficiente, e a cabeça da lista é atualizada para refletir a mudança na estrutura da lista.

### Remoção de Elementos:

Para remover um elemento, você precisa ajustar os ponteiros para que o nó anterior aponte para o nó seguinte, e então liberar a memória do nó que está sendo removido.

```c
struct Node* temp = head;
head = head->next;       // Move a cabeça para o próximo nó
free(temp);              // Libera a memória do nó removido
```

Esse código realiza uma operação de remoção do primeiro nó de uma lista encadeada. Ele atualiza o ponteiro `head` para apontar para o próximo nó na lista, mantém temporariamente uma referência ao nó removido em `temp` e, em seguida, libera a memória alocada para o nó removido usando a função `free`.

### Transversing (Percorrendo) a Lista:

Você pode percorrer uma lista encadeada usando um loop, começando pela cabeça e seguindo os ponteiros `next` até que o ponteiro seja NULL.

```c
struct Node* current = head;
while (current != NULL) {
    printf("%d ", current->data);  // Imprime o valor do nó
    current = current->next;      // Move para o próximo nó
}
```

 Esse código percorre uma lista encadeada a partir do nó inicial (`head`) e imprime os valores dos nós um por um. Ele utiliza um loop `while` para continuar o percurso até que o final da lista seja alcançado (quando `current` se torna `NULL`). Durante cada iteração do loop, o valor do nó atual é impresso, e o ponteiro `current` é atualizado para apontar para o próximo nó na lista, permitindo assim a iteração pela lista inteira e a impressão de todos os valores dos nós.

 #

 Finalizando, as listas encadeadas são uma estrutura de dados fundamental na programação. Elas oferecem flexibilidade para adicionar e remover elementos dinamicamente, tornando-as valiosas em muitas aplicações. No entanto, é importante entender suas vantagens e desvantagens para escolher a estrutura de dados adequada para um problema específico