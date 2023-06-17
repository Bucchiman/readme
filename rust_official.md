<!--
 FileName:      rust_official
 Author:        8ucchiman
 CreatedDate:   2023-06-17 20:18:43
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     8ucchiman.jp
 Description:   ---
-->


- 3. 基本的な方
    - 3.1 固定長数値
        - 3.1.1 
        - 3.1.2 
        - 3.1.3 
    - 3.2 真偽値型
    - 3.3 文字
    - 3.4 タプル
    - 3.5 ポインタ型
        - 3.5.1 参照
        - 3.5.2 Box
        - 3.5.3 rawポインタ
    - 3.6 配列、ベクタ、スライス
        - 3.6.1 配列
        - 3.6.2 ベクタ
        - 3.6.3 スライス
    - 3.7 文字列型
        - 3.7.1 文字列リテラル
        - 3.7.2 バイト文字列
        - 3.7.3 メモリ上の文字列
        - 3.7.4 文字列String
        - 3.7.5 文字列の使用
        - 3.7.6 他の文字列に類する型
    - 3.8 型エイリアス
    - 3.9 基本型の先にあるもの
- 4. 所有権と移動
    - 4.1 所有権
    - 4.2 移動
        - 4.2.1 移動を伴うほかの操作
        - 4.2.2 移動と制御フロー
        - 4.2.3 移動とインデックス参照される値
    - 4.3 コピー型: 移動の例外
    - 4.4 RcとArc: 所有権の共有
- 5. 参照
    - 5.1 値への参照
    - 5.2 参照の使い方
        - 5.2.1 Rustの参照 vs C++の参照
        - 5.2.2 参照の代入
        - 5.2.3 参照への参照
        - 5.2.4 参照の比較
        - 5.2.5 参照はnullにはならない
        - 5.2.6 任意の指揮への参照の借用
        - 5.2.7 スライスとトレイトオブジェクトへの参照
    - 5.3 参照の安全性
        - 5.3.1 ローカル変数の借用
        - 5.3.2 仮引数として参照を受け取る場合
        - 5.3.3 参照を関数に渡す
        - 5.3.4 返り値としての参照
        - 5.3.5 参照を含む構造体
        - 5.3.6 個別の生存期間パラメータ
        - 5.3.7 生前期間パラメータの省略
    - 5.4 共有と変更
    - 5.5 オブジェクトの海に立ち向かう
- 6. 式
    - 6.1 式言語
    - 6.2 優先順位と結合性
    - 6.3 ブロックとセミコロン
    - 6.4 宣言
    - 6.5 ifとmatch
    - 6.6 if let式
    - 6.7 ループ
    - 6.8 ループ内の制御フロー
    - 6.9 return式
    - 6.10 なぜRustにはloop式があるのか
    - 6.11 関数呼び出しとメソッド呼び出し
    - 6.12 フィールドと要素
    - 6.13 参照演算子
    - 6.14 算術演算子、ビット演算子、比較演算子、論理演算子
    - 6.15 代入
    - 6.16 型キャスト
    - 6.17 クロージャ
    - 6.18 その先へ
- 7. エラー処理
    - 7.1 パニック
        - 7.1.1 スレッドの巻き戻し
        - 7.1.2 アボート
    - 7.2 Result
        - 7.2.1 エラーのキャッチ
        - 7.2.2 Result型のエイリアス
        - 7.2.3 エラーの表示
        - 7.2.4 エラーの伝播
        - 7.2.5 複数種類のエラーへの対応
        - 7.2.6 起こるはずのないエラーの処理
        - 7.2.7 エラーを無視する
        - 7.2.8 main()でのエラー処理
        - 7.2.9 カスタムエラー型の宣言
        - 7.2.10 なぜResultを使うのか
- 8. クレートとモジュール
    - 8.1 クレート
        - 8.1.1 エディション
        - 8.1.2 ビルドプロファイル
    - 8.2 モジュール
        - 8.2.1 モジュールのネスト
        - 8.2.2 モジュールの複数ファイルへの分割
        - 8.2.3 パスとインポート
        - 8.2.4 標準とプレリュード
        - 8.2.5 use宣言をパブリックにする
        - 8.2.6 構造体のフィールドをpubにする
        - 8.2.7 staticと定数
    - 8.3 プログラムからライブラリへ
    - 8.4 src/binディレクトリ
    - 8.5 属性
    - 8.6 テストとドキュメント
        - 8.6.1 結合テスト
        - 8.6.2 ドキュメント
        - 8.6.3 ドキュメントテスト
    - 8.7 依存ライブラリの指定
        - 8.7.1 バージョン
        - 8.7.2 Cargo.lock
    - 8.8 クレートのcrates.ioでの公開
    - 8.9 いいものをもっと
- 9. 構造体
    - 9.1 名前付きフィールド型構造体
    - 9.2 タプル型構造体
    - 9.3 ユニット型構造体
    - 9.4 構造体のメモリ配置
    - 9.5 implによるメソッド定義
        - 9.5.1 selfをBox、Rc、Arcで渡す
        - 9.5.2 型関連関数
    - 9.6 型関連定数
    - 9.7 ジェネリック構造体
    - 9.8 生存期間パラメータを持つジェネリック構造体
    - 9.9 定数パラメータを持つジェネリック構造体
    - 9.10 一般的なトレイトの自動実装
    - 9.11 内部可変性
- 10. 列挙型とパターン
    - 10.1 列挙型
        - 10.1.1 データを保持する列挙型
        - 10.1.2 列挙型のメモリ上での表現
        - 10.1.3 列挙型を用いたリッチなデータ構造
        - 10.1.4 ジェネリック列挙型
    - 10.2 パターン
        - 10.2.1 パターン内のリテラル、変数、ワイルドカード
        - 10.2.2 タプルと構造体パターン
        - 10.2.3 配列パターンとスライスパターン
        - 10.2.4 参照パターン
        - 10.2.5 マッチガード
        - 10.2.6 複数の可能性へのマッチ
        - 10.2.7 @パターンによる束縛
        - 10.2.8 パターンが使える場所
        - 10.2.9 二分木へのデータ追加
    - 10.3 大きな絵の中での位置づけ
- 11. トレイトとジェネリクス
    - 11.1 トレイトの使い方
        - 11.1.1 トレイトオブジェクト
        - 11.1.2 ジェネリック関数と語パラメータ
        - 11.1.3 どちらを使うべきか
    - 11.2 トレイトの定義と実装
        - 11.2.1 デフォルトメソッド
        - 11.2.2 トレイトと第三者の定義した型
        - 11.2.3 トレイトでのSelf
        - 11.2.4 サブトレイト
        - 11.2.5 型関連関数
    - 11.3 完全修飾メソッド呼び出し
    - 11.4 型と型の関係を定義するトレイト
        - 11.4.1 関連型: イテレータはどう動く
        - 11.4.2 ジェネリックトレイト: 演算子オーバーロードはどう機能するか
        - 11.4.3 impl Trait
        - 11.4.4 トレイトの関連定数
    - 11.5 制約のリバースエンジニアリング
    - 11.6 基盤としてのトレイト
- 12. 演算子オーバーロード
    - 12.1 算術演算子とビット演算子
        - 12.1.1 単項演算子
        - 12.1.2 二項演算子
        - 12.1.3 複合代入演算子
    - 12.3 順序比較
    - 12.4 IndexとIndexMut
    - 12.5 その他の演算子
- 13. ユーティリティトレイト
    - 13.1 Drop
    - 13.2 Sized
    - 13.3 Clone
    - 13.4 Copy
    - 13.5 DerefとDerefMut
    - 13.6 Default
    - 13.7 AsRefとAsMut
    - 13.8 BorrowとBorrowMut
    - 13.9 FromとInto
    - 13.10 TryFromとTryInto
    - 13.11 ToOwned
    - 13.12 BorrowとToOwnnedの動作例: つつましいCow
- 14. クロージャ
    - 14.1 変数のキャプチャ
        - 14.1.1 借用するクロージャ
        - 14.1.2 盗むクロージャ
    - 14.2 関数型とクロージャ型
    - 14.3 クロージャの性能
    - 14.4 クロージャと安全性
        - 14.4.1 殺すクロージャ
        - 14.4.2 FnOnce
        - 14.4.3 FnMut
        - 14.4.4 クロージャのCopyとClone
    - 14.5 コールバック
    - 14.6 クロージャの効率的な利用
- 15. イテレータ
    - 15.1 IteratorトレイトとIntoIteratorトレイト
    - 15.2 イテレータの作成
        - 15.2.1 iterメソッドとiter_mutメソッド
        - 15.2.2 IntoIteratorの実装
        - 15.2.3 from_fnとsuccessors
        - 15.2.4 drainメソッド
        - 15.2.5 他のイテレータの生成方法
    - 15.3 イテレータアダプタ
        - 15.3.1 mapとfilter
        - 15.3.2 filter_mapとflat_map
        - 15.3.3 flatten
        - 15.3.4 takeとtake_while
        - 15.3.5 skipとskip_while
        - 15.3.6 peekable
        - 15.3.7 fuse
        - 15.3.8 反転可能イテレータとrev
        - 15.3.9 inspect
        - 15.3.10 chain
        - 15.3.11 enumerate
        - 15.3.12 zip
        - 15.3.13 by_ref
        - 15.3.14 clonedとcopied
        - 15.3.15 cycle
    - 15.4 イテレータの消費
        - 15.4.1 単純な累積: count, sum, product
        - 15.4.2 max, min
        - 15.4.3 max_by, min_by
        - 15.4.4 max_by_key, min_by_key
        - 15.4.5 アイテム列の比較
        - 15.4.6 any, all
        - 15.4.7 position, rposition, ExactSizeIterator
        - 15.4.8 foldとrfold
        - 15.4.9 try_foldとtry_rfold
        - 15.4.10 nthとnth_back
        - 15.4.11 last
        - 15.4.12 find, rfind, find_map
        - 15.4.13 コレクションの作成: collectとFromIterator
        - 15.4.14 Extendトレイト
        - 15.4.15 partition
        - 15.4.16 for_eachとtry_for_each
    - 15.5 ユーザ定義イテレータの実装
- 16. コレクション
    - 16.1 概要
    - 16.2 Vec<T>
        - 16.2.1 要素へのアクセス
        - 16.2.2 イテレート処理
        - 16.2.3 ベクタの伸長と縮小
        - 16.2.4 連結
        - 16.2.5 分割
        - 16.2.6 入れ替え
        - 16.2.7 フィル
        - 16.2.8 ソートと検索
        - 16.2.9 スライスの比較
        - 16.2.10 ランダムな要素
        - 16.2.11 Rustでは無効化エラーは生じない
    - 16.3 VecDeque<T>
    - 16.4 BinaryHeap<T>
    - 16.5 HashMap<K,V>とBTreeMap<K,V>
        - 16.5.1 エントリ
        - 16.5.2 マップに対するイテレート
    - 16.6 HashSet<T>とBTreeSet<T>
        - 16.6.1 セットのイテレート
        - 16.6.2 値が等しいが別のものの場合
        - 16.6.3 セット全体に対する演算
    - 16.7 ハッシュ
    - 16.8 ハッシュアルゴリズムのカスタマイズ
    - 16.9 標準コレクションを超えて

## 3.1 固定長数値
### 3.1.1 整数型
- C, C++ ... size_t, ptrdiff_t
- Rust ... usize, isize
### 3.1.2 チェック付き演算、ラップ演算、飽和演算、オーバーフロー演算
```rust
    let mut i: i32 = 1;
    loop {
        // panic: multiplication overflowed いずれのビルドでもエラー
        i = i.checked_mul(10).expect("multiplication overflowed");
    }
```
#### チェック付き演算
#### ラップ演算
#### 飽和演算
#### オーバーフロー演算
### 3.1.3 浮動小数点数
## 3.2 真偽値型
## 3.3 文字
## 3.4 タプル
- e.g. <br />
```rust
    let text = "I see the eigenvalue in thine eye";
    let (head, tail) = text.split_at(21);
    assert_eq!(head, "I see the eigenvalue ");
    assert_eq!(tail, "in thine eye");
```
- e.g. <br />
```rust
    let text = "I see the eigenvalue in thine eye";
    let temp = text.split_at(21);
    let head = temp.0;
    let tail = temp.1;
    assert_eq!(head, "I see the eigenvalue ");
    assert_eq!(tail, "in thine eye");
```

### unit type
0要素のタプル
- std::mem::swap
```rust
    fn swap<T>(x: &mut T, y: &mut T)
    # -> fn swap<T>(x: &mut T, y: &mut T) -> ();
```

- write_image <br />
```rust
    fn write_image -> Result<(), std::io::Error)
    # エラーが起きればstd::io::Errorを返すが、成功時には何も返さないこと
```

## 3.5 ポインタ型
### 3.5.1 参照
`&T` `&mut T` <br />
- rustにはnull参照を作る方法がない
- &x ... xへの参照を借用する
- &T <br />
変更不能な共有参照。
ある値に対して複数の共有参照をもつくことができるが、値を読み出すことしかできない。
Cのconst T*に相当

- &mut T <br />
排他的な可変参照。参照先の値を読み出し、変更することができる。CのT*に相当

### 3.5.2 Box
ヒープ上に値を確保するもっとも簡単な方法
```rust
    let t = (12, "eggs");
    let b = Box::new(t);    # ヒープ上にタプルを確保
```

### 3.5.3 rawポインタ


## 3.6 配列、ベクタ、スライス
### 3.6.1 配列
```rust
    let lazy_caterer: [u32; 6] = [1, 2, 4, 7, 11, 16];
    let taxonomy = ["Animalia", "Arthropoda", "Insecta"];

    assert_eq!(lazy_caterer[3], 7);
    assert_eq!(taxonomy.len(), 3);
```

```rust
    let mut sieve = [true; 10000];
    for i in 2..100 {
        if sieve[i] {
            let mut j = i*i;
            while j < 10000 {
                sieve[j] = false;
                j += i;
            }
```

## 3.6 配列、ベクタ、スライス
メモリ上の値の列を表現する方は３つ
- 型[T; N] <br />
型TのN個の値の配列を表す。
新しい要素を追加したり、縮小したりすることはできない。

- 型Vec<T> <br />
Tのベクタで、道的に確保される慎重可能なT型の値の列を表す。
ベクタの要素はヒープ上に作られる。

- 型&[T]と&mut [T] <br />
Tの共有スライス及びTの可変スライス。
配列、ベクタなどの一部の連続した要素への参照である。

### 3.6.1 配列
`配列のメソッドはスライスのメソッドとして使える`

```rust
    let lazy_caterer: [u32; 6] = [1, 2, 4, 7, 11, 15];
    let taxonomy = ["animal", "hoge", "geho"];
    let mut sieve = [true; 100000];
```

```rust
    let mut chaos = [1, 3, 4, 5];
    chaos.sort();
```

### 3.6.2 ベクタ
`Vec<T> ... ヒープ上に確保されるサイズを変更することができる型Tの配列` <br />
- e.g. <br />
```rust
    let mut primes = vec![2, 3, 5, 7];
    assert_eq!(primes.iter().product::<i32>(), 210);
```

- e.g. <br />
```rust
    let mut pal = Vec::new();
    pal.push("step");
```

- e.g. <br />
```rust
    let v: Vec<i32> = (0..5).collect();
    assert_eq!(v, [0, 1, 2, 3, 4]);
```

- e.g. <br />
Vec<T>は3つの値をヒープ上に確保する。
```rust
    let mut v = Vec::with_capacity(2);
```

#### 宣言方法
- let mut primes = vec![2, 3, 5];    # マクロ
- let mut unko = vec![0; 1000];      # 配列リテラル様式
- let mut pal = Vec::new(); 
- let v: Vec<i32> = (0..5).collect();


### 3.6.3 スライス
```rust
    let v: Vec<f64> = vec![0.0, 0.707, 1.0, 0.707];
    let a: [f64; 4] = [0.0, -0.707, -1.0, -0.707];

    let sv: &[f64] = &v;
    let sa: &[f64] = &a;
```
```
              v                    a               sa     sv
    +-------------------------------------------------------------+
    |      |.|4|4|     |0.0|-0.707|-1.0|-0.707|   |.|4|  |.|4|    |
    +-------|------------|-------------------------|------|-------+
            | 容量,長さ  +-------------------------+      |
            +----------+       参照(所有権なし)           |
   所有権のあるポインタ | +-------------------------------+  参照(所有権なし)
               +-------|-|------------------------------+
               |      |0.0|0.707|1.0|0.707|             |
               +----------------------------------------+
```

```rust
    fn print(n: &[f64]) {
        for elt in n {
            println!("{}", elt);
        }
    }
    print(&a);      # 配列に対しても動作
    print(&v);      # ベクタに対して動作
    print(&[0..2]);
    print(&a[2..]);
    print(&sv[1..3]);
```

## 3.7 文字列型
### 3.7.1 文字列リテラル
### 3.7.2 バイト文字列
### 3.7.3 メモリ上の文字列
### 3.7.4 文字列String
### 3.7.5 文字列の使用
### 3.7.6 他の文字列に類する型
## 3.8 型エイリアス
## 3.9 基本方の先にあるもの
Cではif文やswitch文を式の中で使うことができない。
Rustは式言語なので使えることができる。

# 4. 所有権と移動
メモリ管理の特徴は2つある。
- メモリが、プログラマが選んだタイミングで適切に解放されること。これによってプログラムのメモリ消費を制御できる。
- 解法済みのオブジェクトへのポインタを使ってしまうことがないこと。このようなことをすると未定義動作になりクラッシュやセキュリティホールにつながる。

ダンぐリングポインタ: ポインタが存在するうちに値を開放すればそのポインタの参照する先がなくなること

## 4.1 所有権
### C, C++ <br />
std::stringオブジェクトは、そのバッファを所有している。
プログラムがstd::stringオブジェクトを破棄したらデストラクタを解放する。

```cpp
    std::string s = "frayed knot";
```

```
           バッファ,容量,長さ
    +-------------------------------------------------------------+
    |      |.|16|11|                                              |
    +-------|-----------------------------------------------------+
            |
            | <-------------------------> 16
    +-------------------------------------------------------------+
    |      |f|r|a|e|d| |k|n|o|t| | | | | |                        |
    +-------------------------------------------------------------+
              <---------------> 11
```

### Rust
`Box<T>はヒープ上の型Tの値へのポインタ` <br />
Box::new(v)を呼ぶと、ヒープ上にメモリを確保し、値vをそこに移動させ、そのヒープ空間を指すBoxを返す。
```rust
    {
        let point = Box::new((0.625, 0.5));
        let label = format!("{:?}", point):
        asswert_eq!(label, "(0.625, 0.5)");
    }
```
```
           point
    +-------------------------------------------------------------+
    |      |.|               |.|17|12|                            |
    +-------|-----------------|-----------------------------------+
            |                 +---------+
            |                           |
    +---------------------+        +----|--------------------------------+
    |      |0.625|0.5|    |        |   |(|0|.|6|2|5|,|0|.|5|)| | | | | | |
    +---------------------+        +-------------------------------------+
```

## 4.2 移動
### 4.2.1 移動を伴なう他の操作
### 4.2.2 移動と制御フロー
### 4.2.3 移動とインデック参照される値

## 4.3 コピー型: 移動の例外
## 4.4 RcとArc: 所有権の共有

# 5. 参照
## 5.1 値への参照

# 6. 式
## 6.1 式言語
`Cは式と文を厳密に分けている` `Rustは式言語である`
- 式
```rust
    5 * (fahr-32) / 9
```

- 文(値を持たない)
```rust
    for (; begin != end; ++begin) {
        if (*begin == target) {
            break;
        }
    }
```

## 6.3 ブロックとセミコロン
`ブロックは値を生み出す(;なし)` <br />
```rust
    let msg = {
        // let-declaration: semicolon is always required
        let dandelion_control = puffball.open();

        // expression + semicolon: method is called, return value dropped
        dandelion_control.release_all_seeds(launch_codes);

        // expression with no semicolon: method is called, return value stored in `msg`
        dandelion_control.get_status()
    }
```

## 6.4 宣言
`let name: type = expr;` `型と初期化式は省略できる` `シャドーイング: 変数を再び宣言して型を変える`

- e.g. アイテムの宣言 <br />
```rust
    use std::io;
    use std::cmp::Ordering;

    fn show_files() -> io::Result<()> {
        let mut v = vec![];

        fn cmp_by_timestamp_then_name(a: &FileInfo, b: &FileInfo) -> Ordering {
            a.timestamp.cmp(&b.timestamp).reverse().then(a.path.cmp(&b.path))
        }
        v.sort_by(cmp_by_timestamp_then_name);
    }
```

## 6.5 ifとmatch

- e.g. 定数
```rust
    match code {
        0 => println!("OK"),
        1 => println!("Wires Tangled"),
        2 => println!("User Asleep"),
        _ => println!("Unrecognized Error {}", code)
    }
```

- e.g. Option値
```rust
    match params.get("name") {
        Some(name) => println!("Hello, {}!", name),
        None => println!("Greetings, stranger.")
    }
```

## 6.6 if let式
`exprがpatternにマッチするならblock1が実行` `OptionやResultからデータを取り出すのに便利`
```rust
    if let pattern = expr {
        block1
    } else {
        block2
    }
```

- e.g.
```rust
    if let Some(cookie) = request.session_cookie {
        return restore_session(cookie);
    }
    if let Err(err) = show_cheesy_anti_robot_task() {
        log_robot_attempt(err);
        politely_accuse_user_of_being_a_robot();
    } else {
        session.mark_as_human();
    }
```

## 6.7 ループ
```rust
    while condition {
        block
    }

    while let pattern = expr {
        block
    }
    
    loop {
        block
    }

    for pattern in iterrable {
        block
    }
```

## 6.8 ループ内の制御フロー
```rust
    let answer = loop {
        if let Some(line) = next_line() {
            if line.starts_with("answer: ") {
                break line;
            }
        } else {
            break "answer: nothing";
        }
    };
```

## 6.9 return 式