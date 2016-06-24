# OpenRTB_API_Specification中文版(V2.3.1)

#名词解释
**IAB:** Interactive Advertising Bureau 交互式广告局。

# 前言
## 简介

RTP工程， 前身为OpenRTB组织， 在2010年11月份组建。致力于为数字媒体自动化交易开发一套全新的开放标准，以应对更大范围的平台，设备以及广告解决方案。本文档就是RTB工程努力的结晶，你可以在[www.iab.net](www.iab.net)找到最新的官方文档。

## 关于IAB的广告网络和交易协会

IAB 广告网络和交易协会主要由广告网络和广告交易平台成员公司的高层领导组成。该协会致力于促进当今世界日益复杂的广告市场中数字生态系统的利益。协会目标是促进完成在广告商，发布者，中间商，代理协会之间专业性和责任心的最高标准， 开发能够保证收入增长的程序以及创建保护消费者和行业的最佳实践。

RTB工程是IAB广告科技理事会下的一个工作小组。

## IAB 联系方式
Melissa Gallo
产品总监 – 数据和程序自动化, IAB 科学实验室
[melissa@iab.net](melissa@iab.net)

## 许可证

OpenRTB 规范是在[Creative Commons Attribution 3.0 License](https://creativecommons.org/licenses/by/3.0/)许可之下，基于[http://openrtb.info](http://openrtb.info)的工作。 在该许可证之外的权限你可以在[http://openrtb.info](http://openrtb.info)找到。如果要查看该许可证的副本， 可以访问[https://creativecommons.org/licenses/by/3.0/](https://creativecommons.org/licenses/by/3.0/)或者写信给Creative Commons, 171 Second Street, Suite 300, San Francisco, CA 94105, USA.


# 1. 介绍
## 1.1 Mission / Overview
## 1.2 History of OpenRTB
## 1.3 Version History
## 1.4 Resources
## 1.5 Terminology

# 2. OpenRTB 基础知识
## 2.1 Transport
## 2.2 Security
## 2.3 Data Format
## 2.4 OpenRTB Version HTTP Header
## 2.5 Privacy by Design
## 2.6 Relationship to IAB Quality Assurance Guidelines
## 2.7 Customization and Extensions

# 3. Bid Request 规范
## 3.1 Object Model
##　3.2 Object Specifications
### 3.2.1 BidRequest
### 3.2.2 Imp
### 3.2.3 Banner
### 3.2.4 Video
### 3.2.5 Native
### 3.2.6 Site
### 3.2.7 App
### 3.2.8 Publisher
### 3.2.9 Content
### 3.2.10 Producer
### 3.2.11 Device
### 3.2.12 Geo
### 3.2.13 User
### 3.2.14 Data
### 3.2.15 Segment
### 3.2.16 Regs
### 3.2.17 Pmp
### 3.2.18 Deal

# 4. Bid Response 规范
## 4.1 Object Model
## 4.2 Object Specifications
### 4.2.1 BidResponse
### 4.2.2 SeatBid
### 4.2.3 Bid
## 4.3 Ad Serving Options
### 4.3.1 Markup Served on the Win Notice
### 4.3.2 Markup Served in the Bid
### 4.3.3 Comparison of Ad Serving Approaches
## 4.4 Substitituion Macros

# 5. 规范清单列表
## 5.1 Content Categories
## 5.2 Banner Ad Types
## 5.3 Creative Attributes
## 5.4 Ad Position
## 5.5 Expandable Direction
## 5.6 API Frameworks
## 5.7 Video Linearity
## 5.8 Video Bid Response Protocols
## 5.9 Video Playback Methods
## 5.10 Video Start Delay
## 5.11 Video Quality
## 5.12 VAST Companion Types
## 5.13 Content Delivery Methods
## 5.14 Content Context
## 5.15 QAG Media Rating
## 5.16 Location Type
## 5.17 Device Type
## 5.18 Connection Type
## 5.19 No-Bid Reason Codes

# 6. Bid Request/Response 样例
## 6.1 Github Repository
## 6.2 Validator
## 6.3 Bid Requests
### 6.3.1 Sample Banner
### 6.3.2 Expandable Creative
### 6.3.3 Mobile
### 6.3.4 Video
### 6.3.5 PMP with Direct Deal
### 6.3.6 Native Ad

## 6.4 Bid Responses
### 6.4.1 Ad Served on Win Notice
### 6.4.2 VAST XML Document Returned Inline
### 6.4.3 Direct Deal Ad Served on Win Notice
### 6.4.4 Native Markup Returned Inline

# 7. 实现注意事项
## 7.1 COPPA Regulation Flag
## 7.2 PMP & Direct Deals
## 7.3 No-Bid Signaling

# 附录A. 附加信息
# 附录B. 规范版本更新日志
