# Grafos

- [Montagem de um Grafo](#montagem-de-um-grafo)
- Flood Fill
    - [DFS](#dfs)
    - [BFS](#bfs)
- [Dijkstra](#dijkstra)

São um conjunto de vértices(V) e arestas(E), que são pares de vértices. Um caminho vai do vértice a até o b, e o comprimento é o número de arestas nele.

> Grau de um vértice
    
É o número de arestas que são incidentes no vértice
> Vertices vizinhos

Dados dois vértices(u e v), eles são vizinhos se existir uma aresta (u,v) interligando-os, ou seja, se existir um caminho entre os dois.


> Self-loop: 

Aresta da forma (u,u), a aresta começa e termina no mesmo vértice.


> Tipos de Grafos:
- Conectado: se tem um caminho entre quaisquer dois vértices
- Multi-grafo: possui duas arestas iguais.
- Simples: não é um multi-grafo nem possui um self-loop
- Direcionados: aresta só pode ser percorrida em um sentido (representação por setas)
- Bipartido: cada vértice pode ser colorido usando 2 cores, e não há dois vértices adjacentes com a mesma cor. Ocorre quando um grafo não contém um ciclo com um número ímpar de arestas
- Conexo: bidirecional que, para todo vértice u e para todo vértice v pertencentes ao gráfico, existe um caminho de um para o outro.
- Ciclo: quando existe um caminho de um vértice para ele mesmo
- Árvore: é um gráfico conectado que consiste de n vértices e n-1 arestas, e tem apenas um caminho entre qualquer dois vértices
- Ponderado: cada aresta possui um peso. O caminho é a soma dos pesos
- Regular: se o grau de cada vértice é uma constante
- Completo: se o grau de cada vértice é n-1, ou seja, o grafo contém todas as possíveis arestas entre os vértices.

## Montagem de um Grafo

-  Matriz de Adjacência

    Cada eixo será um conjunto com todos os vértices, assim, guardaremos as informações de todos os pares de vértices. Ou seja, na posição (i, j) será a informação entre o vértice i e o j

    No armazenamento de tal informação, podemos utilizar 0 para informar que não possui relação, e 1 ou o peso da aresta para informar que possui.

    ```cpp
    // Exemplo com input = Matriz
    // N vértices M arestas
    int n,m; 
    cin >> n >> m;
    // matriz N x N
    int v[maxn][maxn];
    // Lê toda a matriz
    for(int i = 1; i <= n; i++) {
        for(int j=1; j<=n; j++) {
            cin >> v[i][j];
        }
    }
    ```
    OBS: importante para percorrer as matrizes / vizinhos de cada posição

    ```cpp
    int dx[] = {0,0,1,-1};
    int dy[] = {1,-1,0,0};

    // Percorre todos os vizinhos da posição m[x][y]
    for(int i = 0; i < 4; i++){
        // eixo X
        int a = dx[i] + x;
        // eixo Y
        int b = dy[i] + y;
        // m[a][b]
    }
    ```

- Lista de Adjacência

    Utiliza-se um matriz de vectors, ou seja, em cada posição de um vector, há outro vector.

    Assim, para cada vértice, guarda-se as os vizinhos dele.

    ```cpp
    // n vertices e m arestas
    int n, m; 
    cin >> n >> m;

    // Lista de Adjacência
    // vector < pair < vértice, distância > >
    vector< pair<int,int> > g[maxn];

    // Percorre todas as relações(arestas)
    for (int i = 0; i < m; i++){
        // Aresta do vértice U para o V com peso W
        int u, v, w;
        cin >> u >> v >> w;

        // Adiciona em cada lista dos vértices
        // o vértice V será adicionado na lista de U
        // o vertice U será adicionado na lista de V
        g[u].push_back({v,w});
        g[v].push_back({u,w});
    }
    ```

## Busca em Grafos

### Algoritmo Flood Fill    
    
> Preenche um grafo como se fosse um fluxo.

### DFS
(Busca em Profundidade)

Em cada passo, olha-se os vizinhos do vértice V que se está avaliando, e para cada vizinho cuja componente não foi determinada(não visitado), faz-se a sua componente ser v e chama a função recursivamente nesse vértice.

```cpp
// Matriz de Adjacência
vector<int> g[maxn];
// Marca se o vértice foi visitado
bool vis[maxn];

int dfs(int start){
    // Visita o vértice
    vis[start] = true;
    // Percorre os vizinhos 
    for (auto p : g[start]) {
        // Visita os vizinhos não visitados
        if (vis[p] ==  false){
            dfs(p);
        }
    }
}
```

### BFS

(Busca em Largura)

Processo similar ao do DFS, porém, ao invés de funções recursivas, o vizinho é adicionado a uma fila e processado posteriormente. Assim, o BFS visita os vértices em ordem crescente de distância para o inicial.

```cpp
void bfs(int start) {
    queue <int> q;
    // Inicio a fila com o vértice de início
    q.push(start);
    vis[start] = true;
    // Enquanto tiver vertices na fila
    while(!q.empty()){
        // Guarda o vértice
        int v = q.front();
        // Retira-o da fila
        q.pop();
        // Percorre seus vizinhos
        for(auto u: g[v]){
            // se o vizinho não foi visitado
            if(!vis[u]){
                // Visito o vizinho
                vis[u] = true;
                // Adiciono na fila
                q.push(u);
            }
        }
    }
}
```

- Aplicações: 
    - Saber quantos componentes há no grafo
    ```cpp
    int numero_componentes = 0;
    // Percorre todos os vertices
    for (int i = 0; i <= n; i++) {
        // Se ainda nao foi visitado
        if (!vis[i]) {
            numero_componentes++;
            // Visita vizinhos
            dfs(i); //bfs(i)
        }
    }
    ```
    - Encontrar Ciclos

    Encontramos um vértice cujo vizinho (diferente do vértice anterior no caminho atual) já foi visitado.
    
    Outra maneira é calcular o número de vértices e arestas em cada componente. Se contém C vértices, deve conter exatamente c-1 arestas para não ter ciclos, se tem C ou mais arestas, contém um ciclo.

### Caminho Mínimo

### Dijkstra

Encontra o menor caminho desde a origem até todos os vértices do grafo.

Inicialmente, a distância no vértice inicial é zero e a dos outros é infinito. A cada passo, é selecionado o vértice que não foi processado e que a distância é a menor possível. Para eficiência, é utilizado uma fila de prioridade do menor para o maior.

OBS1: Não pode conter arestas de pesos negativos 

OBS2: O peso da aresta é guardado primeiro no pair
```cpp
g[u].push_back({custo, v});
g[v].push_back({custo, u});
```

Implementação:

```cpp
vector <pair <int, int> > g[maxm];
int n, dist[maxm];

void dijkstra(int origem) {
    // Inicializa distancias para infinito
    memset(dist, 63, sizeof dist);
    
    priority_queue < pair<int,int> > pq;
    pq.push({0, origem});
    dist[origem] = 0;

    while (pq.size()) {
        int v = pq.top().second;

        // d negativa para prioridade ser a menor distancia
        int dv = -pq.top().first;
        pq.pop();

        // Se já for a melhor distância
        if (dv > dist[v]) continue;

        for (auto i : g[v]) {
            // Vertice
            int u = i.second;
            // Aresta
            int du = i.first;
            // Se a distância for melhor, atualizo a distancia e adiciono na fila 
            if (dist[u] > dist[v] + du) {
                dist[u] = dist[v] + du;
                pq.push({-dist[u], u});
            }
        }
    }
}
```