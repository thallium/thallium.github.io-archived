---
published: true
title: Comparison of std::array and std::tuple / std::array和std::tuple的比较
category: 杂项/Miscellany 
tags: 
layout: post
math: true
---
I saw both who uses `std::array` and `std::tuple` as elements of `std::vector` so I want to see which one performs better and what's their pro and cons.

<!-- more -->
# Acknowledgement

The test is to sort 1e7 randomly generated data. It is just for a simple comparison and may not be rigorous.

Compile command:
`g++ -Wall -Wextra -O2 -std=c++1z -static  test.cpp -o test `


# array vs pair

As I expected, the pair is much faster than array.

|array	|pair|
|---|---|
1.275|	1.046
1.341|	1.016
1.571|	1.033
1.289|	1.044
1.258|	1.051
1.948|	1.043
1.543|	1.038
1.523|	1.168
1.296|	1.428
1.28|	1.016
average:	|
1.4324|	1.0883

# Three elements tuple vs array

The performance is surprisingly close:

array|	tuple
---|---
1.379|	1.227
1.373|	1.447
1.379|	1.158
1.366|	1.161
1.373|	1.561
1.368|	1.286
1.347|	1.134
1.374|	1.328
1.378|	1.454
1.47|	1.195
average:|	
1.3807	|1.2951

# Summary

When we only need a two-element pair, `std::pair` is obviously the best option. It's faster and easy to access the first and second element.

When we need a triple, in the older C++ standard, it's quite hard to change an element in tuple. However, in C++17, we can easily access the elements using structured bindings which looping a vector:
```cpp
for(auto& [a,b,c]:someVector){
    //...
}
```

Thus, it won't make a huge difference whether you choose tuple or array.