<!--
 FileName:      rust
 Author:        8ucchiman
 CreatedDate:   2023-05-24 14:51:02
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     https://doc.rust-lang.org/rust-by-example/index.html
 Description:   ---
-->




# 所有権のルール
- Each value has an owner.
- There can only be one owner at a time.
- When the owner goes out of scope, the value will be dropped.


# Result型
列挙型(enum)と呼ぶ。
列挙子はOk, Err。


# クレート
- バイナリクレート  : 実行可能形式(cargo newで作ったプロジェクト)
- ライブラリクレート: 依存ファイルとしてcargo.tomlのdependenciesに追記するクレート

# Cargo.lock
再現可能な環境をあらかじめ用意することが目的。


# shadowing
`前に定義した変数と同じ名前の変数を新しく宣言すること` `前の変数を覆い隠す`
```
    let guess: u32 = guess + 1;
    let x = 5;
    let x = x + 1;
```

## mutとの違い


# 構造体

## 構造体更新記法
```rust
    struct User {
        username: String,
        email: String,
        sign_in_count: u64,
        active: bool,
    }

    let user1 = User {
        email: String::from("someone@example.com"),
        username: String::from("someusername123"),
        active: true,
        sign_in_count: 1,
    };

    let user2 = User {
        email: String::from("another@example.com"),
        username: String::from("anotherusername567"),
        ..user1      # 残りのフィールドはuser1にする
    };
```

## タプル構造体
`異なる型を生成する名前付きフィールドのないタプル構造体`
```
    struct Color(i32, i32, i32);
    struct Point(i32, i32, i32);

    let black = Color(0, 0, 0):
    let origin = Point(0, 0, 0);
```

## ユニット構造体
`フィールドのないユニット様構造体`

