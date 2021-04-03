---
title: Simultaneous Localization and Mapping of Robots Based on Feature Tracking

summary: Ubuntu 18.04, ROS

tags:
- Robotics1	# correspond with "projects.md"
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

**指导老师:** [王越](https://ywang-zju.github.io/)，副教授，博士生导师，浙江大学智能系统与控制研究所

实验目的：给定移动机器人结构模型与环境地图，设计具有导航、定位等功能的移动机器人，最终实现即时定位与地图构建（SLAM）。

实验环境：Ubuntu16.04​, ROS (Kinetic)，使用编程语言为Python。

（由于COVID-19的影响，我的实验均为基于仿真环境的线上实验）

我的主要工作包括：

1）导航。设计了移动机器人平稳运动的运动控制律，生成基于A*算法的最优的全局路径规划与基于DWA算法的局部路径规划，并实现导航。

2）定位（位姿估计）。依次试验了以下移动机器人位姿估计方法，并进行耗时和精度对比。

- 基于里程计的运动模型

- 基于激光里程计和ICP算法的观测模型

- 基于EKF框架，对里程计运动模型和观测模型结果进行最优估计
- 基于EKF框架，对里程计运动模型和特征匹配模型结果进行最优估计

3）基于特征的EKF-SLAM。



以下为部分实验结果：

{{< figure src="rob1.png" caption="图1. 后三种位姿估计方法的耗时记录" >}}



{{< figure src="rob2.png" caption="图2. 红、蓝、绿色箭头依次表示后三种估计方法的位置估计结果" >}}



最终得到SLAM结果如下：

{{< video src="slam.mp4" width="320" height="240" controls=controls" >}}