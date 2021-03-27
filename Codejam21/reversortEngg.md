>https://codingcompetitions.withgoogle.com/codejam/round/000000000043580a/00000000006d12d7
```
#include<bits/stdc++.h>
using namespace std;
void reverse(int *temp,int n,int start,int end)
{
    int i,j;
    i=start;
    j=end;
    while(i<j)
    {
        int t=temp[i];
        temp[i]=temp[j];
        temp[j]=t;
        i++;
        j--;
    }
    
}
int calculate_Cost(int *temp,int n)
{
     int cost=0;
     for(int i=0;i<n-1;i++)
        {
            priority_queue<pair<int,int>,vector<pair<int,int>>,greater<pair<int,int>>> pq;
            for(int j=i;j<n;j++)
            {
                pq.push({temp[j],j});
            }
            pair<int,int> x=pq.top();
            cost+=x.second-i+1;
            reverse(temp,n,i,x.second);
            
        }
        return cost;
}
int main()
{
    int t;
    cin>>t;
    
    for(int test=1;test<=t;test++)
    {
        int n;
        cin>>n;
        int cost_Given;
        cin>>cost_Given;
        int arr[n];
        bool impossible=true;
        for(int i=0;i<n;i++)
        arr[i]=i+1;
        do{
            
          // for(int i=0;i<n;i++)
          // cout<<arr[i]<<" ";
          // cout<<endl;
          int temp[n];
          for(int i=0;i<n;i++)
            temp[i]=arr[i];
          int cost=calculate_Cost(temp,n);
          if(cost==cost_Given)
          {
            impossible=false;
            break;
            
          }
          
      }
        
        while(next_permutation(arr,arr+n));
        
    
     cout<<"Case #"<<test<<": ";
     if(impossible)
        cout<<"IMPOSSIBLE"<<endl;
     else
    {
        for(int i=0;i<n;i++)
        cout<<arr[i]<<" ";
        cout<<endl;
    }
}
}
```