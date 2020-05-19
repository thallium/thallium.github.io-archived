---
published: true
title: 单调栈常见模型
category: 算法笔记/Alg Notes
tags:
- 数据结构/Data Structure
- 单调栈/Monotone Stack
layout: post
---
总结一下加深印象
<!-- more -->

## 左边第一个比当前小

严格单调递增栈，如果求的是数字栈内就存数字，如果求距离栈内就存数字+下标或者数字+到栈内前一个元素的距离。

### 举例

`[2,1,6,4,5]`

`[]` 空栈，说明2之前没有比2小的元素，然后2入栈 `[2]`

为了保持单调递增，需要把2弹出，变成空栈，说明1前面也没有比1小的，然后1入栈 `[1]`

6比1大，直接入栈，`[1, 6]`

先把比4大的元素弹出`[1]`,然后入栈 `[1, 4]`

5直接入栈 `[1, 4, 5]`

求距离：

`{元素,到前一个的距离}`

`[]` -> `[{2,1}]`

`[]` -> `[{1,2}]`

`[{1,2}]` -> `[{1,2},{6,1}]`

`[{1,2}]` -> `[{1,2},{4,2}]`

`[{1,2},{4,2}]` -> `[{1,2},{4,2},{5,1}]`

### 代码

求元素：

```cpp
stack<int> stk
vector<int> ans(n);
for(int i=0;i<n;i++){
    while(!stk.empty()&&stk.top()>=a[i]) stk.pop();
    ans[i]=stk.top();
    stk.push(a[i]);
}
```

求距离:

```cpp
stack<pair<int,int>> stk;
vector<int> ans(n);
for(int i=0;i<n;i++){
    int res=1;
    while(!stk.empty()&&stk.top().first>=a[i]){
        res+=stk.top().second;
        stk.pop();
    }
    ans[i]=res;
    stk.push({a[i],res});
}
```

## 左边第一个大，第一个大于等于，第一个小于等于

严格单调递减栈，非严格递减栈，非严格递增

## 右边第一个大等等

从右往左处理即可