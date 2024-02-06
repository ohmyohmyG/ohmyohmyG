#include<iostream>
#include<vector>
#include<algorithm>
#include<set>

using namespace std;

#define pb push_back

bool cmp(pair<int,int> a ,pair<int,int> b)
{
    if(a.second==b.second) return a.first>b.first;
    else return a.second<b.second;
}


int main()
{
    int n,k;
    cin >> n >> k;
    vector<pair<int,int>> data(n);
    for(int i=0;i<n;i++)cin >> data[i].first;
    for(int i=0;i<n;i++)cin >> data[i].second;
    sort(data.begin(),data.end(),cmp);
    
    int ans=0;
    multiset <int> mac;
    for(int i=0;i<k;i++) mac.insert(0);
    for(int i=0;i<n;i++)
    {
        auto it=mac.lower_bound(data[i].first);
        if(it==mac.begin()) continue;
        else
        {
            mac.erase(--it);
            mac.insert(data[i].second);
            ans++;
        }
    }
    
    
    cout << ans << '\n';
    
    
    
    return 0;
}
