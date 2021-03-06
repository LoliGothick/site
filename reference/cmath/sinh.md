#sinh
* cmath[meta header]
* std[meta namespace]
* function[meta id-type]
* [mathjax enable]

```cpp
namespace std {
  float sinh(float x);

  double sinh(double x);

  long double sinh(long double x);

  double sinh(Integral x);   // C++11
}
```
* Integral[italic]

##概要
算術型の双曲線正弦（ハイパボリックサイン）を求める。


##戻り値
引数 `x` の双曲線正弦を返す。


##備考
$$ f(x) = \sinh x $$


##例
```cpp
#include <cmath>
#include <iostream>

int main() {
  std::cout << std::fixed;
  std::cout << "sinh(-1.0) = " << std::sinh(-1.0) << std::endl;
  std::cout << "sinh(0.0)  = " << std::sinh(0.0) << std::endl;
  std::cout << "sinh(1.0)  = " << std::sinh(1.0) << std::endl;
}
```

###出力
```
sinh(-1.0) = -1.175201
sinh(0.0)  = 0.000000
sinh(1.0)  = 1.175201
```

##バージョン
###言語
- C++03
- C++11

###処理系
- [Clang](/implementation.md#clang): 1.9, 2.9, 3.1
- [GCC](/implementation.md#gcc): 3.4.6, 4.2.4, 4.3.5, 4.4.5, 4.5.1, 4.5.2, 4.6.1, 4.7.0
- [GCC, C++11 mode](/implementation.md#gcc): 4.3.4, 4.4.5, 4.5.2, 4.6.1, 4.7.0
- [ICC](/implementation.md#icc): 10.1, 11.0, 11.1, 12.0
- [Visual C++](/implementation.md#visual_cpp) 7.1, 8.0, 9.0, 10.0

####備考
特定の環境で `constexpr` 指定されている場合がある。（独自拡張）
- GCC 4.6.1 以上


##実装例
マクローリン展開によって近似的に求めることができる。

$$ \sinh x = \sum_{n = 0}^{\infty} \frac{1}{(2n + 1)!} x^{2n + 1} \quad \mathrm{for~all} \; x $$
