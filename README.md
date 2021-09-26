# hello-world
注意不要多余的零
力扣118题
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
vector<vector<int>> v;
v.resize(numRows);
for(int i=0;i<numRows;i++)
{
    vector<int>dp(i+1,0);
    for(int j=0;j<i+1;j++)
    {       
        if(j==0||j==i)
        dp[j]=1;
        else
        dp[j]=v[i-1][j-1]+v[i-1][j];
    }
    v[i]=dp;
}
return v;
    }
};  
力扣62 不能用dfs，df超时，但是本地编译器可以通过，蛮开心的。                           
class Solution {
public:
    int uniquePaths(int m, int n) {
int count=0;
 count=dfs(0,0,m,n);
return count;
    }
int dfs(int x,int y,int m,int n){
        if(x==n-1&&y==m-1)  return 1;
        int count=0;
if(x>=0&&x<n&&y>=0&&y<m){
    count=dfs(x+1,y,m,n)+dfs(x,y+1,m,n);
}
return count;
    }
};
