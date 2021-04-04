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

**指导老师:**

[赵春晖](https://person.zju.edu.cn/chhzhao)，教授，博士生导师，浙江大学工业控制技术国家重点实验室

- **Data processing:** Perform data     analysis (correlation analysis, production batch division, etc.) on the     raw data of sensors in the industrial filed, filter out abnormal data and reconstruct     the data through Median Filtering, Double-blind Denoising Autoencoder and     other methods.
- **Flow Soft-sensoring:** Use     process variables such as pressure to perform multiple regression on flow,     compare and improve the performance of Random Forest, XGBoost, LSTM and     other methods used in industrial fields.
- **Online Fault Monitoring:** Based on the offline data including the fault, the fault monitoring     sensitivity test is carried out on the dynamic PCA, dynamic SFA, Autoencoder, etc. After selecting the best method     PCA, the comprehensive statistical index φ of T2 and SPE statistics is introduced for     online fault monitoring.