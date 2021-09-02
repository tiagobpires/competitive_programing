# Soma de Prefixos

- [👨‍🏫 Explicação](#explicação)
- [🤸 Aplicações](#aplicações)
- [🏋️ Exercícios](#exercícios)

## Explicação

O array de soma de prefixos trata-se de um array que, na posição **i**, guarda a soma dos elementos até a **i-ésima** posição.

> Exemplo:

Seja v um vetor:

```v = [1, 2, 3, 4, 5, 6];```

A array de soma de prefixos seria:

```s = [1, 3, 6, 10, 15, 21];```

- A posição 1 é a soma dos elementos até a posição 1 (1)
- A posição 2 é a soma dos elmetnos até a posição 2 (1 + 2 = 3)
- A posição 3 é a soma dos elmetnos até a posição 3 (1 + 2 + 3 = 6) ...

## Aplicações

> Soma de um subarray

Uma das formas de calcualr a soma de um subarray é percorrê-lo e somar seus elementos, porém, isso tem complexidade **O(n)**.

Com o array de prefixos podemos obter esse valor em **O(1)**, pois a soma de um subarray de **A** até **B** será a soma dos elementos até **B** menos a soma dos elementos anteriores a **A**

Exemplo:

```cpp
v = [1, 2, 3, 4, 5, 6];
s = [1, 3, 6, 10, 15, 21]; // array de prefixos
```

OBS: Considerando o valor com posições de 1 a n

Para calcularmos a soma dos valores da posição 3 a 5, ou seja, o subarray
```[3,4,5]```, só precisamos da soma dos valores até o 5º item, 15, e a soma do 2º item (anterior a posição 3), 3. Subtraindo-os:

```15 - 3 = 12```

Código:
> Inicializar array

```cpp
// Array de prefixos, das posições 1 a n
int s[n+1];

// Inicializa com 0, pois para guardar a soma pegaremos o valor anterior
s[0] = 0;
int aux;

for (int i = 1; i <= n; i++) {
    cin >> aux;
    // guarda a soma anterior adicionado com o valor recebido
    s[i] = aux + s[i-1];
}
```

> Calcular soma de subarray

```cpp
// Intervalo do subarray
int a, b;
cin >> a >> b;

cout << s[b] - s[a-1] << endl;
```

## Exercícios