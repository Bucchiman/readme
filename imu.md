<!--
 FileName:      imu
 Author:        8ucchiman
 CreatedDate:   2023-08-16 10:34:02
 LastModified:  2023-01-25 10:56:12 +0900
 Reference:     https://myenigma.hatenablog.com/entry/2015/11/09/183738
 Description:   ---
-->



# コリオリ力
$F = 2mv\omega$




# IMU
直交3軸に対して、3つのジャイロセンサと3つの加速度センサとして構成し、


- 誤差をなくすために、地磁気センサ、傾斜センサ、GPSを取り付けることもある


## 振動ジャイロ
MEMSのシリコン阻止を振動させ、その時にセンサに回転運動が加わると、シリコン素子にコリオリ力が発生
-> $\omega$を計算して


## Fiber Optic Gyro(FOG)





## まとめ
| センサ | ジャイロ | 加速度センサ | 電子コンパス | GPS | 角速度出力 | 加速度出力 | ロール角・ピッチ角出力 | ヨー角出力 | 位置出力 |
|--------|----------|--------------|--------------|-----|------------|------------|------------------------|------------|----------|
|IMU     |    o     |      o       |       x      |  x  |     o      |     o      |          x             |      x     |     x    |
|VR      |    o     |      o       |       x      |  x  |     o      |     o      |          o             |      x     |     x    |
|AHRS    |    o     |      o       |       o      |  x  |     o      |     o      |          o             |      o     |     x    |
|GPS/INS |    o     |      o       |       o      |  o  |     o      |     o      |          o             |      o     |     o    |



## 評価指標
- バイアス誤差
