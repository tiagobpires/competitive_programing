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

- Top Down
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
- Bottom Up
```cpp
int fib(n) {
    int f[maxn];
    f[0] = 0, f[1] = 1;
    for (int i = 2; i <= n; i++) {
        f[i] = f[i - 1] + f[i - 2];
    }
    return f[n];
}
```

### [Problema da moeda](https://br.spoj.com/problems/MOEDAS/)
> Dado um vetor de moedas, descobrir qual a solução ótima(menor número de moedas necessárias) para obter um determinado valor 

> Cada moeda pode ser utilizada várias vezes

```cpp
int dp[maxn], n, m, moedas[maxn];

int troco(int val) {
    // Ja consegui trocar o valor
    if (val == 0) return 0;
    // Ja calculei subproblema
    if (dp[val] != -1) return dp[val];

    int aux = 1e9;
    // Passar por todas as moedas
    for (int i = 0; i < n; i++) {
        // Se eu puder utilizar essa moeda
        if (moedas[i] <= val) {
            // Minímo entre ele e a situação de eu usar a moeda  
            aux = min(aux, 1 + troco(val-moedas[i]));
        }
    }
    return dp[val] = aux;
}

int main() {
    // m = valor que quero trocar, n = numero de moedas
    cin >> m >> n;

    for (int i = 0; i < n; i++) {
        cin >> moedas[i];
    }

    // Inicio vetor dp em -1
    memset(dp, -1, sizeof dp);
            
    int resp = troco(m);
    if (resp == 1e9) 
        cout << "Impossivel" << endl;
    else   
        cout << resp << endl;  

    return 0;
}
```

## [Problema do Troco](https://br.spoj.com/problems/TROCO13/)
> Saber se é possível ou não obter um troco com as moedas que tem

> Cada moeda de determinada posição do vetor podem ser utilizadas apenas uma vez

```cpp
int dp[maxn][100010], n, m, moedas[maxn];
bool flag = false;

void troco(int idm, int soma) {   
    // Consegui uma solução
    if (soma == m) flag = true;
    if (flag) return;

    // Solução não é possível
    if (idm >= n || soma > m) return;

    // Já foi "visitado"
    if (dp[idm][soma] != -1) return;

    // Marco como já "visitado"
    dp[idm][soma] = 1;

    // Utilizando a moeda
    troco(idm+1, soma + moedas[idm]);

    // Não utilizando a moeda
    troco(idm+1, soma); 
}
```
