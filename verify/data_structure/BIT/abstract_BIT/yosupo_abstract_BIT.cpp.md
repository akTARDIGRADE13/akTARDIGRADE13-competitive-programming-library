---
data:
  _extendedDependsOn:
  - icon: ':warning:'
    path: lib/data_structure/BIT/abstract_BIT.hpp
    title: abstract_BIT
  _extendedRequiredBy: []
  _extendedVerifiedWith: []
  _isVerificationFailed: false
  _pathExtension: cpp
  _verificationStatusIcon: ':warning:'
  attributes:
    links:
    - https://judge.yosupo.jp/problem/point_add_range_sum
  bundledCode: "#line 1 \"verify/data_structure/BIT/abstract_BIT/yosupo_abstract_BIT.cpp\"\
    \n#define PROBLEM \"https://judge.yosupo.jp/problem/point_add_range_sum\"\n\n\
    #line 2 \"lib/data_structure/BIT/abstract_BIT.hpp\"\n\n#include <functional>\n\
    #include <vector>\n\nnamespace akTARDIGRADE13 {\n\ntemplate <typename T> struct\
    \ BIT {\n    BIT() : n(0) {}\n    explicit BIT(int _n, function<T(T, T)> _fx,\
    \ function<T(T)> _inv, T _ex)\n        : n(_n + 1), vec(_n + 1, 0), fx(_fx), inv(_inv),\
    \ ex(_ex) {}\n\n    void add(int i, T x) {\n        ++i;\n        while(i < n)\
    \ {\n            vec[i] = fx(vec[i], x);\n            i += i & (-i);\n       \
    \ }\n    }\n\n    T sum(int i) {\n        if(i == 0)\n            return 0;\n\
    \        T ret = ex;\n        while(i > 0) {\n            ret = fx(vec[i], ret);\n\
    \            i -= i & (-i);\n        }\n        return ret;\n    }\n\n    T query(int\
    \ l, int r) { return fx(sum(r), inv(sum(l))); }\n\n    int binary_search(T x)\
    \ {\n        int ret = 0, r = 1;\n        while(r < n)\n            r = r << 1;\n\
    \        while(r > 0) {\n            if(ret + r < n && vec[ret + r] < x) {\n \
    \               x = fx(x, rev(vec[ret + r]));\n                ret += r;\n   \
    \         }\n            r = r >> 1;\n        }\n        return ret;\n    }\n\n\
    \  private:\n    int n;\n    std::vector<T> vec;\n    std::function<T(T, T)> fx;\n\
    \    std::function<T(T)> inv;\n    const T ex;\n};\n\n}\n#line 4 \"verify/data_structure/BIT/abstract_BIT/yosupo_abstract_BIT.cpp\"\
    \n\n#include <iostream>\n\nint main() {\n    int n, q;\n    std::cin >> n >> q;\n\
    \    auto fx = [](long long x, long long y)->long long{return x+y;};\n    auto\
    \ inv = [](long long x)->long long{return -x;};\n    long long ex = 0;\n    akTARDIGRADE13::BIT<long\
    \ long> bt(n, fx, inv, ex);\n    for(int i = 0; i < n; ++i) {\n        int x;\n\
    \        std::cin >> x;\n        bt.add(i, x);\n    }\n    while(q--) {\n    \
    \    int t;\n        std::cin >> t;\n        if(!t) {\n            int p, x;\n\
    \            std::cin >> p >> x;\n            bt.add(p, x);\n        } else {\n\
    \            int l, r;\n            std::cin >> l >> r;\n            std::cout\
    \ << bt.query(l, r) << std::endl;\n        }\n    }\n    return 0;\n}\n"
  code: "#define PROBLEM \"https://judge.yosupo.jp/problem/point_add_range_sum\"\n\
    \n#include \"lib/data_structure/BIT/abstract_BIT.hpp\"\n\n#include <iostream>\n\
    \nint main() {\n    int n, q;\n    std::cin >> n >> q;\n    auto fx = [](long\
    \ long x, long long y)->long long{return x+y;};\n    auto inv = [](long long x)->long\
    \ long{return -x;};\n    long long ex = 0;\n    akTARDIGRADE13::BIT<long long>\
    \ bt(n, fx, inv, ex);\n    for(int i = 0; i < n; ++i) {\n        int x;\n    \
    \    std::cin >> x;\n        bt.add(i, x);\n    }\n    while(q--) {\n        int\
    \ t;\n        std::cin >> t;\n        if(!t) {\n            int p, x;\n      \
    \      std::cin >> p >> x;\n            bt.add(p, x);\n        } else {\n    \
    \        int l, r;\n            std::cin >> l >> r;\n            std::cout <<\
    \ bt.query(l, r) << std::endl;\n        }\n    }\n    return 0;\n}"
  dependsOn:
  - lib/data_structure/BIT/abstract_BIT.hpp
  isVerificationFile: false
  path: verify/data_structure/BIT/abstract_BIT/yosupo_abstract_BIT.cpp
  requiredBy: []
  timestamp: '2024-03-09 02:47:29+09:00'
  verificationStatus: LIBRARY_NO_TESTS
  verifiedWith: []
documentation_of: verify/data_structure/BIT/abstract_BIT/yosupo_abstract_BIT.cpp
layout: document
redirect_from:
- /library/verify/data_structure/BIT/abstract_BIT/yosupo_abstract_BIT.cpp
- /library/verify/data_structure/BIT/abstract_BIT/yosupo_abstract_BIT.cpp.html
title: verify/data_structure/BIT/abstract_BIT/yosupo_abstract_BIT.cpp
---