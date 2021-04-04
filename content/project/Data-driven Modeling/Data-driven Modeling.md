---
title: Soft-sensoring on the Flow and Online Fault Monitoring for Slurry Pump

summary: Python (numpy, pandas, Pytorch, etc.)

tags:
- Data-driven Modeling	# correspond with "projects.md"

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

**指导老师**:

[赵春晖](https://person.zju.edu.cn/chhzhao)，教授，博士生导师，浙江大学工业控制技术国家重点实验室



**实验目的**:

- **流量软测量**：使用电流、频率等变量对两台泵的输出流量进行软测量；

- **在线故障监测**：故障通过相关变量的变化趋势预判泵的故障情况。

  

**实验动机**:

- 流量软测量：解决了 1)流量计损坏时无反馈变量或失准 2)目标变量不容易通过工业传感器直接测量 情况下的变量测量问题

- 在线故障监测：在渣浆泵等设备因故障而出现停机等异常情况之前，通过异常数据的监测对故障进行预警，减少故障带来的损失

  

**主要步骤**:

- **数据处理：**对工业现场传感器原始数据进行数据分析(相关性分析、生产批次划分等)，通过中值滤波、双盲降噪自编码器(DBDAE)等方法滤去异常数据并完成数据重构。
- **流量软测量：**运用压力、电流等过程变量对流量进行多元回归，横向比较并改进Random Forest、XGBoost、LSTM等方法用于工业现场的表现。
- **在线故障监测：**基于含故障发生时段的离线数据，对动态PCA、动态SFA、Isolation Forest等方法进行报障灵敏度测试。选取最佳方法PCA后，引入$T^2$和$SPE$统计量的综合统计量指标$\Phi$进行在线故障监测。



注：实验所使用的原始数据均来自于工业现场，因保密性等原因，以下不标注绝对数值



**训练数据获取（正常运行数据段）**:

注意到，在渣浆泵正常运行数据段内，**压力**与**流量**会出现数次值为0的空白数据。考虑到极短的采样间隔与压力、流量的连续变化特性，可以认为这些数据为异常数据并对它们进行清洗。

针对过程变量会出现上述**脉冲噪声**的特点，对正常运行数据段作**中值滤波**进行去噪。经试验，取中值滤波邻域窗口长度为7时，正常运行数据段无脉冲噪声。之后，再对正常运行数据段作归一化处理。

**测试数据获取（含故障数据段）**:

将测试数据输入模型前，对测试数据作如上归一化处理。考虑到测试数据含较多异常数据，基于训练数据与测试数据中正常数据同分布的假设，式中的$\mu、\sigma$采用训练数据的结果。



**软测量**:

问题理解：

- 从数据驱动建模的角度，软测量本质上是多元回归分析，可以用PCR、PLSR、GPR、SVR等方法；

- 从时序相关性的角度，动态软测量模型包括DPLS、QSFR、LSTM、M-ARMAX等方法；

- 从状态估计的角度，软测量可以视为状态观测和估计问题，可以用Kalman Filter、Luenberger等方法；



**在线故障监测**:

基于实验原始数据的特性，发现该问题本质上是单建模时段非平稳时间序列的异常检测。由于该问题不涉及间歇过程，也不具备多时段特性，所以关键在于找到监测控制限/离群点集中的时段。

