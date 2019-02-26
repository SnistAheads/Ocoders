---
title: 'Contest-1'
image: '/services/noun_591323.png'
---

Its a series of Coding Contests weekly on specific topics open for everyone.

Topics for Contest-1
#Basic Number Theory #Implementation #strings,#arrays #brute force

link [here](https://www.hackerrank.com/snistcontest1)

**SOLUTIONS FOR CONTEST-1**

**1.Decorate Tree**

Consider some solution Y, B, R, where Y+1=B and B+1=R. Let's add two yellow ornaments and one blue both to the solution and to the reserve, then we have Y=B=R. We can see that this new problem is equivalent to the old one. In this problem, the best solution is achieved when we use min(y,b,r) ornaments of each colour. Hence, we can find the said minimum, multiply by three and then remove the three extra ornaments again.


code: 
(c++ , see the logic if u dont know c++ syntax)

```cpp
#include <bits/stdc++.h>
using namespace std;

int main(){
    int a, b, c;
    cin >> a >> b >> c;
    cout << min(a + 2, min(b + 1, c)) * 3 - 3;
}
```
**2.Repeating characters**
There are many possible approaches in this problem, I will describe one of the easiest.

Let's print the initial string by the following algorithm: firstly, init the variable i=1. Then, while the encrypted string isn't empty, print the first character of this string, remove i first characters from it and increase i by one.

c++ code:
```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
    int n;
    cin >> n;
    string s;
    cin >> s;
    int index = 0;
    int gap = 1;
    while (index < n)
        cout << s[index], index += gap, gap++;
}
```

**3.Pieces of land**
https://www.hackerrank.com/challenges/restaurant/editorial


**4.Direction of Wind**
```cpp

#include<bits/stdc++.h>
#define ll long long
using namespace std;
int main()
{
    map<char,ll> m;
    map<ll,char> m1;
    m['N']=0;m['W']=1;m['S']=2;m['E']=3;
    m1[0]='N';m1[1]='W';m1[2]='S';m1[3]='E';
    ll mm,n;
    cin>>mm>>n;
    ll a[mm][n];
    ll i,j;
    for(i=0;i<mm;i++)
    {
        for(j=0;j<n;j++)
        {
            char c;
            cin>>c;
            a[i][j]=m[c];
        }
    }
    ll query;
    cin>>query;
    while(query--)
    {
        char c;
        cin>>c;
        if(c=='C')
        {
            ll x1,y1,x2,y2,dir;
            cin>>x1>>y1>>x2>>y2>>dir;
            for(i=x1-1;i<=x2-1;i++)
            {
                for(j=y1-1;j<=y2-1;j++)
                {
                    if(dir==0)
                    {
                        a[i][j]--;
                        if(a[i][j]<0)
                            a[i][j]=3;
                    }
                    else
                    {
                        a[i][j]=(a[i][j]+1)%4;
                    }
                }
            }
        }
        else
        {
            ll x,y;
            cin>>x>>y;
            cout<<(m1[a[x-1][y-1]])<<endl;
            
        }
    }
}

```
**5.Prime Sequence**

hint: learn sieve of erasthones for finding primes...
code:
```cpp

#include<bits/stdc++.h>
#define ll long long
using namespace std;
ll findi[10000001];
ll dp[10000001];
void sieve()
{
    ll i,j;
    for(i=2;i<=10000000;i++)
    {
        if(findi[i]==0)
        {
            findi[i]=i;
            for(j=i*i;j<=10000000;j+=i){
                if(findi[j]==0)
                    findi[j]=i;
            }
        }
        dp[i]=dp[i-1]+findi[i];
    }
}
int main()
{
    sieve();
    ll t;
    cin>>t;
    while(t--)
    {
        ll n;
        cin>>n;
        cout<<dp[n]<<endl;
    }
}
```
**6.Divisors of Two Integers** 
Let's take a look on the maximum element of the given array. Suddenly, this number is x (or y, the order doesn't matter). Okay, what would we do if we know x and merged list of divisors of x and y? Let's remove all divisors of x and see what we got. The maximum element in the remaining array is y. So, the problem is solved.

code:
```cpp

#include <bits/stdc++.h>

using namespace std;

int main() {
#ifdef _DEBUG
	freopen("input.txt", "r", stdin);
//	freopen("output.txt", "w", stdout);
#endif
	int n;
	cin >> n;
	multiset<int> a;
	for (int i = 0; i < n; ++i) {
		int x;
		cin >> x;
		a.insert(x);
	}
	int x = *prev(a.end());
	for (int i = 1; i <= x; ++i) {
		if (x % i == 0) {
			a.erase(a.find(i));
		}
	}
	cout << x << " " << *prev(a.end()) << endl;
	return 0;
}
```
