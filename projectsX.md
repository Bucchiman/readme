
# 1. GNSS測位計算
### 1.1 ECEF
### 1.2 ENU
### 1.3 衛星データの活用


# 2. Extended Kalman filter
- ノイズの混合した観測データから、ノイズを除去して状態を逐次推定する手法の一つ。
- 状態方程式、観測方程式という2つの方程式をモデル化する。
- x_k, u_k, z_k, w_k, v_k
- f, h, 共分散行列Q_k, R_kは既知とする。
- 状態方程式: x_k = f(x_k-1, u_k) + w_k
- 観測方程式: z_k = h(x_k) + v_k

### 2.1 推定手順

### 2.2 短所
 - 線形の場合、最適解を与えるが、非線形の場合、最適解ではない。
 - 初期値が誤っている場合や、モデルが不適切の場合、推定値が発散していく可能性がある。
 - 逐次的に推定を行うため、一時の観測値の外れ値の影響を受けやすい。
 - 観測ノイズを正規分布とする仮定は、広く開けた場所では成り立つが、都市部などでは成立しない。


# 3. Factor graph
 - ノード: variable vertices, factor vertices
 - エッジ: variable vertices-factor verticesのみ
 - 関数の因数分解。多変数の確率密度関数が因数分解されると、確率変数間の関係がわかりやすくなる?



# term
- ENU : the local East, North, Up coordinate system
- ECEF : the Earth-centered, Earth-fixed coordinate system, that is, geocentric coordinate system
- GNSS : Global Navigation Satellite System.
- GNSS/INS integration
- INS : inertial navigation system
- Kalman filter
- LC integration : loosely coupled integration.
- TC integration : tightly coupled integration.
- UTC integration : ultra-tightly coupled integration.



# kalman filterによるloosely coupled integration
# kalman filterによるtightly coupled integration
# factor graphによるGNSS-INSSintegration



## reference

- https://navi.ion.org/content/68/2/315
- https://www.researchgate.net/publication/355164217_GNSSINS_Integration_Kalman_Filter-Loose_Coupling_Master%27s_degree_course_in_Mobile_Mapping_and_Navigation_Systems_Polytechnic_University_Warsaw
- https://pdfs.semanticscholar.org/139c/f2241ec9a3a4f41eca798385d3612b40432f.pdf?_gl=1*1sckten*_ga*MTIyNDE5ODY5MS4xNjgxMzYxOTkw*_ga_H7P4ZT52H5*MTY4MTM2MTk4OS4xLjAuMTY4MTM2MTk5MS4wLjAuMA..
- https://dc.tsinghuajournals.com/cgi/viewcontent.cgi?article=1250&context=tsinghua-science-and-technology
- https://comm.ee.tut.ac.jp/~takeuchi/lecture/communication/.pdf
- https://smartech.gatech.edu/bitstream/handle/1853/45226/Factor Graphs and GTSAM A Hands-on Introduction GT-RIM-CP%26R-2012-002.pdf?sequence=1&isAllowed=y
- https://dellaert.github.io/files/Indelman13ras.pdf
- https://github.com/TixiaoShan/LIO-SAM
- https://www.jstage.jst.go.jp/article/jacc/54/0/54_0_358/_pdf
- http://opendata.enri.go.jp/~fks442/K_MUSEN/


- https://dc.tsinghuajournals.com/cgi/viewcontent.cgi?article=1250&context=tsinghua-science-and-technology
- https://dynamic-positioning.com/proceedings/dp2017/Sensors-%20Russell%20-%20presentation.pdf
- https://rpg.ifi.uzh.ch/docs/IROS20_Cioffi.pdf
- http://web.stanford.edu/group/scpnt/gpslab/pubs/papers/Alban_IONNTM_2003.pdf


- https://github.com/neufieldrobotics/simple_vslam.git
- https://github.com/neufieldrobotics/simple_vslam/blob/master/docs/tutorial.md
- https://navi.ion.org/content/navi/68/2/315.full.pdf
- https://www.youtube.com/watch?v=f5bIh96SRsk
- https://www.mdpi.com/1424-8220/22/23/9297
- https://gtsam.org/tutorials/intro.html
- https://github.com/borglab/gtsam






# Camera, LiDARをヒュージョンさせた速度推定手法の調査
イメージカメラ、LiDARなどのセンサーを使って速度測定を行うため、センサーフュージョンと2D/3Dト
ラッキング技術を調査・検討・評価を実施し、ロボット搭載に適したモデルを選定する。選定したモデルを
ROS2ノードとして実装する。
## RGB/LiDAR Detection+Tracking
- EagerMOT
- DeepFusionMOT
- PolarMOT
- JRMOT
- TransFusion

## RGB/LiDAR Detection
- BEVFusion
- MVX-Net
- BSH-Det3D
- 3D Dual-Fusion

## 2D/3D Tracking
- SORT/DeepSORT
- StrongSORT
- EagerMOT

## RGB Detection+Tracking
- SORT/DeepSORT
- Tracktor
- QDTrack
- ByteTrack
- OC-SORT
- FairMOT
- UniTrack

## RGB Detection
- YOLOX
- EfficientDet

# Camera

# Ladar
## Detection
- RODNet

## 3D Object Detection
- CenterFusion
- CRF-Net
- RODNet
- BIRANet
- Radar Guided Dynamic Visual Attention for Resource-Efficient RGB Object Detection
- Destance Vehicle Detection Using Radar and Vision

## Ladar/LiDAR/Camera 3D Object Detection
- RadarVoxelFusionNet
- SeeingThroughFog

## LadarRGB-Depth Obstacle Detection(for people)
- Fusion of Millimeter wave Ladar and RGB-Depth sensors for assisted navigation of the visually impaired
- Unifying Obstacle Detection, Recognition and Fusion Based on Millimeter Wave Radar and RGB-Depth Sensors for the Visually Impaired


# 06/19 速度推定

## 3D物体検出ステレオ
index	Model	Year	Repository	License	Input	Output	Backbone	Inference/fps/flops	Ap	LongRange	memory	Remarks	候補の可能性
1	DSGN++	2022	o	Apache-2.0	"Binomicular
Images(384x1248)"	"3D Detection
+
Depth Map"	PSMNet(or ResNet34)	5.62fps on a RTX2080Ti	67.37	50m	6.0 GB	"Siamese Network
Joint Stereo-LiDAR copy-paste"	
2	Pseudo-Stereo for Monocular 3D Object Detection in Autonomous Driving	2022	o	記載なし	-	-		-	-	-	-	-	
3	ESGN	2022	x	---	Binomicular images + LiDAR	3D Detection	Resnet34	16.13fps on a RTX3090	38.42	-	-		x(リポジトリがない)
4	LIGA-Stereo	2021	o	Apache-2.0	Binomicular Images(KiTTY)	3D Detection	"UNet(Stereo)
Sparse Conv(LiDAR)"	2.86 on TITAN Xp	64.66	-	4.9 GB	"LiDAR + Stereo
3 classes"	"x(マシン-fpsでorinの
実装は難しい)"
5	YOLOStereo3D	2021	o	Apache-2.0	Binomicular images(288x1280)	"3D Detection
+
Disparity Estimation"	resnet34	"20fps on a RTX3090(ESGNから参照)
including file IO, 12.5fps"	41.25	-	"1.75 GB
(Training 7GB/4batch)"		"o(fps, 他の論文でも
高速なアルゴリズムと指定紹介)"
6	Stereo CenterNet	2021	x	---	Binomicular images			25fps on a RTX3090(ESGNから参照)		-	-	"3D detection
realtime performance"	x(リポジトリがない)
7	DSGN	2020	o	MIT	Biomicular images(1382x512/512x256)	"3D Detection
+
Disparity Estimation"	PSMNet	1.49fps on a RTX3090/V100	52.18	-	6.5 GB		
8	RTS3D	2020	o	MIT	Binomicular images	3D Detection	-	"25.64fps on a RTX3090(ESGNから参照)
33.12fps"	45.58	-	-	Siamese Network	o
9	OC Stereo	2020	x	---	Binomicular images			2.86	41.44	-	-		x(リポジトリがない)
10	Stereo R-CNN	2019	o	MIT	Binomicular images(600pixels)	3D Detection	FPN, ResNet101	3.33 a RTX3090(ESGNから参照)	34.05	75mまでの評価あり	-		


## 3D物体検出 LiDAR+Camera
index	Model	Year	Repository	License	Input	Output	Backbone	FPS		Accuracy(mAP)		LongRange	memory	Remarks
								Kitti	NuScenes	Kitti	NuScenes			
1	DFR-FastMOT​	2023​	x	-								-	-	
2	BEVFusion​	2022​	o	Apache-2.0​	"RGB(256x704)
+
LiDAR point cloud"	"3D Detection
+
Task Specific Heads"	"Swin-T(RGB)
+
VoxelNet(LiDAR)"	-	8.4(RTX3090)	-	75	30m以上の評価あり	-	10 class
3	MVX-Net​	2019​	o	Apache-2.0​	"RGB
+
LiDAR point cloud"	3D Detection	-	40	-	65.2	-	-	-	MMDetection3Dの一部​
4	BSH-Det3D​	2023​	o(No Sourcecode)	​				20.83	-	77	-	-	-	Code is coming soon.​
5	3D Dual-Fusion​	2022​	o	-	"Multi view camera RGB()
+
LiDAR point cloud"	3D Detection	VoxelNet(LiDAR)	-	-	79.3	70.6	30m以上の評価あり	-	
6	Fast-CLOCs​	2022​	-​	-​								-	-	​
7	UVTR​	2022​	o	Apache-2.0​	"RGB(256/512/1024/2048)
+
LiDAR point cloud(32 beam 20Hz)"	3D Detection	"VoxelNet(LiDAR)
Resnet50(RGB)"	-	9.3(V100)	-	65	30m以上の評価あり	-	10 class




## others
Index	Algorithm	Year	Repository	License	Input	output	Inference/fps/flops	Backbone	Remarks
1	UniAD​	2023​	o	Apache-2.0​	"Multi-view sensor?
or
Vision-only input?
両対応している?"	Planning a car position(xyz)	1.8(A100)	Resnet101	"CVPR2023 Award Candidate
Theme: ""Planning-oriented Autonomous Driving""
Detection,Tracking,Mapping,Motion prediction, Occupancy map prediction,planning(次の行動の予定)について一つのnetworkで行うフレームワークの論文"
2	VoxelNeXt​	2023​	o	Apache-2.0​	LiDAR point cloud	BEV	"Sparse CNN/33.6GFLOPS(CenterPoint:62.9FLOPS)
Detection Head/5.1GFLOPS(CenterPoint:123.7FLOPS)"		"3D Detection and Tracking
Theme: ""VoxelNeXt: Fully Sparse VoxelNet for 3D Object Detection and Tracking""
演算量(FLOPs)についてCenterPointと比較(Sparse CNN: CenterPointより1/2削減, Head: CenterPointより1/10以上削減)"
3	MSeg3D​	2023​	o	-	"multi-camera images
+
LiDAR point cloud"	semantic segmentation			"Multi-modal Semantic segmentation Segmentation
Theme: ""MSeg3D: Multi-modal 3D Semantic Segmentation for Autonomous Driving"""
4	3D consistent patch attack​	2023​	-​	-​					3D Detection
5	MSMDFusion​	2023​	o	Apache-2.0​					"3D Detection(+Tracking?​)
Theme: ""MSMDFusion: Fusing LiDAR and Camera at Multiple Scales with Multi-Depth Seeds for 3D Object Detection"""
6	FlatFormer	2023	x	-	LiDAR point cloud	3D Detection	16.1(Orin)		"the first point cloud transformer that
achieves real-time performance on edge GPUs(Orinで>10fps達成)"


## 3D物体検出 LiDAR
Index	Model	Year	Repository	License	Input	Output	Backbone	FPS		Accuracy(mAP)		LongRange	memory	Remarks
								KiTTY	NuScenes	Kitti	NuScenes			
1	Point-GNN	2020	o	MIT	LiDAR point cloud	3D Detection	-	1.55fps on a GTX1070		79.47				
2	CenterPoint	2020	o	MIT	LiDAR point cloud	3D Detection + Tracking	VoxelNet	"13fps on Titan RTX
13.6fps on Orin(FlatFormerから引用)"	11fps on Titan RTX					
3	VoxelNeXt​	2023​	o	Apache-2.0​	LiDAR point cloud	BEV	Sparse Conv	"Sparse CNN/33.6GFLOPS(CenterPoint:62.9FLOPS)
Detection Head/5.1GFLOPS(CenterPoint:123.7FLOPS)"		72.2				"3D Detection and Tracking
Theme: ""VoxelNeXt: Fully Sparse VoxelNet for 3D Object Detection and Tracking""
演算量(FLOPs)についてCenterPointと比較(Sparse CNN: CenterPointより1/2削減, Head: CenterPointより1/10以上削減)"
	FlatFormer	2023	x	-	LiDAR point cloud	3D Detection		16.1fps(Orin)		71.4				"the first point cloud transformer that
achieves real-time performance on edge GPUs(Orinで>10fps達成)"
