# Vetor Dinâmico

É um vetor que aumenta de tamanho de acordo com a necessidade do programador. Ele inicia-se com tamanho constase (1), e quando sua capacidade é exedida, ele aumenta de tamanho, multiplicando-o por um fator de expansão k, que normalmente é 2, ou seja, o vetor dinâmico dobra de tamanho quando a capacidade é exedida.

Podemos acessar qualquer elemento em tempo O(1), pois o vetor dinâmico sempre tenta armazenar sequencialmente na memória, como um vetor normal.

> Declaração
```cpp
vector <int> v;
v = {1, 2, 3};
```

> Operações

- Acessar algum elemento (igual ao vetor) O(1)
```cpp
cout << v[1] << endl
```

- Retornar ponteiro para o primeiro elemento do vector O(1)
```cpp
auto ini = v.begin();
cout << *ini << endl;
```

- Retornar uma referência (ponteiro) para a memória que indica o final do vector O(1)
```cpp
auto fim = v.end();
// diminui uma posição para apontar para o fim
cout << *(fim - 1) << endl;
```

- Tamanho do vetor  O(1)
```cpp
cout << v.size() << endl;
```

- Redimensionar tamanho do vector O(n)
    Parâmetros:
    - Tamanho que desejamos redefinir
    - Valor que será setado nas novas posições (default = 0)
    Possibilidades de uso:
    - Se o novo tamanho for menor que o atual, as posições extras são apagadas
    - Se o novo tamanho for maior que o atual, as novas posições são setadas com o valor fornecido.
```cpp
v.resize(5,1);
```

- Apagar os elementos do vector O(n)
```cpp
v.clear();
```

- Inserir um elemento no final do vector O(1)
```cpp
v.push_back(2);
```
- Apagar o elemento do final do vector O(1)
```cpp
v.pop_back();
```

- Inserir um elemento em qualquer posição do vector O(n)
  
    Parâmetros:
    - Ponteiro para a posição onde será inserido o elemento
    - O elemento
```cpp
// Inserindo na segunda posição
pos = 2;
v.insert(v.begin() + pos, 3);
```
- Apagar um elemento em qualquer posição do vector O(n)
    
    Parâmetros:
    - Ponteiro para a posição onde será apagado o elemento
    - O elemento
```cpp
// Apagando o elemento na segunda posição
pos = 2;
v.erase(v.begin() + pos, 3);
```


# Fila

## Explicação
É uma estrutura do tipo FIFO (first-in first-out), onde o primeiro elemento a ser inserido na fila é o primeiro a sair, funcionando, por exemplo, como uma fila de banco onde quem chega primeiro é atendidbo primeiro.

Aplicações reais:
- Fila de atendimento (banco, supermercado, para utilizar algum recurso, etc)

> Declaração
```cpp
queue <int> q;
```

> Operações
- Inserir elemento no final da fila

    OBS: a fila mantém um ponteiro para o último elemento para a inserção ser em tempo constante
```cpp
q.push(1);
```

- Retornar o elemento da frente da fila
```cpp
cout << q.front() << endl;
```

- Remover o elemento da frente da fila 
```cpp
q.pop();
```

- Tamanho da fila
```cpp
cout << q.size() << endl;
```

# Pilha
É uma estrutura do tipo LIFO (last-in last-out), onde o primeiro elemento a sair é o último a entrar. Funciona como uma pilha de roupas, onde podemos pegar a roupa de cima, e quando novas roupas forem adicionadas, ou empurradas, serão postas em cima também.

Aplicações:
- Gerenciamento de memória
- Funções (principalmente recursivas)
  
> Declaração
```cpp
stack <int> p;
```

> Operações
- Inserir elemento na pilha
```cpp
p.push(1);
```

- Retornar o elemento no topo da pilha
```cpp
cout << p.top() << endl;
```

- Remover o elemento no top da pilha
```cpp
p.pop();
```

- Tamanho da pilha
```cpp
cout << p.size() << endl;
```

# Fila de prioridade
Mantém na primeira posição sempre o maior elemento.

> Declaração
Parâmetros:
- Tipo de dado que será armazenado
- O container onde serão alocados os elementos (default: vector)
- A função de comparação (default: topo é o maior elemento)
```cpp
priority_queue <int, vector <int>, greater <int>> pq;
```
OBS: Adicionar o negativo do elemento para o topo ser o menor elemento

> Operações
- Inserir elemento no final da fila de prioridade O(log n)
```cpp
pq.push(1);
```

- Remover o elemento no topo da fila de prioridade O(log n)
```cpp
cout << pq.pop() << endl;
```

- Retornar o elemento no topo da fila de prioridade O(1)
```cpp
cout << pq.top() << endl;
```

- Tamanho da fila de prioridade
```cpp
cout << pq.size() << endl;
```