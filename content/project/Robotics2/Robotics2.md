---
title: High-precision DH Calibration and Motion Control of Six-axis Mechanical Arm

summary: Ubuntu 18.04, ROS, MATLAB, Python

tags:
- Robotics	# correspond with "projects.md"
# - Planning, Localization and Mapping

date: "2020-11-00T00:00:00Z"

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

[周春琳](https://person.zju.edu.cn/c_zhou)，副教授，硕士生导师，浙江大学智能系统与控制研究所

**实验动机:**

对于含平行连续关节的机械臂，由制造工艺、装配精度等因素引起的尺寸、角度的微小误差将会在传统的四参数DH表中放大，这对正运动学控制精度会产生比较大的影响。

**主要贡献:**

1）为了提取双目相机扫描到的目标点位置信息，设计了基于静态和动态两种扫描方式的机械臂几何特征提取算法

2）复现文献中的误差修正方法，将其成功实践于实验所用的含平行连续关节机械臂上

3）基于目标路径特征以及修正DH表参数，进行逆运动学解算、路径插值以及正运动学控制

**实现步骤:**

1. **几何参数估计**: 用双目相机记录标记物动态位置，由平面圆弧约束和最小二乘法估计几何参数，获得该含平行连续关节机械臂的失准DH表。

2. **DH表修正**: 采用修正参数β校正含平行连续关节机械臂的失准DH表，将DH参数用于逆运动学解算。

3. **运动控制**: 对逆运动学解算出的关节角序列进行插值，从而实现更平稳和精准的正运动学控制。



为了直观反映运动控制的准确度，在防割板上依次选取直线路径和圆弧线路径，令机械臂遵循其轨迹运动。

直线路径运动结果如下：

{{< video src="2.mp4" width="320" height="240" controls=controls" >}}

以下视频中的圆弧线路径为人工用黑笔绘制的正圆弧（痕迹较淡，需仔细辨认），运动结果如下：

{{< video src="3.mp4" width="320" height="240" controls=controls" >}}



实验间隙，尝试用图形化编程对NAO机器人编舞：

{{< video src="1.mp4" width="320" height="240" controls=controls" >}}