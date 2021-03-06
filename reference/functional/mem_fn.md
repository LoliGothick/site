#mem_fn
* functional[meta header]
* std[meta namespace]
* function template[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  template <class R, class T>
  unspecified mem_fn(R T::* pm);
}
```
* unspecified[italic]


##概要
与えられたメンバ関数を呼び出す [*Callable*](/reference/functional/callable.md) オブジェクトを生成して返す。


##戻り値
`fn(t, a2, ..., aN)` の呼出しが [*INVOKE*](invoke.md)`(pm, t, a2, ..., aN)` と等価となる [*Callable*](callable.md) オブジェクト `fn` を返す。

`fn` の型には、必要に応じて `typedef` 名 `argument_type`, `first_argument_type`, `second_argument_type`, `result_type` が定義される。


##例外
投げない


##例
```cpp
#include <functional>
#include <memory>
#include <iostream>

int main() {
  auto l = std::make_shared<std::less<int>>();
  std::cout << std::boolalpha;
  std::cout << (*l)(3, 5) << std::endl;
  std::cout << std::mem_fn(&std::less<int>::operator ())(l, 3, 5) << std::endl;
  std::cout << std::bind(*l, std::placeholders::_1, 5)(3) << std::endl;

  // std::cout << std::bind(l, std::placeholders::_1, 5)(3) << std::endl;
  //   エラー！ std::shared_ptr< std::less<int> > は Callable ではない

  // mem_fn() で包むと Callable になる
  std::cout <<
      std::bind(std::mem_fn(&std::less<int>::operator ()), l, std::placeholders::_1, 5)(3)
  << std::endl;
}
```

###出力
```
true
true
true
true
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc):
- [GCC, C++11 mode](/implementation.md#gcc): 4.7.0
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp): ??


##参照
- [LWG Issue 2048. Unnecessary `mem_fn` overloads](http://www.open-std.org/jtc1/sc22/wg21/docs/lwg-defects.html#2048)
    - 不必要なオーバーロードを、C++14で削除

