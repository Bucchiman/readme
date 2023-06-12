
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


# 06/09 速度推定
## others o 
Index	Algorithm	Year	Repository	License	Input	output	fps	Backbone	Remarks
1	UniAD​	2023​	o	Apache-2.0​	"Multi-view sensor?
or
Vision-only input?
両対応している?"	Planning position(xyz)	1.8(A100)	Resnet101	"CVPR2023 Award Candidate
Theme: ""Planning-oriented Autonomous Driving""
Detection,Tracking,Mapping,Motion prediction, Occupancy map prediction,planning(次の行動の予定)について一つのnetworkで行うフレームワークの論文"
2	VoxelNeXt​	2023​	o	Apache-2.0​					"3D Detection and Tracking
Theme: ""VoxelNeXt: Fully Sparse VoxelNet for 3D Object Detection and Tracking""
演算量(FLOPs)についてCenterPointと比較(Sparse CNN: CenterPointより1/2削減, Head: CenterPointより1/10以上削減)"
3	MSeg3D​	2023​	o	-	"multi-camera images
+
Lidar point cloud"	semantic segmentation			"Multi-modal Semantic segmentation Segmentation
Theme: ""MSeg3D: Multi-modal 3D Semantic Segmentation for Autonomous Driving"""
4	3D consistent patch attack​	2023​	-​	-​					3D Detection
5	MSMDFusion​	2023​	o	Apache-2.0​					"3D Detection(+Tracking?​)
Theme: ""MSMDFusion: Fusing LiDAR and Camera at Multiple Scales with Multi-Depth Seeds for 3D Object Detection"""
6	FlatFormer	2023	x	-	-	"LiDAR point cloud
-> 3D Detection"	16.1(Orin)		"the first point cloud transformer that
achieves real-time performance on edge GPUs(Orinで>10fps達成)"

- CenterPoint
- CenterTrack

## 2d 3d tracking o 
index	Model	Year	Repository	License	Input	Output	Backbone	FPS - Tracking only		Accuracy - KITTI		LongRange	memory	Remarks
		Year	Repository	License	Input	Output	Backbone	Kitti	NuScenes	HOTA	AMOTA			
1	SORT/DeepSORT​	2016/2017​	o	Apache-2.0​										MMTracking​
			o	GPL-3.0​										Official​
			o	GPL-3.0​										Official​
2	StrongSORT​	2022​	o	GPL-3.0​										2D Tracking​
3	EagerMOT​	2021​	o	MIT​										Detectorを入れ替え​
4	MOTSFusion	2020	o	MIT​										

## 3D Detection + tracking(LiDAR+RGB) x
index	Model	Year	Repository	License	Input	Output	Backbone	FPS - Tracking only		Accuracy - KITTI		LongRange	memory	Remarks
		Year	Repository	License	Input	Output	Backbone	Kitti	NuScenes	HOTA	AMOTA			
1	MSMDFusion​	2023​	o	Apache-2.0​								-	-	CVPR2023​
2	DeepFusionMOT​	2022​	o	MIT​				110		75	0.635	-	-	IROS2022​
3	PolarMOT​	2022​	o	MIT​				170	33		0.664	-	-	ECCV2022​
4	TransFusion​	2022​	o	Apache-2.0​							0.718	-	-	CVPR2022​
5	EagerMOT​	2021​	o	MIT​				90	4		0.677	-	-	ICRA2021​
6	AlphaTrack​	2021​	-​	-​								-	-	​
7	JRMOT​	2020​	o	MIT​				25		70		-	-	​
8	StrongSORT	2022​	o	GPL-3.0​				50		77		-	-	

## 3D Detection (LiDAR+RGB) o 
index	Model	Year	Repository	License	Input	Output	Backbone	Num Classes	FPS		Accuracy		LongRange	memory	Remarks
									Kitti	NuScenes	Kitti	NuScenes			
1	DFR-FastMOT​	2023​	x	-									-	-	
2	BEVFusion​	2022​	o	Apache-2.0​	"RGB(256x704)
+
LiDAR point cloud"	"3D Detection
+
Task Specific Heads"	"Swin-T(RGB)
+
VoxelNet(LiDAR)"	10	-	8.4(RTX3090)	-	75	30m以上の評価あり	-	OK
3	MVX-Net​	2019​	o	Apache-2.0​	"RGB
+
LiDAR point cloud"	3D Detection	-	-	40	-	65.2	-	-	-	MMDetection3Dの一部​
4	BSH-Det3D​	2023​	o(No Sourcecode)	​					20.83	-	77	-	-	-	Code is coming soon.​
5	3D Dual-Fusion​	2022​	o	-	"Multi view camera RGB()
+
LiDAR point cloud"	3D Detection	VoxelNet(LiDAR)		-	-	79.3	70.6	30m以上の評価あり	-	
6	Fast-CLOCs​	2022​	-​	-​									-	-	​
7	UVTR​	2022​	o	Apache-2.0​					-	9.3(V100)			30m以上の評価あり	-	​
8	Point-GNN	2020	o	MIT											


## 3D Detection (Stereo) o 
index	Model	Year	Repository	License	Input	Output	Backbone	Inference/fps/flops	Ap	LongRange	memory	Remarks
1	DSGN++	2022	o	Apache-2.0	"Binomicular
Images(384x1248)"	"3D Detection
+
Depth Map"	PSMNet(or ResNet34)	"5.62
(a RTX2080Ti)"	67.37	50m	-	"Siamese Network
Joint Stereo-LiDAR copy-paste"
2	Chen et al.	2022	o	記載なし	-	-		-	-	-	-	-
3	ESGN	2022	x	---	Binomicular images + LiDAR			"16.13
(a RTX3090)"	38.42	-	-	
4	LIGA-Stereo	2021	o	Apache-2.0	Binomicular Images			"2.86
(V100)"	57.22	-	-	
5	YOLOStereo3D	2021	o	Apache-2.0	Binomicular images	"3D Detection
+
Disparity Estimation"		"20
(a RTX3090)"	41.25	-	-	
6	Stereo CenterNet	2021	x	---	Binomicular images			"25
(a RTX3090)"		-	-	"3D detection
realtime performance"
7	DSGN	2020	o	MIT	Biomicular images	"3D Detection
+
Disparity Estimation"		"1.49
(a RTX3090/V100)"	52.18	-	-	
8	RTS3D	2020	o	MIT	Binomicular images	3D Detection		"25.64
(a RTX3090)"	45.58		-	Siamese Network
9	OC Stereo	2020	x	---	Binomicular images			2.86	41.44	-	-	
10	Stereo R-CNN	2019	o	MIT	Binomicular images			"3.33
(a RTX3090)"	34.05	-	-	
