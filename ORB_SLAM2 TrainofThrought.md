# SLAM

## Tracking Thread

** 初始化 **
- Input: ** Frame **
- StereoInitialization()/MonoInitialization()
    - 需要特征点数量大于500
    - 如果满足条件，则将该帧的位姿设为原点，即单位矩阵
    - 该帧设为关键帧，并将其插入到地图的关键帧列表中
    - 为每个有效的特征点创建一个地图点，并与关键帧进行关联，将特征点信息也添加到关联中
    - 计算地图点的描述子、法线和深度，把地图点添加到地图中
    - 更新系统状态为“OK”，表示初始化完成
一般下一步为位姿跟踪或者重定位（在追踪失败的情况下），除非我们在可视化界面中选择“only tracking”
-  TrackReferenceKeyFrame()/TrackWithMotionModel()/Relocalization()
    -  利用运动学模型或者重定位初始化相机位姿
    -  局部优化地图点
