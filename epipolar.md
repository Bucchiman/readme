<!--
 FileName:      epipolar
 Author:        8ucchiman
 CreatedDate:   2023-05-24 16:58:33
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     https://cvml-expertguide.net/terms/epipolar-geometry/
 Description:   ---
-->


# エピポーラ幾何
`左画像上の対応点を右画像上で探索するときに用いる `
![372px-Epipolar_geometry svg](https://github.com/Bucchiman/readme/assets/52972710/fff759fa-ba6b-46d7-82f6-a05080ddead5)

- 基線(baseline) ... ２台のカメラ中心を結んだ，線分 $O_{L}, O_{R}$ <br />
- エピポール (epipole) ... 基線が，画像平面を通る点を エピポール(epipole) と呼ぶ．$e_{L}$が左画像のエピポールで$e_{R}$が右画像のエピポール <br />
- エピポーラ平面 (epipolar plane) ... シーン中の注目点 $X$と，２台のカメラ中心 $O_{L}$, $O_{R}$が形成する平面 <br />
- エピポーラ線 (epipolar line) ... エピポーラ平面が画像平面と交差する断面が，画像上に作る線 

# エピポーラ拘束と三角測量
## エピポーラ拘束
[参考](https://qiita.com/Thought_Nibbler/items/9cb7c2637000eecc1a30) <br />
![0c78d924cabff9ec8a093d0a0fcbca8c](https://github.com/Bucchiman/readme/assets/52972710/c92f6908-a4ff-46d4-864f-aaa4c163ef2c) <br />
Pにある物体は、カメラ$C$からは$p$, カメラ$C'$からは$p'$に映る。
以下のように定義する。
- $`p=\begin{pmatrix} x_p & y_p & 1\end{pmatrix}`$
    - $`C`$を原点とした同次座標系
- $`p'=\begin{pmatrix} x'_{p} & y'_{p} & 1 \end{pmatrix}`$
    - $`C'`$を原点とした同次座標系

ここで以下のことが言える。
1. カメラ$`C`$から見て$`p`$に物体が映っている際、カメラ$`C'`$でその物体が映る位置はエピポーラ線上のどこかに限定できる
2. カメラ$`C'`$から見て$`p'`$に物体が映っている際、カメラ$`C`$でその物体が映る位置はエピポーラ線上のどこかに限定できる<br />
これをエピポーラ拘束と呼ぶ。

## 基本行列
`ステレオキャリブレーション済みのエピポーラ幾何について基本行列$p'^{T}Ep=0$であらわされる$E$`
![0c78d924cabff9ec8a093d0a0fcbca8c](https://github.com/Bucchiman/readme/assets/52972710/c92f6908-a4ff-46d4-864f-aaa4c163ef2c) <br />
1. カメラ$`C`$から見て$`p`$に物体が映っている際、カメラ$`C'`$でその物体が映る位置はエピポーラ線上のどこかに限定できる<br />
数式を用いて展開する。<br />
1. $`p'=\begin{pmatrix} x'_{p} & y'_{p} & 1\end{pmatrix}`$はエピポーラ線上にある
エピポーラ線の方程式を$`ax+by+c = 0`$とする。ここで$`ax+by+c = \begin{pmatrix} a \\ b \\ c \end{pmatrix}\begin{pmatrix} x \\ y \\ 1`$より$`l=\begin{pmatrix} a \\ b \\ c\end{pmatrix}`$は法線ベクトルである。
1. $`p' = \begin{pmatrix} x_{p'} && y_{p'} && 1\end{pmatrix}`$は$'p'\dot l = ax_{p'}+by_{p'}+c=0'$を満たす。
1. $`p'=\begin{pmatrix} x_{p'} && y_{p'} && 1\end{pmatrix}`$は$`l`$と常に垂直である。<br />

これを満たす$`l`$を決める。$`p'`$はエピポーラ面上にあるため、$`l`$はエピポーラ面に垂直であればよい。
すなはち、$`l=t\times Rp`$と表せられる。
- 理由
   - 2つのベクトルの外積はそれらのベクトルが張る平面に垂直である。(外積定義)
   - $`t`$はエピポーラ面上のベクトルである。
   - $`Rp`$はどちらもエピポーラ面上のベクトルである。<br />
1. $`p'=\begin{pmatrix} x_{p'} && y_{p'} && 1\end{pmatrix}`$は$`p'\times(t\times Rp) = 0`$を満たす
ベクトル$`t`$と行列$`R`$を一括で扱うため変形する。
ベクトル$`t`$による外積と同じ作用となる行列は歪対称行列$`[t]_{x}`$として表せられる。
1. $`p'=\begin{pmatrix} x_{p'} && y_{p'} && 1 \end{pmatrix}`$は$`p'\dot ([t]_{x}Rp) = 0`$を満たす
$`E=[t]_{x}R`$とおく。この$`E`$を基本行列と呼ぶ。
基本行列$`E`$を用いて次のように書ける。
$$p'^{T}Ep = 0$$
