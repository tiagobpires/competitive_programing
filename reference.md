## Sumário
- [Template](#template)
- Grafos
    - [DFS](#dfs)
    - [BFS](#bfs)
    - [Dijkstra](#dijkstra)
- [Busca Binária](#busca-binária)
## Template
```cpp
typedef long long ll;
typedef pair<int, int> ii; 
typedef vector<ii> vii;
typedef vector<int> vi;
typedef push_back pb;
#define INF 1000000000

int main() {
    ios_base::sync_with_stdio(false);cin.tie(NULL);


    return 0;
}
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

## Busca Binária
```cpp
bool check (int x) {

}

vector <int> v;

int binarySearch(int n) {
    int l = 0, r = v.size() - 1, m;

    while (l <= r) {
        m = (l + r) / 2;
        if (check(m))
            return m;
        else if (v[m] > n)
            r = m - 1;
        else if (v[m] < n) 
            l = m + 1;
    } 

    return -1;
}
```