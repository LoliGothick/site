#operator<=(C++11)
```cpp
namespace std {
  template <class T, class U>
  bool operator<=(const shared_ptr<T>& a, const shared_ptr<U>& b) noexcept; // (1)

  template <class T>
  bool operator<=(const shared_ptr<T>& x, nullptr_t) noexcept;              // (2)

  template <class T>
  bool operator<=(nullptr_t, const shared_ptr<T>& x) noexcept;              // (3)
}
```
* nullptr_t[link /reference/cstddef/nullptr_t.md]

##概要
`shared_ptr`において、左辺が右辺以下かを判定する。

比較対象は、`shared_ptr`が指す値ではなく、`shared_ptr`が保持するポインタ値。これは「値ベース(value-based)な比較」と呼ばれる。「所有権ベース(ownership-based)な比較」は、[`owner_before()`](./owner_before.md)を参照。


##戻り値
- (1) : `!(b < a)`
- (2) : `!(nullptr < x)`
- (3) : `!(x < nullptr)`


##例
```cpp
#include <iostream>
#include <memory>

int main()
{
  std::cout << std::boolalpha;

  std::shared_ptr<int> p1(new int(3));
  std::shared_ptr<int> p2(new int(3));

  bool r1 = p1 <= p2;
  std::cout << r1 << std::endl;

  bool r2 = p1 <= nullptr;
  std::cout << r2 << std::endl;

  bool r3 = nullptr <= p1;
  std::cout << r3 << std::endl;
}
```

###出力例
```
false
false
true
```

##バージョン
###言語
- C++11

###処理系
- [GCC](/implementation#gcc.md): 4.3.6 (`nullptr`バージョン以外), 4.7.4
- [Clang libc++, C++11 mode](/implementation#clang.md): 3.0 (`nullptr`バージョン以外), 3.3
- [ICC](/implementation#icc.md): ?
- [Visual C++](/implementation#visual_cpp.md): ??