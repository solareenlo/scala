---
weight: 6
title: type parameter
---

# 型パラメータ（type parameter）
- class を作る時点では何の type か特定できない場合に用いる．
- どの type でも同じ処理を抽象化できる．

# 定義
```bash
class <クラス名>[<型パラメータ1>, <型パラメータ2>, ...](<クラス引数>) {
  (<フィールド定義>|<メソッド定義>)*
}
```

# Tuple1 ~ Tuple22
- `Tuple1` ~ `Tuple22` （数字は要素数）とは，複数の引数を操作するあらかじめ用意された便利なクラスのこと．

```scala
val m = 7
val n = 3

// 下の2つは同じこと
new Tuple2(m / n, m % n)
(m / n, m % n)
// (Int, Int) = (2, 1)
```

# 変位指定（variance）
## 非変（invariant）
- Scala は基本的に型パラーメータは非変（invariant）．
- 下記の場合に A と B の型が一致していないといけない．
```scala
val: G[A] = G[B]
```

## 共変（covariant）
```scala
class G[+A]
val: G[B] = G[A]
```
- A は B を継承していないといけない．

## 反変（contravariant）
```scala
class G[-A]
val: G[A] = G[B]
```
- A は B を継承していないといけない．
- わかりやすい例は関数の型．
  - 関数の引数の型は戻り値の型を継承していなくてはならない．

# 型パラメータの境界（bounds）
## 上限境界（upper bounds）
- 自分がどのような型を継承しているかを指定するもの．
- 対象の型（自分）を別の型のサブタイプに制限するもの．
- `自分 <: 上限の型`

## 下限境界（lower bounds）
- 自分がどのような型のスーパータイプであるかを指定するもの．
- 対象の型（自分）が別の型のスーパータイプであることを宣言するもの．
- `下限の型 >: 自分`
