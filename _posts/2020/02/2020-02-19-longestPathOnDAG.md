---
published: true
title: Finding the longest path on a DAG
category: 算法笔记/Alg Notes
tags: 
- 图论/Graph Theory
- 动态规划/DP
- DFS
layout: post
math: true
---
```cpp
vector<int> G[N];
int dp[N];

int get(int u){
	if(dp[u]) return dp[u];
	for(auto it:G[u]){
		dp[u]=max(dp[u],get(it)+1);
	}
	return dp[u];
}
```