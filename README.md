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
                          dp通过了！！！！！！
class Solution {
public:
    int uniquePaths(int m, int n) {
int dp[m][n];
for(int i=0;i<m;i++) dp[i][0]=1;
for(int i=0;i<n;i++) dp[0][i]=1;
for(int i=1;i<m;i++){
    for(int j=1;j<n;j++){
dp[i][j]=dp[i][j-1]+dp[i-1][j];
    }
}
return dp[m-1][n-1];
    }
};   
                          力扣45题 dp和提拉克斯标号法如出一辙 
class Solution {
public:
    int jump(vector<int>& nums) {
        const int len = nums.size();
        int dp[len];
        memset(dp,0x3f,sizeof(dp));//初始化为无穷大
        dp[0] = 0;  //第0步是出发点，初始化为0
        for(int i=0 ; i<len ; ++i){
            int tmp = nums[i];
            for(int j=1 ; i+j<len && j<=tmp ; ++j){ //注意不要让数组越界
                dp[i+j] = min(dp[i+j] , dp[i]+1);//逐个松弛
            }
        }
        return dp[len-1];
    }
};
                                           力扣53
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
int index=0,maxvalue=nums[0];
for(int i=0;i<nums.size();i++){
    index+=nums[i];
    if(index>maxvalue)
    maxvalue=index;
    //注意这里上下两边不能互换，因为要考虑到数组中数全为零的情形
    if(index<=0){
        index=0;
    }
}
return maxvalue;
    }
};
