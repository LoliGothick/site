#swap (非メンバ関数)
* thread[meta header]
* std[meta namespace]
* function[meta id-type]
* cpp11[meta cpp]

```cpp
namespace std {
  void swap(thread& x, thread& y) noexcept;
}
```

##概要
2つの`thread`オブジェクトを入れ替える


##効果
`x.`[`swap`](swap.md)`(y);`


##戻り値
なし


##例外
投げない


##例
```cpp
#include <thread>

int main()
{
  std::thread th1([]{ /*...*/ });
  std::thread th2;

  std::swap(th1, th2);

  th2.join();

  return 0;
}
```
* swap[color ff0000]


###出力
```
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): 
- [GCC, C++11 mode](/implementation.md#gcc): 4.7.0
- [ICC](/implementation.md#icc): ??
- [Visual C++](/implementation.md#visual_cpp) ??


##参照


