```

const int N = 4 * 1e4 + 10;
struct LCATREE //边添加好后记得调用bfs(root)初始化
{
    /*
        vector<int> g[N];//邻接数组存边
            void add(int a, int b)
            {
                g[a].push_back(b);
            }
    */
    int head[N], next[2 * N], to[2 * N], idx = 1; //邻接表存边(内存占优)
    //邻接表的计数idx从1开始 可以不用初始化head为-1
    // head[i]:与i节点连接的最后一条边的编号
    // next[i]:编号为i的边的上一条边的编号
    // to[i]:编号为i的有向边指向的下一个节点的编号
    int depth[N], fa[N][32];
    //深度数组     倍增数组
    void add(int a, int b) //加入边
    {
        to[idx] = b;
        next[idx] = head[a];
        head[a] = idx;
        idx++;
    }
    void bfs(int root) //初始化
    {
        queue<int> q;
        bitset<N> cmp; //广搜存某点是否被搜索过
        q.push(root);
        cmp[root] = 1;
        depth[root] = 1; //根节点深度为1
        while (q.size())
        {
            int now = q.front();
            q.pop();
            for (int i = head[now]; i != 0; i = next[i]) //因为idx从1开始记录,结束条件设为i!=0
            {
                int next = to[i];
                if (cmp[next] == 0)
                {
                    cmp[next] = 1;                //记录next点被搜过
                    depth[next] = depth[now] + 1; //更新next的深度
                    q.push(next);
                    fa[next][0] = now; //更新倍增数组
                    for (int i = 1; i <= 31; i++)
                        fa[next][i] = fa[fa[next][i - 1]][i - 1];
                }
            }
        }
    }
    int lca(int a, int b) //求a和b的lca
    {
        if (depth[a] < depth[b]) //将深度大的节点往上跳到深度相同
            swap(a, b);
        for (int i = 31; i >= 0; i--)
            if (depth[fa[a][i]] >= depth[b])
                a = fa[a][i];
        if (a == b) //特判
            return a;
        for (int i = 31; i >= 0; i--) //倍增找lca
        {
            if (fa[a][i] != fa[b][i])
            {
                a = fa[a][i];
                b = fa[b][i];
            }
        }
        return fa[a][0];
    }
} tree;

```