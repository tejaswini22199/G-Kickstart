>https://codingcompetitions.withgoogle.com/codejam/round/000000000043580a/00000000006d0a5c
```
#include<bits/stdc++.h>
using namespace std;
void reverse(int *arr,int n,int start,int end)
{
    int i,j;
    i=start;
    j=end;
    while(i<j)
    {
        int temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
        i++;
        j--;
    }
    
}
int main()
{
    int t;
    cin>>t;
    for(int test=1;test<=t;test++)
    {
        int n;
        cin>>n;
        int arr[n];
        for(int i=0;i<n;i++)
        cin>>arr[i];
        int cost=0;
       
        for(int i=0;i<n-1;i++)
        {
            priority_queue<pair<int,int>,vector<pair<int,int>>,greater<pair<int,int>>> pq;
            for(int j=i;j<n;j++)
            {
                pq.push({arr[j],j});
            }
            pair<int,int> x=pq.top();
            cost+=x.second-i+1;
            reverse(arr,n,i,x.second);
            
        }
        cout<<"Case #"<<test<<": ";
        cout<<cost<<endl;
    }
}
```