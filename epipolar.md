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
## 基本行列
![0c78d924cabff9ec8a093d0a0fcbca8c](https://github.com/Bucchiman/readme/assets/52972710/c92f6908-a4ff-46d4-864f-aaa4c163ef2c)
2カメラ間がステレオキャリブレーション済みのエピポーラ幾何を考える．この時，エピポーラ拘束を表現するのが，式(1)で表わされる 基本行列(Essential Matrix) の $E$
である
