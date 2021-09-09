## Programação Dinâmica

A ideia da Programação Dinâmica é passar por todas as soluções possíveis e evitar recalculos em funções recursivas.

Para isso, salvamos todos os resultados que já obtemos até então, e na chamada da função, verificamos se aquele dado caso já foi calculado. Caso não foi, calculamos-o.

Pode ser aplicada se o problema puder ser dividido em subproblemas que podem ser divididos de forma independente.

programa q vou fazer:
- nao pode ser cíclico
- tenho que ter independência entre as respostas

Usos:
- Achar uma solução ótima
- Achar o número de soluções

Fibonacci
 ```cpp
// guarda os valores já calculados
int dp[maxn]

int fib(int x) {
    if (x == 1 || x == 0) return 1;
    // Se já calculei, apenas retorno o valor salvo
    if (dp[x] != -1) return d[x];

    // Se não, calculo, guardo o resultado e o retorno
    return dp[x] = fib(n-1) + fib(n-2) // % (10^9+7)
}

int main() {
    // Inicializo os valores com -1
    memset(dp, -1, sizeof dp);
    //dp[0] = dp[1] = 1;
}
```

Template genérico:

```cpp
// guarda os valores já calculados
int dp[maxn]

int func(int x) {
    // Se já calculei, apenas retorno o valor salvo
    if (dp[x] != -1) return d[x];

    // Se não, calculo, guardo o resultado e o retorno
    return dp[x] = //...;
}

int main() {
    // Inicializo os valores com -1
    memset(dp, -1, sizeof dp);

}
```
Para uma função que recebe dois parâmetros, utiliza-se uma matriz

## Tipos de Abordagem

### Top-Down

A função recursiva chama os casos mais de cima até chegar aos casos base, e só a partir daí ir voltando. 

### Bottom-Up

Primeiro é construído os casos base e a partir deles é criado os casos de cima, até chegarmos ao valor procurado.

## Problemas Clássicos

### Problema da moeda
