## Template
```cpp
typedef long long ll;
typedef pair<int, int> ii; 
typedef vector<ii> vii;
typedef vector<int> vi;
typedef push_back pb;
#define INF 1000000000
```

## DFS
```cpp
vector<int> g[maxn];
bool vis[maxn];

int dfs(int start){
    vis[start] = true;
    for (auto p : g[start]) {
        if (vis[p] ==  false) {
            dfs(p);
        }
    }
}
```

## BFS
```cpp
void bfs(int start) {
    queue <int> q;
    q.push(start);
    vis[start] = true;
    while(!q.empty()){
        int v = q.front();
        q.pop();
        for(auto u: g[v]){
            if(!vis[u]){
                vis[u] = true;
                q.push(u);
            }
        }
    }
}
```

## Dijkstra

```cpp
vector <pair <int, int> > g[maxm];
int n, dist[maxm];

void dijkstra(int origem) {
    memset(dist, 63, sizeof dist);
    
    priority_queue < pair<int,int> > pq;
    pq.push({0, origem});
    dist[origem] = 0;

    while (pq.size()) {
        int v = pq.top().second;

        int dv = -pq.top().first;
        pq.pop();

        if (dv > dist[v]) continue;

        for (auto i : g[v]) {
            int u = i.second;
            int du = i.first;
            if (dist[u] > dist[v] + du) {
                dist[u] = dist[v] + du;
                pq.push({-dist[u], u});
            }
        }
    }
}
```