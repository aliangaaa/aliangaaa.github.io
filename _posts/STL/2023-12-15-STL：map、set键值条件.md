---
layout: post
title: STL：lower_bound、upper_bound
category: STL
tags: Essay
keywords: 
description: 
---

unordered\_*map、unordered*\_set键不可为vector、pair...

map、set中键可以为vector、pair、set...

```cpp
        set<unordered_set<int>> pset;
        unordered_set<int> qs;
        qs.insert(1);
        qs.insert(2);
        pset.insert(qs);   //  [error]set键不可为unordered，map同
```

```cpp
        set<set<int>> pset;
        set<int> qs;
        qs.insert(1);
        qs.insert(2);
        pset.insert(qs);
        set<int> ps;
        ps.insert(1);
        ps.insert(2);
        if(pset.count(ps)) {
            cout<< 1<<endl;
        }          //  "1"
```

```cpp
        map<map<int,int>, int> pmap;
        map<int, int> qs;
        map<int, int> ps;
        qs[1] = 2;
        qs[2] = 3;
        pmap[qs] = 8;
        ps[1] = 2;
        ps[2] = 3;
        if(pmap.count(ps)){
            cout<< 1 <<endl;
        }            // "1"
```

