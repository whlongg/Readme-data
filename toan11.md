#include <iostream>
#include <vector>
#include <queue>
#include <map>
#include <string>

using namespace std;

int main() {
    string s;
    cin >> s;

    map<pair<int, int>, vector<pair<int, int>>> adj;
    map<pair<int, int>, int> dist;
    map<pair<int, int>, bool> vis;


    int x = 0, y = 0;
    pair<int, int> cur = {0, 0}, prev;

    for (char c : s) {
        prev = cur;
        if (c == 'D') x++;
        else if (c == 'T') x--;
        else if (c == 'N') y--;
        else y++;
        cur = {x, y};
        adj[prev].push_back(cur);
        adj[cur].push_back(prev);
    }

    queue<pair<int, int>> q;
    q.push({0, 0});
    dist[{0, 0}] = 0;
    vis[{0,0}] = true;

    int ans = -1; // Khởi tạo ans với giá trị không hợp lệ

    while (!q.empty()) {
        pair<int, int> u = q.front();
        q.pop();

        if (u == cur) {
            ans = dist[u];
            break;
        }

        for (pair<int, int> v : adj[u]) {
            if (!vis[v]) {
                vis[v] = true;
                dist[v] = dist[u] + 1;
                q.push(v);
            }
        }
    }

    cout << ans << endl;

    return 0;
}
