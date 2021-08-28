# Busca Binária

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

OBS: as funções retornam ponteiros

> Para sabermos o índice

```cpp int ind = lower (v, v + n, x) - v;```


```cpp int ind = lower (v.begin(), v.end(), x) - v.begin();```

## Código:

```cpp

```
