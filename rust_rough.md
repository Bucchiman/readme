<!--
 FileName:      rust
 Author:        8ucchiman
 CreatedDate:   2023-05-24 14:51:02
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     https://doc.rust-lang.org/rust-by-example/index.html
 Description:   ---
-->


# OverView
- 1. ことはじめ
    - 1.1 インストール
    - 1.2 Hello, World!
    - 1.3 Hello, Cargo!
    - 1.4 まとめ

- 2. 数当てゲームをプログラムする
    - 2.1 新規プロジェクトの立ち上げ
    - 2.2 予想を処理する
    - 2.3 秘密の数字を生成する
    - 2.4 予想と秘密の数字を比較する
    - 2.5 ループで複数回の予想を可能にする
    - 2.6 まとめ

- 3. 一般的なプログラミングの概念
    - 3.1 変数と可変性
    - 3.2 データ型
    - 3.3 関数
        - 3.3.1 関数の引数
        - 3.3.2 関数本体は、文と式を含む
        - 3.3.3 戻り値のある関数
    - 3.4 コメント
    - 3.5 フロー制御
        - 3.5.1 if式
            - 3.5.1.1 else if で複数の条件を扱う
            - 3.5.1.2 let文内でif式を使う
        - 3.5.2 ループでの繰り返し
            - 3.5.2.1 loopでコードを繰り返す
            - 3.5.2.2 whileで条件付ループ
            - 3.5.2.3 forでコレクションを覗き見る
    - 3.6 まとめ

- 4. 所有権を理解する
    - 4.1 所有権とは?
    - 4.2 参照と借用
    - 4.3 スライス型
    - 4.4 まとめ

- 5. 構造体を使用して関係のあるデータを構造化する
    - 5.1 構造体を定義し、インスタンス化する
    - 5.2 構造体を使ったプログラム例
    - 5.3 メソッド記法
    - 5.4 まとめ

- 6. Enumとパターンマッチング
    - 6.1 Enumを定義する
    - 6.2 matchフロー制御演算子
    - 6.3 if letで簡潔なフロー制御
    - 6.4 まとめ

- 7. 肥大化していくプロジェクトをパッケージ、クレート、モジュールを利用して管理する
    - 7.1 パッケージとクレート
    - 7.2 モジュールを定義して、スコープとプライバシーを制御する
    - 7.3 モジュールツリーの要素を示すためのパス
    - 7.4 useキーワードでパスをスコープに持ち込む
    - 7.5 モジュールを複数のファイルに分割する
    - 7.6 まとめ

- 8. 一般的なコレクション
    - 8.1 ベクタで一連の値を保持する
    - 8.2 文字列でUTF-8でエンコードされたテキストを保持する
    - 8.3 キーとそれに紐づいた値を八種マップに格納する
    - 8.4 まとめ

- 9. エラー処理
    - 9.1 panic!で回復不能なエラー
    - 9.2 Resultで回復可能なエラー
    - 9.3 panic!すべきかするまいか
    - 9.4 まとめ

- 10. ジェネリック型、トレイト、ライフタイム
    - 10.1 関数を抽出することで重複を取り除く
    - 10.2 ジェネリックなデータ型
    - 10.3 トレイト: 共通のふるまいを定義する
    - 10.4 ライフタイムで参照を検証する
    - 10.5 ジェネリックな型引数、トレイト境界、ライフタイムを一度に

- 11. 自動テストを書く
    - 11.1 テストの記述法
    - 11.2 テスト関数の構成
    - 11.3 テストの実行のされ方を制御する
    - 11.4 テストの体系化
    - 11.5 まとめ

- 12. 入出力プロジェクト: コマンドラインプログラムを構築する
    - 12.1 コマンドライン引数を受け付ける
    - 12.2 ファイルを読み込む
    - 12.3 リファクタリングしてモジュール性とエラー処理を向上させる
    - 12.4 テスト駆動開発でライブラリの機能を開発する
    - 12.5 環境変数を取り扱う
    - 12.6 標準出力ではなく標準エラーにエラーメッセージを書き込む
    - 12.7 まとめ

- 13. 関数型言語の機能: イテレータとクロージャ
    - 13.1 クロージャ: 環境をキャプチャできる匿名関数
    - 13.2 一連の要素をイテレータで処理する
    - 13.3 他のイテレータを生成するメソッド

- 14. CargoとCrates.ioについてより詳しく
    - 14.1 リリースプロファイルでビルドをカスタマイズする
    - 14.2 Crates.ioにクレートを公開する
    - 14.3 Cargoのワークスペース
    - 14.4 cargo installでCrates.ioからバイナリをインストールする
    - 14.5 独自のコマンドでCargoを拡張する
    - 14.6 まとめ

- 15. スマートポインタ
    - 15.1 ヒープのデータを指すBox<T>を使用する
    - 15.2 Derefトレイトでスマートポインタを普通の参照のように扱う
    - 15.3 Dropトレイトで片付け時のコードを走らせる
    - 15.4 Rc<T>は、参照カウント方式のスマートポインタ
    - 15.5 RefCell<T>と内部可変性パターン
    - 15.6 循環参照は、メモリをリークすることもある
    - 15.7 まとめ

- 16. 恐れるな!並行性
    - 16.1 スレッドを使用してコードを同時に走らせる
    - 16.2 メッセージ受け渡しを使ってスレッド間でデータを転送する
    - 16.3 状態共有並行性
    - 16.4 SyncとSendトレイトで拡張可能な並行性
    - 16.5 まとめ

- 17. Rustのオブジェクト指向プログラミング機能
    - 17.1 オブジェクト指向言語の特徴
    - 17.2 トレイトオブジェクトで異なる型の値を許容する
    - 17.3 ブジェクト指向デザインパターンを実装する
    - 17.4 まとめ

- 18. パターンとマッチング
    - 18.1 パターンが使用されることのある個所全部
    - 18.2 論駁可能性: パターンが合致しないかどうか
    - 18.3 パターン記法
    - 18.4 まとめ

- 19. 高度な機能
    - 19.1 Unsafe Rust
    - 19.2 高度なトレイト
    - 19.3 高度な型
    - 19.4 高度な関数とクロージャ
    - 19.5 まとめ
    - 19.6 マクロ
    - 19.7 まとめ

- 20. 最後のプロジェクト: マルチスレッドのWebサーバを構築する
    - 20.1 シングルスレッドのWebサーバを構築する
    - 20.2 シングルスレッドサーバをマルチスレッド化する
    - 20.3 正常なシャットダウンと片付け
    - 20.4 まとめ

- 付録
    - 付録A: キーワード
    - 付録B: 演算子と記号
    - 付録C: 導出可能なトレイト
    - 付録D: 便利な開発ツール
    - 付録E: Edition
    - 付録F: 本の翻訳
    - 付録G: Rustの作られ方と"Nightly Rust"





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
# 3. 一般的なプログラミングの概念
## 3.2 データ型
- Rustは静的型付き言語 ... コンパイル時に全ての変数の型が判明している必要がある。

<details>
 <summary> 3.3 関数 </summary>
 <div>
<details>
 <summary> 3.3.2 関数本体は、文と式を含む </summary>
 <div>
`rustは式指向言語` `文: 何らかの動作をして値を返さない命令` `式: 結果値に評価` <br />
- 文の例
  
```rust
    fn main() {
        let y = 6;
    }
```
```rust
    fn main() {
        let x = (let y = 6);    // 文は値を返さないからエラー
    }
```

- 式の例 <br />
```rust
    fn main() {
        let x = 6;
        let y = {       // 新しいスコープを作る際に使用するブロック
            let x = 3;
            x + 1
        };
    }
```
 </div>
  </details>
  <details>
   <summary> 3.3.3 戻り値のある関数 </summary>
   <div>
    
```rust
    fn five() -> i32 {
        5              // 式として値を返す
    }
    fn main() {
        let x = five();
    }
```
    
   </div>
  </details>
 </div>
  </details>
 

## 3.5 フロー制御
<details>
    <summary> 3.5.1 if式 </summary>
    <div>
        <details>
            <summary> 3.5.1.1 else if で複数の条件を扱う</summary>
            <div>
            </div>
        </details>
        <details>
            <summary> 3.5.1.2 let文内でif式を使う</summary>
            <div>
             
   ```rust
      fn main() {
                        let condition = true;
                        let number = if condition {
                            5
                        }
                        else {
                            6
                        };
                        println!("The value of number is: {}", number);
                    }
```

```rust
                    fn main() {
                        let condition = true;
                        let number = if condition {
                            5
                        } else {
                            "six"     // if, elseアームの互換性が合わずエラー
                        };
                        println!("The value of number is: {}", number);
                    }
```
            </div>
        </details>
    </div>
</details>
</details>

<details>
    <summary> 3.5.2 ループでの繰り返し </summary>
    <div>
        <details>
            <summary> 3.5.2.1 loopでコードを繰り返す </summary>
            <div>
                `loopキーワード` <br />
                ```rust
                    fn main() {
                        loop {
                            println!("again!");
                        }
                    }
                ```
            </div>
        </details>
        <details>
            <summary> 3.5.2.2 whileで条件付ループ </summary>
            <div>
                ```rust
                    fn main() {
                        let mut number = 3;
                        while number != 0 {
                            println!("{}!", number);
                            number = number - 1;
                        }
                    }
                ```
            </div>
        </details>
        <details>
            <summary> 3.5.2.3 forでコレクションを覗き見る </summary>
            <div>
                - 非推奨コード
                    - 添え字の長さが間違えばパニック
                    - ループごとに境界値チェックが行われ、遅い <br />
                ```rust
                    fn main() {
                        let a = [10, 20, 30, 40, 50];
                        let mut index = 0;

                        while index < 5 {
                            println!("the value is: {}", a[index])
                            index = index + 1;
                        }
                    }
                ```

                - 推奨コード
                    - 終端を超える恐れもなく安全 <br />
                ```rust
                    fn main() {
                        let a = [10, 20, 30, 40, 50];
                        for element in a.iter() {
                            println!("the value is: {}", element);
                        }
                    }
                ```

                - 逆順
                ```rust
                    fn main() {
                        for number in (1..4).rev() {
                            println!("{}!", number);
                        }
                    }
                ```
            </div>
        </details>
    </div>
</details>
</details>

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


