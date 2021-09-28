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
