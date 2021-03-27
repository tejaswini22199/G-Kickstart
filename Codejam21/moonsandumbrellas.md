>https://codingcompetitions.withgoogle.com/codejam/round/000000000043580a/00000000006d1145
```
     #include<bits/stdc++.h>
using namespace std;
int main()
{
    int t;
    cin>>t;
    for(int test=1;test<=t;test++)
    {
        int X,Y;
        cin>>X>>Y;
        string S;
        cin>>S;
        int N=S.length();
        int dpC[N];
        int dpJ[N];
        if(S[0]=='?')
        {
           dpC[0]=0;
           dpJ[0]=0;
        }
        else if(S[0]=='C')
        {
          dpC[0]=0;
          dpJ[0]=INT_MAX/2;
        }
        else if(S[0]=='J')
        {
          dpJ[0]=0;
          dpC[0]=INT_MAX/2;
        }
        for(int i=1;i<N;i++)
        {
          if(S[i]=='?')
          {
            if(S[i-1]=='C')
            {
              dpC[i]=dpC[i-1];
              dpJ[i]=dpC[i-1]+X;
            }
            if(S[i-1]=='J')
            {
              dpC[i]=dpJ[i-1]+Y;
              dpJ[i]=dpJ[i-1];
            }
            if(S[i-1]=='?')
            {
              dpC[i]=min(dpC[i-1],dpJ[i-1]+Y);
              dpJ[i]=min(dpJ[i-1],dpC[i-1]+X);
            }
          }
          if(S[i]=='C')
          {
            dpC[i]=min(dpC[i-1],dpJ[i-1]+Y);
            dpJ[i]=INT_MAX/2;
          }
           if(S[i]=='J')
          {
            dpJ[i]=min(dpC[i-1]+X,dpJ[i-1]);
            dpC[i]=INT_MAX/2;
          }
          
        }
        cout<<"Case #"<<test<<": ";
        cout<<min(dpC[N-1],dpJ[N-1])<<endl;
    }
}

```