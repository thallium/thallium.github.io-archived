---
published: true
title: Croatian Open Competition in Informatics 2015/2016, contest 4 - Chewbacca
category: 题解
tags:
 倍增, LCA
layout: post
---
York University programming contest的C题。
[题目链接](https://open.kattis.com/problems/chewbacca)

题意：给出一棵有N个节点的满树，每个节点最多有K个子节点，给出Q个询问，问树上两个点的最短路径的长度。

其实这个题并不是一个很好的倍增的例子，因为每个节点到子节点的距离都是1。所以有更快的做法。