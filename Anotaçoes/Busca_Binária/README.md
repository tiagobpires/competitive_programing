# Busca Binária

- [Explicação](#explicação)

## Explicação

Trata-se de forma de fazer uma busca em um vetor de números **ordenados**

Em cada etapa da busca binária, dividimos o intervalo de respostas possíveis pela metade e verificamos em qual metade o elemento que estamos procurando está e eliminamos a outra metade, pois temos certeza que ela não estará lá.

Para isso, utilizamos duas variáveis, **l (left)** e **r (right)** para indicar o intervalo de posições possíveis. No começo **l = 0** e **r = tamanho do vetor**. A cada etapa, utilizamos uma variável **m (middle) = (l + r) / 2**, e verificamos se o número na posição m é maior ou menor que o número que estamos querendo encontrar. Se for **maior**, não precisamos mais da parte menor que m, então, **l = m + 1**, **caso contrário**, **r = m - 1**.

Com isso, a cada etapa diminuímos o problema pela metade, assim, a complexidade da busca em N itens será **O(log N)**, ao contrário de uma busca checando todos os elementos, que seria O(N)

> Exemplo:

Em um vetor **ordenado** ```v = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]```

```l = 0``` (primeira posição do vetor), ```r = 9``` (ultima posição do vetor).
Na nossa pesquisa, estamos tentando encontrar o número **8**.
A cada etapa, fazemos os passos explicados anteriormente.

1) ```m = (0 + 9) / 2```, ```m = 5```
verificamos a posição 5 no vetor (```v[5] = 6```)
Como 6 é menor que 8, podemos descartar as posições anteriores. Assim, ```l = m + 1```, ```l = 7```.
2) ```m = (7 + 9) / 2```, ```m = 8```
verificamos a posição 8 no vetor (```v[8] = 9```)
Como 9 é maior que 8, podemos descartar as posições posteriores. Assim ```r = m - 1```, ```r = 7```.
3) ```m = (7 + 7) / 2```, ```m = 7```
verificamos a posição 7 no vetor (```v[7] = 8```)

**Encontramos** o nosso valor em apenas 3 etapas, diferente de uma busca verificando cada posição do vetor, 7 etapas.

No C++, já há funções para busca binária, que levam como argumentos ```(começo do vetor, final do vetor, número que estamos procurando)```:
- **binary_search** 

    retorna verdadeiro ou falso

    ex: binary_search(v, v + n, x)
- **lower_bound** 

    retorna o primeiro valor que for maior ou igual ao número procurado

    ex: lower_bound(v, v + n, x)
- **upper_bound** 

    retorna o primeiro valor que for maior do que o número procurado

    ex: upper_bound(v, v + n, x)

- **equal_range**

    retorna os dois ponteiros listados anteriormente

    ex: equal_range(v, v + n, x)

OBS: as funções retornam ponteiros e assumem que o array está ordenado, Se não houver o elemento procurado, o ponteiro aponta para o elemento depois da última posição do array.

> Para sabermos o índice

```cpp
int ind = lower (v, v + n, x) - v;
```

```cpp 
int ind = lower (v.begin(), v.end(), x) - v.begin();
```

> Para encontramos o número de elementos que tem valor igual a x

```cpp
auto s = lower_bound(v.begin(), v.end(), x);
auto e = upper_bound(v.begin(), v.end(), x);
cout << s - e << endl;
```

```cpp
auto range = equal_range(v.begin(), v.end(), x);
cout << range.second - range.first << endl;
```

## Aplicações:

### -  Encontrar determinado número
> Buscar um número em um vetor ordenado
```cpp
vector <int> v;

// n = número que estou procurando
int binarySearch(int n) {
    int l = 0, r = v.size() - 1, m;

    // Enquanto houver um intervalo válido
    while (l <= r) {
        m = (l + r) / 2;
        // Se encontrei o número, retorno a posição dele
        if (v[m] == n)
            return m;
        // Se o número verificado for maior, descarto o intervalo do final
        else if (v[m] > n)
            r = m - 1;
        // Se o número verificado for menor, descarto o intervalo do inicio
        else if (v[m] < n) 
            l = m + 1;
    } 

    // Caso o número não foi encontrado, retorno -1
    return -1;
}
```
### -  "Chutar" a resposta
> Consiste em realizar a busca binária no intervalo possível de respostas e checar se o possível resultado é uma possível resposta ou não

> O código vai depender de cada situação, mas em geral consiste em uma busca binária em que **l = valor mínimo possível** e **r = valor máximo possível** e uma **função** para checar o valor

```cpp
// Checa se possível resposta está de acordo 
// com os requisitos
bool check(int n) {}

int binarySearch () {
    // intervalo possível: 0 a 10^8
    int l = 0, r = 10e8, m, ans = -1;

    while (l <= r) {
        int m = (l + r) / 2;
        // Depende de cada problema
        if (check(m)) {
            ans = m;
            r = m - 1;
        } else {
            l = m + 1;
        }
    } 

    return ans;
}
```

## Exercícios 
- 📗 [Onde está o Mármore?](https://www.urionlinejudge.com.br/judge/pt/problems/view/1025)
- 📗 [Soma das Casas](https://neps.academy/br/exercise/524)
- 📒 [Cápsulas](https://neps.academy/br/exercise/205)
- 📒 [Pão a Metro](https://neps.academy/br/exercise/605)
- 📙 [Cabo de Guerra](https://www.urionlinejudge.com.br/judge/pt/problems/view/1586)
- 📙 [Array Division](https://cses.fi/problemset/task/1085)

