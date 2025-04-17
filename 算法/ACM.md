# ACM算法

`E06 线性DP 最长公共子串`

## 一、基础算法

### 快速幂
```c++
// 计算 a^b % mod
long long qpow(long long a, long long b, long long mod) {
    long long res = 1;
    a %= mod;  // 先对底数取模，防止溢出

    while (b) {
        if (b & 1) res = res * a % mod;  // 如果当前位是1，则乘上a
        a = a * a % mod;  // a 每轮平方
        b >>= 1;  // b 右移一位，相当于除以2
    }

    return res;
}
```

对b进行二进制拆分



### 搜索

DFS、BFS
记忆化搜索：对递归树做了剪枝，搜索过的子树不再重复搜索，直接返回存储值


#### DFS
```c++
vector<int> g[N];
bool vis[N]; // 是否访问过

void dfs(int u) {
    vis[u] = true;

    for (int v : g[u]) {
        if (!vis[v]) {
            dfs(v);
        }
    }
}
```

深度优先搜索



#### BFS
```c++
vector<int> g[N];
bool vis[N]; // 是否访问过
int dist[N]; // 起点到每个点的最短距离

void bfs(int start) {
    memset(vis, 0, sizeof vis);
    memset(dist, -1, sizeof dist);

    queue<int> q;
    q.push(start);
    vis[start] = true;
    dist[start] = 0;

    while (!q.empty()) {
        int u = q.front(); q.pop();

        for (int v : g[u]) {
            if (!vis[v]) {
                vis[v] = true;
                dist[v] = dist[u] + 1;
                q.push(v);
            }
        }
    }
}
```

宽度优先搜索




### 二分查找
```c++
//在升序序列中二分查找某数 x 的位置，二分区间为 [left,right]，如果不存在，返回-1
int arr[N];
int binarySearch(int left, int right, int v) {
    while (left <= right) {
        int mid = (left + right) >> 1;
        if (arr[mid] == v) return mid;
        else if (arr[mid] < v) left = mid + 1;
        else right = mid -1;
    }
    return -1;
}
```




## 二、数据结构


### 树


#### 树的重心



### 二叉树

二叉树先序遍历：`中 -> 左 -> 右`

二叉树中序遍历：`左 -> 中 -> 右`，一个节点在访问时它的左子树一定访问完了

二叉树后序遍历：`左 -> 右 -> 中`，一个节点在访问时它的左右子树一定都访问完了

![二叉树遍历](../assets/二叉树遍历.png)


### ST表
```c++
// 计算1~n的log2值
for (int i = 2; i <= n; ++i)
    Log2[i] = Log2[i / 2] + 1;

// f[a][b]，a存储位置索引(1~n)，b存储2进制长度，f[a][b]存储a~a+2^b-1范围的最值
int f[MAXN][21]; // 第二维的大小根据数据范围决定，不小于log(MAXN)
for (int i = 1; i <= n; ++i)
    f[i][0] = read(); // 读入数据
for (int i = 1; i <= 20; ++i)
    for (int j = 1; j + (1 << i) - 1 <= n; ++j)
        f[j][i] = max(f[j][i - 1], f[j + (1 << (i - 1))][i - 1]);

// 初始化、计算
for (int i = 0; i < n; ++i) {
    int l = read(), r = read();
    // 区间长度所对应的log2值(不超过长度)
    int s = Log2[r - l + 1];
    // 查询、左右边界2进制长度查询
    printf("%d\n", max(f[l][s], f[r - (1 << s) + 1][s]));
}
```

ST 表（Sparse Table，稀疏表）是用于解决 可重复贡献问题 的数据结构
![ST表](../assets/st表.png)
![ST表存储格式](../assets/ST表存储格式.png)   

目标：
- 区间最值





预处理，倍增



### 单调栈

- 下一个更高的数据在哪？
- 小于(大于)该值的数据都出栈
- 栈中只存下标



### 单调队列

- 滑动窗口最值



### 并查集
```c++
/**
    朴素并查集
*/ 
// p[]存储每个点的祖宗节点，s[]只有祖宗节点的有意义，表示祖宗节点所在集合中的点的数量
int p[N], s[N];

// 返回x的祖宗节点
int find(int x) {
    if (p[x] != x) p[x] = find(p[x]);
    return p[x];
}

// 判断是否在同一个集合
bool same(int x, int y) {
    return find(x) == find(y);
} 

// 集合合并
void merge(int x, int y) {
    p[find(x)] = find(y);
    s[p[y]] += s[p[x]];
}

// 初始化并查集，编号 1~n
for (int i = 1; i <= n; i++) {
    p[i] = i;
    s[i] = 1;
}
```

目标：
1.将两个集合合并
2.询问两个元素是否在一个集合中
时间复杂度基本上是O(1);

原理：
1.每一个集合用树来维护，每一个集合的编号是根节点，查找是去看他爸爸是不是根节点，不是再向上，所以每一个节点都要存储他的父节点，p[x]就是x的父节点
2.判断根节点 if（p[x]==x）;
3.集合合并，直接让其中一个变成儿子（子节点）,px是x的编号，py是y的编号，插入p[x]=y;
4.求x的集合编号，while(p[x]!=x)x=p[x],因为他的循环次数取决于树的高度，时间复杂度会很高，所以将其优化为：把所有子节点都指向根节点：（路径压缩）；


### 树状数组
```c++
// 编号1~n
int[N] tree;

// 二进制末尾1
int lowbit(int x) {
    return x & (-x);
}

// 当前更新，更新父节点链，保证树上父节点链上的值为前缀和值
void update(int i, int v) {
    while (i <= n) {
        tree[i] += v;
        i += lowbit(i);
    }
}

// 区间查询，二进制1统计
int query(int i) {
    int sum = 0;
    while (i > 0) {
        sum += tree[i];
        i -= lowbit(i);
    }
    return sum;
}
```

目标：
1.单点更新
2.区间查询


前缀和
基于二进制位为1的前缀和统计
每个节点的编号加上二进制位的末尾(右侧)1，就可以得到父节点的编号(反过来同理获取子节点)


![树状数组结构](../assets/树状数组结构.png)


### 线段树
```c++
// 线段树要开N的4倍空间
struct node {
    int l, r;
    // sum区间和、lazy子树区间更新延迟标记
    long long sum, lazy; 
} tree[N * 4];

// 原始数据
int w[N];

// 向上更新父节点
void pushup(int p) {
    tree[p].sum = tree[p << 1].sum + tree[p << 1 | 1].sum;
}

// 向下更新子树，清空当前节点的lazy标记
void pushdown(int p) {
    node l = tree[p << 1];
    node r = tree[p << 1 | 1];
    if (tree[p].lazy) {
        l.lazy += tree[p].lazy;
        r.lazy += tree[p].lazy;
        l.sum += (long long)(l.r - l.l + 1) * tree[p].lazy;
        r.sum += (long long)(r.r - r.l + 1) * tree[p].lazy;
        tree[p].lazy = 0;
    }
}

// 区间[1~n]，p当前节点、l当前节点左边界、r当前节点右边界
void build(int p, int l, int r) {
    tree[p].l = l;
    tree[p].r = r;
    tree[p].lazy = 0;
    if (l == r) {
        tree[p].sum = w[p];
        return;
    }
    int mid = (l + r) >> 1;
    build(p << 1, l, mid);
    build(p << 1 | 1, mid + 1, r);
    // 向上更新父节点
    pushup(p);
}

// 区间更新、p当前节点、l更新左边界(不变)、r更新右边界(不变)，v更新值
void update(int p, int l, int r, int v) {
    // 完全覆盖当前节点
    if (tree[p].l >= l && tree[p].r <= r) {
        tree[p].sum += (long long)(tree[p].r - tree[p].l + 1) * v;
        tree[p].lazy += v;
        return;
    }
    pushdown(p);
    int mid = (tree[p].l + tree[p].r) >> 1;
    // 左节点重叠
    if (l <= mid) update(p << 1, l, r);
    // 右节点重叠
    if (r > mid) update(p << 1 | 1, l, r);
    pushup(p);
}

// 区间查询、p当前节点、l查询左边界(不变)、r查询右边界(不变)
long long query(int p, int l, int r){
    // 完全覆盖当前节点，更新过程中能保证父节点lazy被清除了
    if (tree[p].l >= l && tree[p].r <= r) return tree[p].sum;
    // 向下更新lazy
    pushdown(p);
    int mid = (tree[p].l + tree[p].r) >> 1;
    long long sum = 0;
    // 左节点重叠
    if (l <= mid) sum += query(p << 1, l, r);
    // 右节点重叠
    if (r > mid) sum += query(p << 1 | 1, l, r);
    return sum;
}

// 初始化
build(1, 1, n);
```

目标：
1.区间查询
2.区间更新


父子关系：
父节点 x/2下取整 等价于 x >> 1;
左儿子 2x 等价于 x << 1;
右儿子 2x + 1 等价于 x << 1 | 1



## 三、字符串


### 哈希Hash
```c++
// 一维字符串hash
const int M=233;//是我们自己选择的进制数，一般可以选233,2333,10007等质数
const int mod=1e9+7;//一般选一个比较大的质数
long long get(string s)//获取字符串对应的哈希值
{
	long long sum=0;
	for(int i=0;i<s.size();i++) sum=(sum*M+s[i]-'a')%mod;
	return sum;
}

// 一维hash，使用unsigned long long 溢出
typedef unsigned long long int ull;
const int N=1e5+10;
const int M=233;
ull h[N],base[N]; // h[i]记录1~i的前缀hash，// base[i]=M^i
ull query(int l,int r)//获取字符串[l,r]的哈希值
{
    return h[r]-h[l-1]*base[r-l+1];
}
//初始化哈希，1~n
void init(string s)
{
    int n=s.size();
    s="0"+s;//让其下标从1开始
    base[0]=1;
    for(int i=1;i<=n;i++)
    {
        h[i]=h[i-1]*M+s[i];
        base[i]=base[i-1]*M;
    }
}
//求[l1,r1],[l2,r2]子串并的哈希值
ull merge(int l1, int r1, int l2, int r2)
{
    return query(l1, r1) * base[r2 - l2 + 1] + query(l2, r2);
}

// 二维矩阵hash
typedef long long int ll;
const int N=1010;
ll h[N][N],base1[N],base2[N];
int a[N][N],n,m;
//构建，先构建行前缀hash（左到右，base1）,在依靠行前缀hash构造列矩阵hash（上到下）
void init()
{
    base1[0]=base2[0]=1;
    for(int i=1;i<N;i++)
    {
        base1[i]=base1[i-1]*131;
        base2[i]=base2[i-1]*233;
    }
    for(int i=1;i<=n;i++)
        for(int j=1;j<=m;j++)
            h[i][j]=h[i][j-1]*131+a[i][j];//行哈希
    for(int i=1;i<=n;i++)
        for(int j=1;j<=m;j++)
            h[i][j]=h[i-1][j]*233+h[i][j];//列哈希
}
//查询矩阵的哈希值，最前面的最大，需要补充由于长度导致前面少乘的幂运算
ll query(int x1,int y1,int x2,int y2)//查询矩阵的哈希值
{
    return h[x2][y2]-h[x2][y1-1]*base1[y2-y1+1]-h[x1-1][y2]*base2[x2-x1+1]
    +h[x1-1][y1-1]*base1[y2-y1+1]*base2[x2-x1 + 1];
}
```

把一个东西转换成一个大整数，这样比较两个东西是否相等的就只要比较两个整数是否相等就行了

![二维hash原理](../assets/二维hash原理.png)





## 四、动态规划

状态转移方程


### 线性DP


#### LIS 最长上升子序列

最长上升子序列的长度
f[i]记录以i结尾的最长上升子序列的长度

可利用手动维护上升子序列（二分+贪心）优化



#### LCS 最长公共子序列

f[i][j]记录 a[1~i]和b[1~j]的最长公共子序列
![LCS状态转移方程](../assets/LCS状态转移方程.png)


### 背包DP




## 五、图论

### 图

#### 图的存储


##### 邻接矩阵
```c++
int w[N][N];

// 点a 与 点b之间有 一条边 c
w[a][b] = c;
```


##### 边集数组
```c++
struct edge {int u, v, w;} e[M];

// 点a 与 点b之间有 一条边 c
e[i] = {a, b, c};
```

##### 邻接表
```c++
struct edge {v, w};
vector<edge> e[N];

// 点a 与 点b之间有 一条边 c
e[a].push_back({b, c});
```


##### 链式邻接表
```c++
struct edge {u, v, w};
// 边集
vector<edge> e;
// 记录点所对应所有的边的索引
vector<int> h[N];

// 点a 与 点b之间有 一条边 c
e.push_back({a, b, c});
h[a].push_back(e.size() - 1);
```


##### 链式前向星
```c++
// 边集，next记录下一条边的索引
struct edge {u, v, next} e[M];
// h[i]记录每个顶点头边索引，idx记录总创建的边的索引
int h[N], idx;

// 点a 与 点b之间有 一条边 c
e[idx] = {a, b, h[a]};
h[a] = idx++;
```


### 树


#### 树的重心



### 拓扑排序
```c++
vector<int> graph[N];
int indegree[N]; // 每个点的入度
int n; // n个点

vector<int> topo_sort() {
    queue<int> q;
    vector<int> res;

    // 所有入度为0的点加入队列
    for (int i = 1; i <= n; i++) {
        if (indegree[i] == 0)
            q.push(i);
    }

    while (!q.empty()) {
        int u = q.front(); q.pop();
        res.push_back(u);
        for (int v : graph[u]) {
            indegree[v]--;
            if (indegree[v] == 0)
                q.push(v);
        }
    }

    // 检查是否存在环（不合法）
    if (res.size() < n)
        return {}; // 有环，无法拓扑排序

    return res;
}
```


有向无环图（DAG）,（基于 BFS / 入度法）


### 最短路



#### Dijkstra 单源最短路
```c++
vector<PII> g[N]; // 邻接表：g[u] = {v, w}
int dist[N];      // dist[i] 表示源点到 i 的最短路径
bool vis[N];      // vis[i] 表示点 i 是否已经确定最短距离
int n, m;

void dijkstra(int start) {
    memset(dist, 0x3f, sizeof dist);
    memset(vis, 0, sizeof vis);
    dist[start] = 0;

    priority_queue<PII, vector<PII>, greater<PII>> q;
    q.push({0, start}); // {距离, 点编号}

    while (!q.empty()) {
        auto [d, u] = q.top(); q.pop();

        if (vis[u]) continue;
        vis[u] = true;

        for (auto [v, w] : g[u]) {
            if (dist[v] > dist[u] + w) {
                dist[v] = dist[u] + w;
                q.push({dist[v], v});
            }
        }
    }
}
```


一旦某个点的最短路径被确定，就不会再被更新
适用于边权非负的图（负边可能导致最短路“提前被确定”，错过更优路径）

#### Floyd 任意两点最短路径
```c++
const int INF = INT_MAX;  // 用于表示无穷大，无法到达的点

void floydWarshall(int n, vector<vector<int>>& dist) {
    // dist[i][j] 表示从节点 i 到节点 j 的最短路径长度

    // 通过中间节点 k 更新路径
    for (int k = 0; k < n; ++k) {
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (dist[i][k] != INF && dist[k][j] != INF) {
                    dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j]);
                }
            }
        }
    }
}
```



#### Bellman-Ford 有负权边
```c++
const int INF = 0x3f3f3f3f;

struct Edge {
    int u, v, w;
};

int dist[N];
int n, m;
vector<Edge> edges;

bool bellman_ford(int start) {
    memset(dist, 0x3f, sizeof dist);
    dist[start] = 0;

    // 最多做 n-1 次松弛
    for (int i = 1; i < n; i++) {
        bool updated = false;
        for (auto e : edges) {
            if (dist[e.u] < INF && dist[e.v] > dist[e.u] + e.w) {
                dist[e.v] = dist[e.u] + e.w;
                updated = true;
            }
        }
        if (!updated) break; // 没更新，提前结束
    }

    // 再做一次：检查负环
    for (auto e : edges) {
        if (dist[e.u] < INF && dist[e.v] > dist[e.u] + e.w) {
            return false; // 有负环
        }
    }

    return true; // 无负环
}
```


对于一个 n 个点的图，最多只需要 进行 n-1 次松弛（最长路径就是n-1条边），就能求出所有最短路径（前提：无负环）


#### SPFA 带负权最短路
```c++
const int INF = 0x3f3f3f3f;
struct Edge {
    int to, weight;
};
vector<Edge> g[N];

int dist[N];      // 最短路径数组
bool in_queue[N]; // 是否在队列中
int cnt[N];       // 统计每个点入队次数（判负环）
int n, m;

bool spfa(int start) {
    memset(dist, 0x3f, sizeof dist);
    memset(in_queue, 0, sizeof in_queue);
    memset(cnt, 0, sizeof cnt);

    queue<int> q;
    dist[start] = 0;
    q.push(start);
    in_queue[start] = true;
    cnt[start]++;

    while (!q.empty()) {
        int u = q.front(); q.pop();
        in_queue[u] = false;

        for (auto &e : g[u]) {
            int v = e.to, w = e.weight;
            if (dist[v] > dist[u] + w) {
                dist[v] = dist[u] + w;
                if (!in_queue[v]) {
                    q.push(v);
                    in_queue[v] = true;
                    cnt[v]++;
                    // 根据Bellman-Ford，最终进行n-1次松弛操作，每个点最多入队n-1次
                    if (cnt[v] >= n) return false; // 存在负环
                }
            }
        }
    }

    return true; // 没有负环
}
```


SPFA（Shortest Path Faster Algorithm）最短路径算法模板，它是 Bellman-Ford 的队列优化版本



### 最小生成树

最小生成树（MST，Minimum Spanning Tree） 是一个图论中的概念，它是一个连接图中所有顶点的树，并且树中所有边的权重之和最小

#### Kruskal
```c++
struct Edge {
    int u, v, weight;
    Edge(int u, int v, int w) : u(u), v(v), weight(w) {}
    bool operator<(const Edge& other) const {
        return weight < other.weight;  // 按边权排序
    }
};

// 并查集（Union-Find）用于判断是否形成环
class UnionFind {
public:
    vector<int> parent, rank;

    UnionFind(int n) {
        parent.resize(n);
        rank.resize(n, 0);
        iota(parent.begin(), parent.end(), 0);  // 初始化，每个点的父节点是它自己
    }

    // 查找根节点，路径压缩
    int find(int x) {
        if (parent[x] != x) {
            parent[x] = find(parent[x]);  // 路径压缩
        }
        return parent[x];
    }

    // 合并两个集合
    bool unionSets(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);

        if (rootX != rootY) {
            // 按秩合并，保持树的平衡
            if (rank[rootX] > rank[rootY]) {
                parent[rootY] = rootX;
            } else if (rank[rootX] < rank[rootY]) {
                parent[rootX] = rootY;
            } else {
                parent[rootY] = rootX;
                rank[rootX]++;
            }
            return true;
        }
        return false;
    }
};

int kruskal(int n, vector<Edge>& edges) {
    UnionFind uf(n);
    int mstWeight = 0;
    int edgesUsed = 0;

    // 将所有边按权重从小到大排序
    sort(edges.begin(), edges.end());

    for (auto& edge : edges) {
        int u = edge.u, v = edge.v, weight = edge.weight;
        
        // 如果没有形成环，则将该边加入生成树
        if (uf.unionSets(u, v)) {
            mstWeight += weight;
            edgesUsed++;
        }

        // 如果生成树包含 n-1 条边，则结束
        if (edgesUsed == n - 1) {
            break;
        }
    }

    // 如果生成树包含的边数小于 n-1，说明图不连通
    if (edgesUsed != n - 1) {
        cout << "图不连通，无法生成最小生成树！" << endl;
        return -1;
    }

    return mstWeight;  // 返回最小生成树的权重和
}
```

Kruskal 算法通过贪心策略，每次选择权重最小的边，逐渐构建生成树，直到生成树包含所有节点



#### Prim
```c++
// Prim 算法
int prim(int n, vector<vector<int>>& graph) {
    vector<int> minCost(n, INF);  // 记录从生成树到其他点的最小边权
    vector<bool> inMST(n, false); // 记录某个节点是否在生成树中
    minCost[0] = 0;  // 从第一个节点开始
    int mstWeight = 0;

    for (int i = 0; i < n; ++i) {
        // 找到当前不在生成树中的最小权边
        int u = -1;
        for (int v = 0; v < n; ++v) {
            if (!inMST[v] && (u == -1 || minCost[v] < minCost[u])) {
                u = v;
            }
        }

        // 如果所有的节点都已加入生成树且图不连通，返回 -1
        if (minCost[u] == INF) {
            return -1;
        }

        // 将 u 节点加入生成树
        inMST[u] = true;
        mstWeight += minCost[u];

        // 更新邻接节点的最小边权
        for (int v = 0; v < n; ++v) {
            if (!inMST[v] && graph[u][v] != INF && graph[u][v] < minCost[v]) {
                minCost[v] = graph[u][v];
            }
        }
    }

    return mstWeight;  // 返回最小生成树的总权重
}
```

Prim 算法是从某个节点开始，逐渐将图中的其他节点通过最小权重的边连接到生成树中，直到所有节点都被连接



## 六、数论


## 七、线性代数


## 八、组合数学



## 九、计算几何


## 十、概率


## 十一、博弈论






