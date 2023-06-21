<!--
 FileName:      programming
 Author:        8ucchiman
 CreatedDate:   2023-06-22 08:29:08
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     8ucchiman.jp
 Description:   ---
-->


# Closures
[関数内関数とクロージャの違い](https://codor.co.jp/python/closure)
- 関数内関数
```python
    def outer(a):
        def inner(b):
            print(b)
            return
        return inner(a)
```

- closure
```python
    def outer(a):
        def inner():
            print(a)      # スコープが有効であるためこのようにかける
            return
        return inner
```

## メリット
`closureによりある状態を保持したまま、違う処理を実行することができる` <br />
```python
    def outer(a):
        def inner():
            print(a)      # スコープが有効であるためこのようにかける
            return
        return inner      # inner関数のアドレス
    closure = outer(10)   # 
```

