#include <bits/stdc++.h>
using namespace std;



#define WHITE 1
#define GRAY  2
#define BLACK 3

int adj[100][100] ;
int color[100];
int parent[100];
int dis[100];

int node ;
int edge ;

void bfs (int statingnode )
{
  for (int i = 0; i < node ; i++)
  {
    color[i] = WHITE;
    dis[i]=INT_MIN;
    parent[i]=-1;
  }
  dis[statingnode]=0;
  parent[statingnode]=-1;
  queue<int > q ;
  q.push(statingnode);
  while(!q.empty())
  {
    int x ;
    x=q.front();
    q.pop();
    color[x]=GRAY;

    for(int i =0;i<node;i++)
    {
      if(adj[x][i]==1)
      {
        if(color[i]==WHITE)
        {
          parent[i]=x;
          dis[i]=dis[x]+1; 
          q.push(i);
        }
      }
    }





    color[x]=BLACK;
  }
}

int main()
{


  cin >> node >> edge;
  int n1 , n2 ;
  for (int i = 0; i < node ; i++)
  {
    cin >> n1 >> n2;
    adj[n1][n2] = 1;
    adj[n2][n1] = 1;
  }
  bfs(0);



  return 0;
}






2nd code ::::::::::::::::::::::::::::::::::::::::

#include <bits/stdc++.h>
using namespace std;
#define ll long long int 

std::vector<int > ar[100001];
int dist[100001];
int par[100001];
bool vis[100001];
 
int n , m ;
 
void bfs()
{
    queue<int> q ;
    dist[1]=1;
    vis[1]=1;
    q.push(1);
 
    while(!q.empty())
    {
        int node = q.front();
        q.pop();
        for(int u:ar[node])
            if(vis[u]==false)
            {
                dist[u]= dist[node]+1;
                vis[u]=true;
                par[u]=node;
                q.push(u);
            }
    }
}
 
 
 
int main()
{
    int a , b ;
    cin>>n>>m;
    for(int i =1 ;i<=m;i++ )
    {
        cin>>a>>b;
        ar[a].push_back(b);
        ar[b].push_back(a);
    }
   bfs();

    
 
 
 
    return 0;
}

