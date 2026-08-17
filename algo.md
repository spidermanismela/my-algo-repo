![alt text](image.png)
#include<bits/stdc++.h>
using namespace std;
const int N=1<<16;
int arr[N+5];
set<int> s;
queue<pair<int,int>> q;
int main()
{
	q.push({0,0});
	s.insert(0);
	arr[0]=0;
	while(q.size())
	{
		pair<int,int> p=q.front();
		q.pop();
		if(!s.count((p.first+1)%N))
		{
			q.push({(p.first+1)%N,p.second+1});
			s.insert((p.first+1)%N);
			arr[(p.first+1)%N]=p.second+1;
		}
		if(!s.count((p.first-1+N)%N))
		{
			q.push({(p.first-1+N)%N,p.second+1});
			s.insert((p.first-1+N)%N);
			arr[(p.first-1+N)%N]=p.second+1;
		}
		if(!s.count((p.first/2)%N)&&p.first%2==0)
		{
			q.push({(p.first/2)%N,p.second+1});
			s.insert((p.first/2)%N);
			arr[(p.first/2)%N]=p.second+1;
		}
		if(!s.count((p.first/2+N/2)%N)&&p.first%2==0)
		{
			q.push({(p.first/2+N/2)%N,p.second+1});
			s.insert((p.first/2+N/2)%N);
			arr[(p.first/2+N/2)%N]=p.second+1;
		}
		
		
	}
	int T;
	cin>>T;
	while(T--)
	{
		int n;
		cin>>n;
		int a;
		long long sum=0;
		for(int i=1;i<=n;i++)
		{
			cin>>a;
			sum+=arr[a];
		}
		cout<<sum<<endl;
	}
	return 0;
}