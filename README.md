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
