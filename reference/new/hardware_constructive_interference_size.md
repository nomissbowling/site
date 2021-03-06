# hardware_constructive_interference_size
* new[meta header]
* std[meta namespace]
* variable[meta id-type]
* cpp17[meta cpp]

```cpp
namespace std {
  inline constexpr std::size_t hardware_constructive_interference_size = implementation-defined;
}
```

## 概要
2つのオブジェクトに一時局所的にアクセスできる最大サイズ。

この変数と対になる[`hardware_destructive_interference_size`](hardware_destructive_interference_size.md)は、各変数がそれぞれ別なキャッシュラインに乗るようアライメントを調整するものだが、この変数は、複数の変数を意図的に同じキャッシュラインに乗せるためのアライメントサイズである。


## 備考
- この変数の値は、`alignof(`[`max_align_t`](/reference/cstddef/max_align_t.md)`)`以上である


## 例
```cpp
#include <iostream>
#include <new>

struct X {
  int a;
  int b;
};

// Xクラスのメンバ変数aとbが、同じキャッシュラインに乗ることを意図する
static_assert(sizeof(X) <= std::hardware_constructive_interference_size);

int main()
{
  std::cout << "hardware_constructive_interference_size : "
            << std::hardware_constructive_interference_size
            << std::endl;
}
```
* std::hardware_constructive_interference_size[color ff0000]
* threads.push_back[link /reference/vector/vector/push_back.md]


### 出力例
(実装がないため、動作確認できていない)


## バージョン
### 言語
- C++17

### 処理系
- [Clang, C++17 mode](/implementation.md#clang):
- [GCC, C++17 mode](/implementation.md#gcc):
- [Visual C++](/implementation.md#visual_cpp): ??


## 参照
- [N4523 `constexpr std::thread::hardware_{true,false}_sharing_size`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4523.html)
- [P0154R0 `constexpr std::hardware_{constructive,destructive}_interference_size`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0154r0.html)
- [P0154R1 `constexpr std::hardware_{constructive,destructive}_interference_size`](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)
