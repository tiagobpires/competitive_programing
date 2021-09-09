## Programação Dinâmica

A ideia da Programação Dinâmica é passar por todas as soluções possíveis e evitar recalculos em funções recursivas.

Para isso, salvamos em um vetor (ou matriz caso seja uma função que recebe dois parâmetros) inicializado com -1 (indicando que não calculamos o resultado ainda) todos os resultados que já obtemos até então, e, na chamada da função, verificamos se aquele dado caso já foi calculado. Se sim, apenas o retornamos, caso não, calculamos-o.

Pode ser aplicada se o problema puder ser dividido em subproblemas que podem ser divididos de forma independente, o qual não pode ser cíclico e deve ter independência entre as respostas.

Usos:
- Achar uma solução ótima
- Achar o número de soluções

Template genérico:

```cpp
// guarda os valores já calculados
int dp[maxn];

int func(int x) {
    // Se já calculei, apenas retorno o valor salvo
    if (dp[x] != -1) return d[x];

    // Se não, calculo, guardo o resultado e o retorno
    return dp[x] = //...;
}

int main() {
    // Inicializo os valores com -1
    memset(dp, -1, sizeof dp);

    return 0;
}
```

## Tipos de Abordagem

### Top-Down

A função recursiva chama os casos mais de cima até chegar aos casos base, e só a partir daí ir voltando. 

### Bottom-Up

Primeiro é construído os casos base e a partir deles é criado os casos de cima, até chegarmos ao valor procurado.

## Problemas Clássicos

### Sequência de Fibonacci

Trata-se de uma sequência de números inteiros na qual cada termo subsequente corresponde à soma dos dois anteriores.

Ou seja, Fn = F(n-1) + F(n-2)

Assim, a sequência seria: 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144...

```cpp
int fib(int x) {
    // Casos base da sequência de fibonacci
    if (x == 1 || x == 0) return 1;
    
    // Se já calculei, apenas retorno o valor salvo
    if (dp[x] != -1) return dp[x];

    // Se não, calculo o valor, salvo no vetor dp e o retorno
    return dp[x] = fib(x-1) + fib(x-2); // % (10^9+7)
}

int main() {
    // Inicializo os valores com -1
    memset(dp, -1, sizeof dp);

    // Outra maneira de colocar os casos base é no próprio vetor dp
    // dp[0] = dp[1] = 1;
    
    int n; cin >> n;
    cout << fib(n) << endl;

    return 0;
}
```

### Problema da moeda

