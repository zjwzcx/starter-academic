---
title: High-precision DH Calibration and Motion Control of Six-axis Mechanical Arm

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

**Adviser:** [Chunlin Zhou](https://person.zju.edu.cn/c_zhou), Associate Professor of Institute of Intelligent Systems and Control, Zhejiang University                                                

- **Geometric Parameter Estimation:** A binocular camera is     used to record the dynamic position of the marker on the end-effector, and     the parameters are estimated by the plane arc constraint and the least     square method.
- **DH Table Correction:** The correction parameter β is used to correct the misalignment DH     table of parallel continuous joints, and the DH parameter is used for Inverse     Kinematics calculation.
- **Motion Control:** Interpolate     the joint angle sequence to achieve more stable and accurate Forward Kinematics     control