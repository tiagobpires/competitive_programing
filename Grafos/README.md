# Grafos

São um conjunto de vértices(V) e arestas(E), que são pares de vértices.
- self-loop: aresta da forma (u,u)
> Tipos de Grafos:
- Multi-grafo: possui duas arestas iguais.
- Simples: não é um multi-grafo nem possui um self-loop
- Diferecionados: aresta só pode ser percorrida em um sentido (representação por setas)
- Conexo: bidirecional que, para todo vértice u e para todo vértice v pertencentes ao gráfico, existe um caminho de um para o outro.
- Ciclo: quando existe um caminho de um vértice para ele mesmo
- Árvore: conexo e não possuir ciclos.
> Grau de um vértice
- É o número de arestas que são incidentes no vértice
> Vertices vizinhos
- Dados dois vértices(u e v), eles são vizinhos se existir uma aresta (u,v) interligando-os, ou seja, se existir um caminho entre os dois.

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

- DFS (busca em profundidade)

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
    Aplicação: 
    - Saber quantos componentes há no grafo
    ```cpp
    int numero_componentes = 0;
    for (int i = 0; i <= n; i++) {
        if (!vis[i]) {
            numero_componentes++;
            dfs(i);
        }
    }
    ```

- BFS (busca em largura)

    Processo similar ao do DFS, porém, ao invés de funções recursivas, o vizinho é adicionado a uma fila e processado posteriormente.

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
                if(vis[u] == false){
                    // Visito o vizinho
                    vis[u] = true;
                    // Adiciono na fila
                    q.push(u);
                }
            }
        }
    }
    ```