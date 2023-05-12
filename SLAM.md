# SLAM

## 定位

### 图像前端

图片中的点（u， v）与对应的三维点（x，y，z）之间的转换关系：


$$
s
\left [\begin{matrix}
u \\
v \\
1 \\
\end{matrix} \right]
=
\left[ \begin{matrix}
f_x & 0 & c_x \\
0 & f_x & c_y \\
0 & 0 & 1\\
\end{matrix}\right]
\left [\begin{matrix}
x \\
y \\
z \\
\end{matrix} \right]
$$
左侧的s为**尺度因子**，表示从相机光心出去的射线都会落在成像平面的同一个点上。

根据上述公式，可以得到计算三维点的公式：
$$
\left \{
\begin{aligned}
x = \frac{(u - c_x) z}{f_x} \\
y = \frac{(v - x_y) z}{f_y} \\
z = \frac{dep(u, v)}{s} \\
\end{aligned}
\right .
$$
知道了三维点的坐标后，就可以根据两帧图像间的差别计算相机的位移-> 位姿估计，经典算法就是**ICP（Iterative Closest Point，迭代最近点）** -> 特征点的提取和匹配

得到一组匹配点后，可以计算两个图像间的转换关系，即**PnP问题**，其模型为：
$$
\left[\begin{matrix}
u \\
v \\
\end{matrix}\right]
=C(Rp + t)
$$
可以使用openCV中的SolvePnPRANSAC函数或者PCL的ICP算法来求解。openCV提供的算法是**RANSAC（Random Sample Consensus，随机采样一致性）架构**，可以剔除错误匹配。所以代码实际运行时，可以很好地找到匹配点。

在求解SLAM问题前，我们要看到，我们拥有的数据是什么？在上面的模型里，我们知道的是运动信息u以及观测z。用示意图表示出来是这样的：![SLAM模型示意图](https://images0.cnblogs.com/i/606958/201404/281107477838540.jpg "SLAM模型示意图")

所求问题就是根据u和z，确定所有的$X_p$和$X_L$















