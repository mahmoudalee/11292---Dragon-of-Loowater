# 11292---Dragon-of-Loowater

#include <iostream>

#include <queue>

#include <functional>

using namespace std;

priority_queue<int, vector<int>, greater<int>> dragons;

priority_queue<int, vector<int>, greater<int>> knights;

int main()
{

	int n, m;
	while (cin >> n >> m && n)
	{
		int res = 0;
		while (!dragons.empty()) dragons.pop();
		while (!knights.empty()) knights.pop();

		for (int i = 0; i < n; i++)
		{
			int x;
			cin >> x;
			dragons.push(x);
		}
		for (int i = 0; i < m; i++)
		{
			int x;
			cin >> x;
			knights.push(x);
		}
		if (n > m)
			cout << "Loowater is doomed!" << endl;
		else
		{
			while(!dragons.empty() && !knights.empty())
			{
				if (knights.top() >= dragons.top())
				{
					res += knights.top();
					knights.pop();
					dragons.pop();
				}
				else
					knights.pop();
			}
			if (dragons.empty())
				cout << res << endl;
			else
				cout << "Loowater is doomed!" << endl;
		}
	}
	return 0;
}
