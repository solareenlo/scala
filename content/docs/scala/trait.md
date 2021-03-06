---
weight: 5
title: trait
---

# trait
- scala のオブジェクト指向プログラミングにおけるモジュール化の中心的な概念．
- class に近い機能を持ちながら実質的な多重継承が可能．

# 定義
```bash
trait <トレイト名> {
  (<フィールド定義> | <メソッド定義>)*
}
```

# 主な特徴
- 複数の trait を1つの class や trait に mixin できる．
- 直接インスタンス化できない．
  - これは trait が単体で使われることを想定しないため．
- クラスパラメータ（コンストラクタの引数）を取ることができない．
  - trait に抽象メンバーを持たせることで値を渡すことができる．
  - trait を class に継承させたり，インスタンス化のときに抽象メンバーを実装することで trait に値を渡すことができる．
