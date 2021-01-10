---
published: true
title: Tutorial for Codeforces 801I - Fake News (hard)
category: 题解/Tutorial
tags:
- 后缀数组/Suffix Array
layout: post
math: true
---
看了两天才看明白这别人的代码
<!-- more -->

## Solution

Consider the contribution to the answer of the each occurrence of each substring. Suppose this substring has appeared $$c$$ times. For a new occurrence of this substring, the answer would change from $$c^2$$ to $$(c+1)^2$$, that is to say, each new occurrence contributes $$(c+1)^2-c^2=2\cdot c+1$$ to the answer. Since there are $$\dfrac {n\cdot (n+1)} 2$$ substrings, the answer is at least $$\dfrac {n\cdot (n+1)} 2$$ , now what we left is to focusing on finding the occurrence of the substrings. You will see why it's more handy to do this.

Let's build the suffix array and the LCP array first. You will notice that the occurrence of some substring is a subsegment in the suffix array. so is it in the LCP array and the min value of the subsegment in the LCP array is the length of that substring. We can process each of the LCP value in the descending order. This is because each LCP value $$lcp_i$$ can represent $$lcp_i$$ substrings, so if we process them in the descending order, we can assure that all the substrings have appeared before.