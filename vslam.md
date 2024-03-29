<!-- FileName: vslam
 Author: 8ucchiman
 CreatedDate: 2023-03-15 17:06:58 +0900
 LastModified: 2023-03-27 11:09:18 +0900
 Reference: 8ucchiman.jp
-->


# VSLAMの幾何学
- Perspective-n-Point(PnP) ... Localization
- 三角測量                 ... Mapping
- エピポーラ幾何           ... Initialization
- バンドル調整             ... Mapping
- ポーズグラフ最適化       ... Loop closure


# 全体的なアルゴリズム
## カメラのキャリブレーション
カメラの内部パラメータKの推定が必要
エピポーラ幾何により求めることが困難

チェス盤の画像を複数の角度から撮影
 - 焦点距離
 - 画像の中心
 - レンズの歪み

## マップの初期化

## トラッキング&マップの更新



# 座標系の幾何学的関係
`画像座標系` `カメラ座標系` `世界座標系`
![image](https://github.com/Bucchiman/readme/assets/52972710/aa801f84-36a0-46e8-b942-d448647fbd4b)

# 座標変換
`内部パラメータ: カメラ->画像` `外部パラメータ: 世界->カメラ` <br />
3D点を画像平面に投影するためには、ワールド座標系->カメラ座標系->画像座標系
の順に変換する。
カメラ->画像の変換を表すのが内部パラメータ, ワールド座標系->カメラ座標系を表すのが外部パラメータである。

# カメラから画像へ
$$
    s \begin{pmatrix} u \\ v \\ 1 \end{pmatrix} = 
      \begin{pmatrix} f_x & 0 & c_x \\
                      0 & f_y & c_y \\
                      0 & 0 & 1
      \end{pmatrix}
      \begin{pmatrix}
        X_c \\ Y_c \\ Z_c
      \end{pmatrix}
$$

# 世界からカメラへ
$$
    $ \begin{pmatrix} X_c \\ Y_c \\ Z_c \\ 1 \end{pmatrix} =
      \begin{pmatrix} r_{11} && r_{12} && r_{13} && t_1 \\
                      r_{21} && r_{22} && r_{23} && t_2 \\
                      r_{31} && r_{32} && r_{33} && t_3 \\
                      0 & 0 & 0 & 1
      \end{pmatrix}
      \begin{pmatrix} X_w \\ Y_w \\ Z_w \\ 1 \end{pmatrix}
$$


# Perspective-n-Point(PnP)問題
`未知: 外部パラメータ` `既知: 内部パラメータ` `3次元座標の既知な点とその画像中の画素の複数ペアから外部パラメータを算出する問題。`
$`su = K\begin{pmatrix}R & T\end{pmatrix} X_w`$

- u: 画像座標
- K: 内部パラメータ
- X_w: 3次元点

## 解法
`初期値の有無によって解法の仕方が変わる`
### 初期値あり
- 反復最適化を用いる手法

### 初期値無し
- EPnP


# 三角測量
`3次元空間の復元` `未知: 3次元座標` `外部パラメータ` <br />
$`su = K\begin{pmatrix}R & T\end{pmatrix} X_w`$
- 既知: 外部パラメータの既知な2つの視点に移る点の画素
- 未知: 3次元座標

## ざっくりイメージ
`一辺とその両端の角度が決まれば3点目の位置が決まる`
- 未知: d
- 既知: α, β, baseline
```


                 +
               - |-
             -   | -
           -     |  -
         -      d|   -
       -         |    -
     - α         |   β -
   +--------------------+
          baseline


```




## カメラの投影モデル
各軸の焦点距離を(fu, fv)、光学中心を(cu, cv)とする。内部パラメータKは以下のように定義できる。
```
       | fu  0  cu |
   K = | 0   fv cv |
       | 0   0  1  |
```
$$
    K = \begin{pmatrix} f_u & 0   & c_u \\
                        0   & f_v & c_v \\
                        0   & 0   & 1 \end{pmatrix}
$$


Kの第3行をのぞいた行列をK'とする。
カメラ座標系の3D点
$`χc=\begin{pmatrix}X_c & Y_c & Z_c\end{pmatrix}^T`$
は以下の式で画像平面上の点
$`z=\begin{pmatrix}u & v\end{pmatrix}^T`$
に投影される。
```
    z = 1 / Zc K'χc
```

ワールド座標系->カメラ座標系の変換は各カメラの外部パラメータを考える必要がある。
カメラの位置姿勢が並進ベクトル$`tcw`$と回転行列$`Rcw`$で表されるとき、ワールド座標系の3D点$`χw=(Xw, Yw, Zw)T`$をカメラ座標系に変換すると、
$`χc=[Rcw|tcw]χw`$となる。
```
    z = 1/Zc K'[Rcw|tcw]χw
```






# エピポーラ幾何
[コンピュータビジョン最前線](https://speakerdeck.com/ksakurada/visual-slamru-men-fa-zhan-falseli-shi-toji-chu-falsexi-de)
3次元のシーンを撮影した画像間の対応点には拘束条件がある。
それを表す時が基礎行列Fと基本行列Eである。
2つのカメラと3D点の空間的対応関係は、エピポーラ幾何と呼ぶ。
基礎行列Fは画像座標系, 基本行列Eはカメラ座標系での拘束条件を表し、カメラの内部パラメータKが既知の場合は基本行列Eを、未知の場合は基礎行列Fを用いることで、
カメラ姿勢[R|t]を推定することができる。


```


                 +-
                 |  -
                 |    -
                 |      -
                 |        -                                                         -+
                 |   x      +                                               -        |
                 |          |                                        -               |
                 |          |                                +-         x            |
                 +-         |                                |                       |
        o           -    x+++++++++++++++++++++++++++++++++++++++++x                 |
                      -     |                                |                       |
                        -   |                                |                      -+
                          - |                                |              -
                            +                                |       -
                                                             +-                 o


```


## 基礎行列
`内部パラメータがキャリブレーションされていない場合`
基礎行列$`F`$は3x3行列,カメラの内部パラメータKと2つのカメラの外部パラメータ$`[R|t]`$の両方の情報を含む。
これはエピポーラ拘束と呼ばれ、一方の$`z1`$が決まればもう一方の画像上の対応点$`z2`$に関する制約を与えることができる。
カメラ1$`\begin{pmatrix} u_1 & v_1\end{pmatrix}$とカメラ2$\begin{pmatrix} u_2 & v_2 \end{pmatrix}`$の制約が決まる。
```
            | f11 f12 f13 ||u1|
   (u2 v2 1)| f21 f22 f23 ||v1| = z2TFz1 = 0
            | f31 f32 f33 ||1 |
```
$$ \begin{pmatrix}
    u_2 & v_2 & 1
  \end{pmatrix}
  \begin{pmatrix}
    f_{11} & f_{12} & f_{13} \\
    f_{21} & f_{22} & f_{23} \\
    f_{31} & f_{32} & f_{33}
  \end{pmatrix}
  \begin{pmatrix}
    u_1 \\
    v_1 \\
    1
  \end{pmatrix}
  = z_{2}^{T}Fz_{1} = 0
$$


画像$`I_1`$上の点$`z_1`$に対応する画像$`I_2`$上のエピポーラ線は$`l_2=Fz_1`$であらわされる。
これを、上の式に代入すると$`z^T_2l_2`$となる。
同様に画像$`I_2`$上の点$`z_2`$に対応する画像$`I_1`$上のエピポーラ線は、$`l_1=F^Tz_2`$で表される。

上の式を展開します。
$$
\begin{pmatrix}
    u_2 & v_2 & 1
  \end{pmatrix}
  \begin{pmatrix}
    f_{11} & f_{12} & f_{13} \\
    f_{21} & f_{22} & f_{23} \\
    f_{31} & f_{32} & f_{33}
  \end{pmatrix}
  \begin{pmatrix}
    u_1 \\
    v_1 \\
    1
  \end{pmatrix}
$$
$$
\begin{pmatrix}
    u_2f_{11}+v_2f_{21}+f_{31} & u_2f_{12}+v_2f_{22}+f_{32} & u_2f_{13}+v_2f_{23}+f_{33}
\end{pmatrix}
\begin{pmatrix}
    u_1 \\
    v_1 \\
    1
\end{pmatrix}
$$
$$
    u_1u_2f_{11}+u_1_2f_{21}+u_1f_{31}+u_2v_1f_{12}+v_1v_2f_{22}+v_1f_{32}+u_2f_{13}+v_2f_{23}+f_{33}
$$

こうして線形方程式で表すことができました。



## 基本行列
基本行列Eは対応店ペアpとp'の幾何関係を表す行列である。
基本行列は回転行列Rとtを歪対称行列表現に変換した[t]xの積で計算される。
```
    E = R[t]x
```

ここで、エピポーラ拘束により、Cp, C'p', tの3つのベクトルが同一平面上に存在するので、基本行列Eを用いて2画像間のエピポーラ拘束を表現できる。+
```
    p'TEp = 0
```








# VSLAMの計算手順
1. Initialization: 世界座標系と初期空間形状の設定
2. Localization  : カメラの位置姿勢の算出
3. Mapping       : 空間形状作成
4. Loop closure  : ループ検出及び空間形状の補正
5. Relocalization: カメラ位置姿勢の再算出
