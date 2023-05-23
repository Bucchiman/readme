# トピック
`メッセージ通信方式`
実行ファイル同士が、メッセージを送信する際の、通信方式。
```

     +------------------------+               topic                   +------------------------+
     |  Node A        message |   message      message     message    |  Node B        message |
     |   送信バッファ message |  -----------------------------------> |   受信バッファ message |
     +------------------------+                                       +------------------------+

```

## msgファイル
トピック通信における型を定義。
- フィールドタイプ
- フィールドネーム

e.g.  geometry_msgs/Twist.msg
```
    Vector3 linear
    Vector3 angular
```

# srvファイル
サービス通信における型を定義。
```
    sensor_msgs/CameraInfo camera_info
    ---
    bool success
    string status_message
```

ハイフンは、サービス要請メッセージ(上段)とサービス応答メッセージ(下段)を分けるために用いられる。
