<!--
 FileName:      assembler
 Author:        8ucchiman
 CreatedDate:   2023-09-07 12:30:51
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     http://nw.tsuda.ac.jp/lec/arm64/mac_m1/
 Description:   ---
-->


# アセンブリ言語
## ディレクティブ

### 現在のセクションを指定するディレクティブ
```bash
    section segname, sectname [[[, type], attribute], sizeof_stub]
```

| ディレクティブ |     セクション    | Description |
|----------------|-------------------|-------------|
|.text           |\_\_TEXT, \_\_text | 命令を配置するセクションを開始 |
|.data           |\_\_Data, \_\_data | 初期値を持つデータを配置するセクションを開始 |

### Location Counterを動かすディレクティブ
```bash
    .align     align_expression [ , 1byte_fill_expression [, max_bytes_to_fill] ]
    .p2align   align_expression [ , 1byte_fill_expression [, max_bytes_to_fill] ]
    .p2alignw  align_expression [ , 2byte_fill_expression [, max_bytes_to_fill] ]
    .p2alignl  align_expression [ , 4byte_fill_expression [, max_bytes_to_fill] ]
    .align32   align_expression [ , 4byte_fill_expression [, max_bytes_to_fill] ]
```

### データ生成用ディレクティブ
```bash
    .ascii ["string"] [, "string"] ...
    .asciiz ["string"] [, "string"] ...
```
