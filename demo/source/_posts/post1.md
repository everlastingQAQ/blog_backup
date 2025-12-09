---
title: 华中农业大学第十五届程序设计竞赛（新生赛）游记及部分题解 #【必需】页面标题
date: 2025-12-09 17:58:26 #【必需】页面创建日期
updated: #【可选】页面更新日期
categories: 
- [题解]
- [游记]
keywords: #【可选】文章关键字
---

# 华中农业大学第十五届程序设计竞赛（新生赛）游记及部分题解

> 仅以此记录我的第一次程序设计线下赛

## 游记

第一次线下赛，不出意料的感觉晚上没睡好，但到了比赛场地后就毫无疲惫感而言了。~~（瑞幸的新品是真难喝）~~

到场签到领了伴手礼，一个ACM的笔记本和一张明信片，虽然有点不及预期，但第一次拿到周边物件还是很兴奋的。在这里还是得感谢志愿者，赛前领的小纸条一下就弄丢了，上面的帐号密码志愿者们很热情地帮我解决了，非常感谢！另外赛前统一发的小熊猫dev还是很好用的，避免了用电脑自带的devc++，好评！

比赛开始后，很幸运地快速发现了签到题L，拿了一个一血！交完显示“correct”的时候发现自己是一血还是非常兴奋的！之后看了眼D题，发现跟热身赛的题差不多一样（~~其实并非~~），写完wa了之后，看到榜上有不少人也wa了D，就觉得有点不对劲了，仔细看题发现只能删除长度大于一的字串，找了下规律后又交了一发，wa了之后就没碰D题了(赛后题解显示是一道恐怖的分类讨论)。

接下来值得说的就是C题，赛时看出来是单调栈很兴奋，快速敲完交了一发wa后，由于没读清题意，自己一直在那乱改，交了无数发，最后十分钟实在没招了，而且此时也对题目思考地比较深入，再把第一发wa去掉特判后交了一发竟然A了~~(真的感受到了救赎感)~~，但是白白在这道题浪费了一个多小时，赛后看来很有可能可以再开一题，也是很可惜了。

另外，赛中发的午饭是一个“冷”热狗，鸡腿和两根香肠，难吃。

最后还是凭借7题获得了金牌，但以993的罚时在7题尾。就本次比赛来说，一定要想清楚题目再交，下次不能 “样例过了就AC” 了。

<br>

## 部分题解

#### L - 山海之约

##### 题意：

给定两个非负整数 a 与 b，判断它们的和是否为神秘数字 350234。

##### 代码：

``` c++
#include <bits/stdc++.h>
using namespace std;
using ll = long long;
using ld = long double;

#define fi first
#define se second

const ll MAXN = 1e8;
const ld eps = 1e-12;
const ll mod = 1e9 + 7;

void solve ()
{
	ll a, b;
	cin >> a >> b;
	if (a + b == 350234) {
            cout << "YES" << '\n';
	}else {
		cout << "NO" << '\n';
	}
}

int main ()
{
	ios::sync_with_stdio(0);
	cin.tie(0);
	int _ = 1;
	cin >> _;
	while (_--) {
		solve();
	}
	return 0;
}
```

#### H - 对决

##### 题意：

给定两个字符串 s 与 t，记字串“fire”出现次数是a，“water”出现次数是b， “wind”出现次数是c，定义字符串的权值为a + b * c，判断s的权值是否严格大于t的权值。

##### 思路：

简单遍历即可。
时间复杂度：O(n + m)。

##### 代码：

``` c++
#include <bits/stdc++.h>
using namespace std;
using ll = long long;
using ld = long double;

#define fi first
#define se second

const ll MAXN = 1e8;
const ld eps = 1e-12;
const ll mod = 1e9 + 7;

ll n, m;

void solve ()
{
	string a = "fire";
	string b = "water";
	string c = "wind";
	cin >> n >> m;
	string s, t;
	cin >> s >> t;
	
	ll cnta = 0;
	ll cntb = 0;
	ll cntc = 0;
	for (int i = 0; i <= n - 4; i++) {
		if (s[i] == 'f' && s[i + 1] == 'i' && s[i + 2] == 'r' && s[i + 3] == 'e') {
			cnta++;
		}
		if (s[i] == 'w' && s[i + 1] == 'i' && s[i + 2] == 'n' && s[i + 3] == 'd') {
			cntc++;
		}
	}
	for (int i = 0; i <= n - 5; i++) {
		if (s[i] == 'w' && s[i + 1] == 'a' && s[i + 2] == 't' && s[i + 3] == 'e' && s[i + 4] == 'r') {
			cntb++;
		}
	}
	
	ll cntaa = 0;
	ll cntbb = 0;
	ll cntcc = 0;
	
	for (int i = 0; i <= m - 4; i++) {
		if (t[i] == 'f' && t[i + 1] == 'i' && t[i + 2] == 'r' && t[i + 3] == 'e') {
			cntaa++;
		}
		if (t[i] == 'w' && t[i + 1] == 'i' && t[i + 2] == 'n' && t[i + 3] == 'd') {
			cntcc++;
		}
	}
	for (int i = 0; i <= m - 5; i++) {
		if (t[i] == 'w' && t[i + 1] == 'a' && t[i + 2] == 't' && t[i + 3] == 'e' && t[i + 4] == 'r') {
			cntbb++;
		}
	}
	
	if (cnta + cntb * cntc > cntaa + cntbb * cntcc) {
		cout << "YES" << '\n';
	}else {
		cout << "NO" << '\n';
	}
}

int main ()
{
	ios::sync_with_stdio(0);
	cin.tie(0);
	int _ = 1;
	cin >> _;
	while (_--) {
		solve();
	}
	return 0;
}
```

#### I - 学霸题

##### 题意

给定三个点 A, B, C，找出一个点D使得这 4 个点可以连成一个平行四边形。

##### 思路

确定两个点，求出两点间x和y座标的变化后根据第三个点推出第四个点的位置。
时间复杂度：O(1)。

##### 代码

``` c++
#include <bits/stdc++.h>
using namespace std;
using ll = long long;
using ld = long double;

#define fi first
#define se second

const ll MAXN = 1e8;
const ld eps = 1e-12;
const ll mod = 1e9 + 7;

void solve ()
{
	ll x1, y1, x2, y2, x3, y3;
	cin >> x1 >> y1 >> x2 >> y2 >> x3 >> y3;
	ll tx = x2 - x1;
	ll ty = y2 - y1;
	ll x4 = x3 + tx;
	ll y4 = y3 + ty;
	cout << x4 << ' ' << y4 << '\n';
}

int main ()
{
	ios::sync_with_stdio(0);
	cin.tie(0);
	int _ = 1;
	cin >> _;
	while (_--) {
		solve();
	}
	return 0;
}
```

#### B - 爱的魔法

##### 题意

给定一个序列，对于序列中的每一个数，交换至多两个数位，最大化操作后的序列和。

##### 思路

数据范围不是很大，直接对每一个数简单遍历，取每个数的最大值即可。
时间复杂度：O(n)。

##### 代码

``` c++
#include <bits/stdc++.h>
using namespace std;
using ll = long long;
using ld = long double;

#define fi first
#define se second

const ll MAXN = 1e8;
const ld eps = 1e-12;
const ll mod = 1e9 + 7;

ll n;

void solve ()
{
	cin >> n;
	vector <ll> v(n);
	for (int i = 0; i < n; i++) {
		cin >> v[i];
	}
	
	for (int i = 0; i < n; i++) {
		string s = to_string(v[i]);
		for (int k = 0; k < (ll)s.size(); k++) {
			ll t = s[k] - '0';
			ll pos = k;
			for (ll j = k + 1; j < (ll)s.size(); j++) {
				ll a = s[j] - '0';
				if (a >= t) {
					t = a;
					pos = j;				
				}
			}
			if (pos != k && s[pos] > s[k]) {
				swap(s[pos], s[k]);
				break;
			}
		}
		v[i] = stoll(s);
	}
	
	ll ans = 0;
	for (int i = 0; i < n; i++) {
		ans += v[i];
	}
	
	cout << ans << '\n';
}

int main ()
{
	ios::sync_with_stdio(0);
	cin.tie(0);
	int _ = 1;
	cin >> _;
	while (_--) {
		solve();
	}
	return 0;
}
```

#### A - 矩形游戏

##### 题意

给定一个**单调不降**的序列[b<sub>1</sub>, b<sub>2</sub>, ... b<sub>n</sub>]与一个k行n列的矩阵A。签到哥从矩阵的第一行第一列移动到第k行的任意一列。签到哥位于(i, j)时可以移动到(i + 1, j - 1)或(i + 1, j)或(i + 1, j + 1)。签到哥只能移动到大于等于自己的位置，且移动后签到哥的体力也会相应增加。

求签到哥到达第k行的体力最大值

##### 思路

由于序列单调不降，只需尽量往右走就行。另外，由于k是1e9级别，而n是2e5级别，最后如果到最后一列可以直接退出单独计算。
时间复杂度：O(n)。

##### 代码

``` c++
#include <bits/stdc++.h>
using namespace std;
using ll = long long;
using ld = long double;

#define fi first
#define se second

const ll MAXN = 1e8;
const ld eps = 1e-12;
const ll mod = 1e9 + 7;

ll k, n;

void solve ()
{
	cin >> k >> n;
	vector <ll> v(n);
	for (int i = 0; i < n; i++) {
		cin >> v[i];
	}
	
	ll sum = 0;
	ll j = 0;
	ll t = 0;
	for (int i = 0; i < k; i++) {
		if (sum >= v[j + 1] && j < n - 1) {
			j++;
		}
		sum += v[j];
		if (j == n - 1) {
			t = k - i - 1;
			break;
		}
	}
	
	sum += max(0LL, t) * v[n - 1];
	cout << sum << '\n';
}

int main ()
{
	ios::sync_with_stdio(0);
	cin.tie(0);
	int _ = 1;
	cin >> _;
	while (_--) {
		solve();
	}
	return 0;
}
```

#### M - 终极考验

##### 题意

给定n个石柱高度，耗费一点能量可以使任意一个i至min(i + x - 1, n)区间内的所有石柱升高1米。

求使得石柱的高度单调不降所要耗费能量的最小值。

##### 思路

这里给出一个简洁的思路。维护出一个差分数组后，只需要在差分数组的基础上对于每个d[i]判断合法的d[i - x]是否小于0。若小于0，则可以给d[i]加上d[i - x]，依次遍历，最后加上所有小于0的d[i]的绝对值即是花费能量的最小值。
时间复杂度：O(n);

##### 代码

``` c++

#include <bits/stdc++.h>
using namespace std;
using ll = long long;
using ld = long double;

#define fi first
#define se second

const ll MAXN = 1e8;
const ld eps = 1e-12;
const ll mod = 1e9 + 7;

void solve ()
{
	ll n, x;
	cin >> n >> x;
	vector <ll> v(n + 1, 0);
	vector <ll> d(n + 1, 0);
	for (int i = 1; i <= n; i++) {
		cin >> v[i];
		d[i] = v[i] - v[i - 1];
	}
	
	for (int i = x + 1; i <= n; i++) {
		if (d[i - x] < 0) {
			d[i] += d[i - x];
		}
	}
	
	ll ans = 0;
	for (int i = 2; i <= n; i++) {
		if (d[i] < 0) {
			ans += abs(d[i]);
		}
	}
	
	cout << ans << '\n';
	
}

int main ()
{
	ios::sync_with_stdio(0);
	cin.tie(0);
	int _ = 1;
	cin >> _;
	while (_--) {
		solve();
	}
	return 0;
}
```

#### C - 小W的计数题

##### 题意

对于给出的每一个a<sub>i</sub>，找到元素数量最多的集合S<sub>x</sub>, 其中对于任意的y∈S，使得[a<sub>min{x,y}</sub>, ..., a<sub>max{x,y}</sub>]的最大值为a<sub>y</sub>。

##### 思路

题意很复杂，简要地说，这一题实际上是想要找到对于每一个a<sub>i</sub>向左的单调递增区间和向右的单调递增区间的长度之和。
由此，不难想到可以利用单调栈来解决问题。可以维护从前往后的一个单调递减栈和从后往前的维护一个单调递减栈，在每一位加上栈的大小，重复两遍即是最终结果。
时间复杂度：O(n);

##### 代码

``` c++
#include <bits/stdc++.h>
using namespace std;
using ll = long long;
using ld = long double;

#define fi first
#define se second

const ll MAXN = 1e8;
const ld eps = 1e-12;
const ll mod = 1e9 + 7;

ll n;

void solve ()
{
	cin >> n;
	vector <ll> v(n + 1);
	for (int i = 1; i <= n; i++) {
		cin >> v[i];
	}
	
	vector <ll> ans(n + 1, 0);
	stack <ll> stk;
	
	for (int i = 1; i <= n; i++) {
		while (!stk.empty() && v[i] > stk.top()) {
			stk.pop();
		}
		stk.push(v[i]);
		ans[i] += stk.size();
	}
	
	stack <ll> stk1;
	
	for (int i = n; i >= 1; i--) {
		while (!stk1.empty() && v[i] > stk1.top()) {
			stk1.pop();
		}
		stk1.push(v[i]);
		ans[i] += stk1.size();
	}
	
	for (int i = 1; i <= n; i++) {
        cout << ans[i] - 1 << ' ';
	}
	cout << '\n';
	
}

int main ()
{
	ios::sync_with_stdio(0);
	cin.tie(0);
	int _ = 1;
	cin >> _;
	while (_--) {
		solve();
	}
	return 0;
}
```

#### G - 二分图判定

##### 题意

给定一个序列[a<sub>1</sub>, a<sub>2</sub>, ... a<sub>n</sub>]和一个正整数k, 在一张包含n个点的图上，第i个点的权值为i，对于合法的任意两点i，j，若 |a<sub>i</sub> - a<sub>j</sub>| > k，就在i与j两点之间连接一条无向边。

求出最小的非负整数k，使得按照上述方法生成的图是二分图。

##### 思路

读完题后不难发现，该题的目的是在给定的a<sub>n</sub>序列中，将其分为两个集合，并最小化两个集合的极差的最大值。

不难想到可以利用二分答案的方法来解决这道题, 可以先对a<sub>n</sub>序列进行排序，再以答案进行从前到后和从后到前的check，最后若r <= l + 1则说明check成功。
时间复杂度：O(nlogn);

##### 代码

``` c++
#include <bits/stdc++.h>
using namespace std;
using ll = long long;
using ld = long double;

#define fi first
#define se second

const ll MAXN = 1e8;
const ld eps = 1e-12;
const ll mod = 998244353;

ll n;

void solve ()
{
    cin >> n;
    vector <ll> v(n + 1);
    for (int i = 1; i <= n; i++) {
        cin >> v[i];
    }
    sort(v.begin() + 1, v.end());

    auto check = [&] (ll md) -> bool {
        ll l = 1;
        for (int i = 1; i <= n; i++) {
            if (v[i] - v[1] <= md) {
                l = i;
            }else {
                break;
            } 
        }
        ll r = n;
        for (int i = n - 1; i >= 1; i--) {
            if (v[n] - v[i] <= md) {
                r = i;
            }else {
                break;
            }
        }
        return r <= l + 1;
    };

    ll l = 0, r = v[n]; 
    while (l <= r) {
        ll mid = l + ((r - l) >> 1);
        if (check(mid)) {
            r = mid - 1;
        }else {
            l = mid + 1;
        }
    }
    cout << l << '\n';
}

int main ()
{
	ios::sync_with_stdio(0);
	cin.tie(0);
	int _ = 1;
	cin >> _;
	while (_--) {
		solve();
	}
	return 0;
}
```

**未完待续