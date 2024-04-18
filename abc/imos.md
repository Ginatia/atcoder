[D - Water Heater](https://atcoder.jp/contests/abc183/tasks/abc183_d)

有热水器每分钟提供 $W$ 升水  
N人，第 $i$ 个人在 $[S,T)$ 时间里，每分钟使用 $P_i$ 升水  

**请问可以为每个人提供热水吗？**

对 $[S,T)$ 的每一个时刻，增加 $P_i$ 的水  
使用imos方法，对进入的时刻$S，+=P_i$ 退出的时刻 $T，-=P_i$
即知道每一时刻所需要的水是多少升  


```cpp
void solve()
{
    int N,W;
    std::cin>>N>>W;
    int X=2e5;
    std::vector<i64>S(X+1);
    for(int i=0;i<N;i++){
        int l,r,p;
        std::cin>>l>>r>>p;
        S[l]+=p;
        S[r]-=p;
    }
    for(int i=0;i<X;i++){
        S[i+1]+=S[i];
        if(S[i]>W){
            std::cout<<"No\n";
            return;
        }
    }
    std::cout<<"Yes\n";
}

```