#m
* random[meta header]
* std[meta namespace]
* lognormal_distribution[meta class]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
result_type m() const;
```

##概要
生成する範囲の平均値を取得する。


##戻り値
構築時に設定された、値の範囲の平均値を返す。


##例
```cpp
#include <iostream>
#include <random>

int main()
{
  std::lognormal_distribution<> dist(0.0, 1.0);

  double m = dist.m();
  std::cout << m << std::endl;
}
```

###出力
```
0
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 
- [GCC, C++11 mode](/implementation.md#gcc): 4.7.2
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp) ??


##参照


