#include<bits/stdc++.h>
using namespace std;
int main() {
    int n,m;
    cout<<"Enter number of rows in the goldmine: ";
    cin >> n;
    cout<<"Enter number of columns in the goldmine: ";
    cin >> m;
    int a[n][m];
    cout<<"Enter gold weight at each index of the goldmine:\n";
    for(int i=0;i<n;i++)
        for(int j=0;j<m;j++)
            cin>>a[i][j];
    int dp[n][m];
    for(int j=m-1;j>=0;j--)
    {
        for(int i=n-1;i>=0;i--)
        {
            if(j == m-1)
                dp[i][j] = a[i][j];
            else if(i == 0)
                dp[i][j] = a[i][j]+max(dp[i][j+1],dp[i+1][j+1]);
            else if(i == n-1)
                dp[i][j] = a[i][j]+max(dp[i-1][j+1],dp[i][j+1]);
            else
                dp[i][j] = a[i][j]+max(dp[i-1][j+1],max(dp[i][j+1],dp[i+1][j+1]));
        }
    }
    int maxi=0;
    for(int i=0;i<n;i++)    
        maxi = max(maxi,dp[i][0]);
    cout<<"Maximum gold which can be collected from the goldmine: ";
    cout<<maxi;
    return 0;
}
