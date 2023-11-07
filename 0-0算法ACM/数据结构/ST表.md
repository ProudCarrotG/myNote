```

#include <bits/stdc++.h>
using namespace std;
#define int long long
#define LL long long
#define PII pair<int, int>
#define umap unordered_map
#define x first
#define y second
#define endl "\n"
#define debug(x) cout << #x << ' ' << x << endl;
#define fg cout << "-----------------" << endl;
signed main()
{
    // freopen(".in", "r", stdin);
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
    int n, m;
    cin >> n >> m;
    //计算总长度是2的几次方
    //可以不做,数组开大点不影响
    int l = 0;
    while ((1 << l) <= n)
        l++;
    //初始化输入
    vector<vector<int>> st(n + 1, vector<int>(l + 1));
    for (int i = 1; i <= n; i++)
        cin >> st[i][0]; //输入直接放到st表里
    //初始化st表
    for (int j = 1; j <= l; j++) //先循环长度开始
    {
        for (int i = 1; i + (1 << j) - 1 <= n; i++) //循环左端点
        {
            st[i][j] = max(st[i][j - 1], st[i + (1 << (j - 1))][j - 1]);
            // cout << i << ' ' << j << ' ' << st[i][j] << endl;
        }
    }
    //预处理长度的log值
    vector<int> logn(n + 1, 0);
    // 1的log为0
    for (int i = 2; i <= n; i++) //从2开始枚举到总长度n
        logn[i] = logn[i >> 1] + 1;
    // 处理问题
    auto get = [&](int l, int r)
    {
        //获得[l,r]的最大值
        if (l > r)
            swap(l, r);
        int len = r - l + 1;
        int loglen = logn[len];
        return max(st[l][loglen], st[r - (1 << loglen) + 1][loglen]);
    };
    while (m--)
    {
        int l, r;
        cin >> l >> r;
        cout << get(l, r) << endl;
    }
    return 0;
}

```