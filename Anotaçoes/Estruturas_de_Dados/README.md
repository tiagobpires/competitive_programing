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