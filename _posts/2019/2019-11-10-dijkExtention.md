---
published: true
title: Dijkstra的一些扩展/Extension of Dijkstra
category: 算法笔记/Alg Notes
tags: 
- 最短路/Shortest Path 
- 图论/Graph Theory
layout: post
math: true
output: pdf_document
---
Just as a reminder with simple explanatin.

<!-- more -->
# 路径记录/Recording the path

我们开一个`vector<int> pre[N]`用来记录某个点的前一个点，在更新距离的时候，如果当前距离更短就舍弃掉之前的记录，将当前点作为被更新点的前一个点；如果当前距离和最短距离相等就在数组里加上这个点。

Use `vector<int> pre[N]` to record the previous vertices of all the vertices in the shortest path(s). When updating the distance to vetex $v$, if the current distance is better, discard the previous record and let the current vetex be the previous vetex of $v$. If the distance is the same, just add the current vertex to `pre[v]`.

```cpp
for(pii it:E[u]){
    ll v=it.S,cost=it.F;
    if(!vis[v]&&dis[v]>dis[u]+cost){
        dis[v]=dis[u]+cost;
        pre[v].clear();
        pre[v].pb({cost,u});
        q.push({dis[v],v});
    }else if(dis[v]==dis[u]+cost)
        pre[v].pb({cost,u});
}
```

# 最短路径的数量/Number of shortest pathes

和路径记录类似，如果更短就让数目等于1,如果一样就加1。

Similar to recording the path, if the distance is better then let the number be one. If the same, plus 1.

```cpp
if(!vis[v]&&dis[u]+cost<dis[v]){
    cnt[v]=1;
    dis[v]=dis[u]+cost;
}else if(dis[u]+cost==dis[v]){
    cnt[v]++;
}
```