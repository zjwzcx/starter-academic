---
title: Simultaneous Localization and Mapping of Robots Based on Feature Tracking

summary: Ubuntu 16.04, ROS（Gazebo, Rviz), Python

tags:
- Robotics	# correspond with "projects.md"
# - Planning, Localization and Mapping

date: "2016-04-27T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart

links:
# - icon: twitter
#  icon_pack: fab
#  name: Follow
#  url: https://twitter.com/georgecushen
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: example

---

**指导老师:**

[王越](https://ywang-zju.github.io/)，副教授，博士生导师，浙江大学智能系统与控制研究所

**实验目的:**

给定移动机器人结构模型与环境地图，设计具有导航、定位等功能的移动机器人，最终实现即时定位与地图构建（SLAM）。

**实验动机:**

无论移动机器人位姿的观测模型使用的是地图ICP还是特征匹配方法，**都对现有的理想化地图有很大的依赖性**，从应用的角度考量，这会使该定位方法的使用场景受到很大限制。

EKF-SLAM方法综合了EKF航位推断方法的优越性和SLAM思想对已知条件更少的依赖性，提供了解决上述问题的一种思路。

**实验环境:**

Ubuntu16.04​, ROS (Kinetic)，使用编程语言为Python。

（由于COVID-19的影响，我的实验均为基于仿真环境的线上实验）

**主要工作:**

1）导航。设计了移动机器人平稳运动的运动控制律，生成基于A*算法的最优的全局路径规划与基于DWA算法的局部路径规划，并实现导航。

2）定位（位姿估计）。依次试验了以下移动机器人位姿估计方法，并进行耗时和精度对比。

- 基于里程计的运动模型

- 基于激光里程计和ICP算法的观测模型

- 基于EKF框架，对里程计运动模型和观测模型结果进行最优估计
- 基于EKF框架，对里程计运动模型和特征匹配模型结果进行最优估计

3）基于特征的EKF-SLAM。在成功实现各种位姿估计模型的基础上，将移动机器人定位和地图特征都建模为状态，因此，该问题本质上被抽象为一个离散时间状态空间系统的估计问题。在本问题中，状态可以被理解为是一个动态列向量。初始状态维度为(3, 1)，仅包含移动机器人初始位姿。记某时刻扫描过的特征点数目为n，那么该时刻状态维度为(2n+3, 1)。

- **地图构建**：根据机器人实时位姿信息和点云数据，使用Bresenham算法构建激光路径。用贝叶斯公式和几率对数对栅格地图占用情况的后验概率进行恒等变形并得到其递推式。得到栅格集合的概率分布之后，设定经验阈值，将每一个栅格单元区分为占用/未占用/未知三类，从而完成地图构建。
- **状态估计**：将地标位置纳入系统状态。对地图特征点作聚类获得地标位置，用KNN对获得的实时地标与系统状态中的已有地标作数据关联。根据里程计运动模型的**状态预测**和激光里程观测模型**状态更新**的结果，用EKF进行系统实时状态的估计。



以下为部分实验结果：

{{< figure src="rob2.png" caption="图1. 红、蓝、绿色箭头依次表示后三种估计方法的位置估计结果" >}}



{{< figure src="rob5.png" caption="图2. 基于EKF框架的三种位姿估计方法的累计误差比较" >}}



{{< figure src="rob3.png" caption="图3. 主要模型方法的耗时记录" >}}



{{< figure src="rob4.png" caption="图4. 真值地图（左）和由激光数据构建的地图（右）" >}}



EKF-SLAM部分过程（视频经过倍速处理）如下：

{{< video src="slam.mp4" width="320" height="240" controls=controls" >}}