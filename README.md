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

# 新手入门

本规范包含了实时竞价接口的详细解释。以下相关解释中多处涉及“对象”这个概念， 所以这里提前说明以下：并不是所有的对象都是必须的，每个对象可能包含多个可选的属性参数。为了帮助第一次接触本文档的读者，我们已经在文档中标注了不同场景下（比如banner, video等等）要完成一个最小可行的实时竞价接口，哪些参数是不可缺少的以及哪些属性是可忽略的。

最小可行接口应该包括标识有**required**以及**recommended**的参数，但是这些参数的作用范围与其特定的使用场景相关。在这些场景的参数描述表中， [Description] 列可能会进一步的标识及注解参数的**required**或者**recommended**状态。为了尽可能填充对象， 可选参数也是可以被填充的，这都取决于该行为的参与者（对象填充者）。

下表展示了不同修饰符的作用：
* 带有**required**为必须参数，带有**recommended**的选项是推荐参数，其余的（带有**default**修饰符或者什么都不带）则是可选参数。
* 按照习惯，通常会按照 **required-->recommended->default->none** 的顺序防止参数。

| Attribute | Type | Description |
| --- |---| ---|
|id|string;**required**|...|
|site|object;**recommended**|...|
|test|integer;**default** 0|...|
|tmax|integer|...|

> 注意： 由于**recommended**属性不是必须的， 所以并不是从每个数据源都可以获取到的。 所以建议所有的OpenRTB事务参与者完成下页中的集成清单来标识供应方在竞价请求中支持，哪些属性是需求方需要用来做广告决策的。

# 集成清单列表
# 1. 介绍
## 1.1 目标/概览
OpenRtb工程的任务是为广告买家和广告位库存买家之间的通信提供开放的工业标准，以刺激实时竞价市场的增长。标准涉及到很多方面，包括但不限于实时竞价协议，信息分类，离线配置同步以及其他很多。

本文档为从早期”block list"项目和"OpenRTB Mobile"项目发展而来的实时竞价接口规范标准。这些标准旨在简化广告媒体库存的提供商（例如，广告交易， 代表发布商利益的广告网络， 卖方平台） 与其有竞争力的买家（例如，竞价者， 需求方平台以及代表广告商利益的广告网络）之间的关系。

OpenRTB总的目标是为买家和卖家之间的沟通创造一种通用语言，这种倾向不是精确的规定每个交易的操作。 作为一个工程， 我们的目标是让参与的各方可以更容易的集成， 从而促进生态系统中交易的各方都能够进行更深层次的创新。

## 1.2 OpenRTB的历史
OpenRTB于2010年的11月份在三个需求方平台（DataXu, MediaMath和Turn）以及三个卖方平台（Admeld, PubMatic以及The Rubicon Project)上作为试点项目启动的。 第一个目标是使交易block lists各方的沟通标准化。OpenRTB 1.0 block list规范在2010年的12月发布。

在得到了业界普遍的正面响应之后， Nexage 介入 OpenRTB工程，并建议在实时竞价请求和响应协议上为OpenRTB创建API规范，尤其是为支持手机移动广告。 移动小组委员会在买方公司（DataXu, Fiksu以及[X+1]和卖方公司(Nexage, Pubmatic, Smaato以及Jumptap)之间形成了。这个项目促成了OpenRTB Mobile 1.0标准， 该标准在2011年2月发布。

随着移动规范的发布， 在与DataXu和ContextWeb协作的视频广告交易（BrightRoll以及Adap.tv)中，一个视频小组委员会也形成了，其目标在于合作支持将普通展示型广告，视频广告以及移动广告规范在一个文档中。这个努力最终促成了一个统一的标准-OpenRTB2.0,在2011年6月发布。

由于业界的广泛采纳， 随着OpenRTB在2012年1月2.1版本的发布，它被采纳为美国互动广告局（Interactive Advertising Bureau）的一项标准。

## 1.3 版本历史
**OpenRTB 实时竞价API**
*　2.3 支持原生广告以及多个微小改动
*　2.2 为私有市场直接交易，视频，移动广告以及regulatory signals做出的一些新的改动
*　2.1 按照QAG规范进行一些修正，一些小的改动以及错误修正。
*　2.0 将展示广告，移动广告以及视频广告标准归一到一个统一的标准
*　1.0 OpenRTB 移动版的最初发布版

**OpenRTB 展示 Block List分支**
*　1.2 发布商API
*　1.1 为包含creative attributes的实时交易进行小改动
*　1.0 OpenRTB block list规范的最初发布。

## 1.4 资源
OpenRTB Google Groups: [http://openrtb.info](http://openrtb.info)
OpenRTB Github 地址 [http://github.com/openrtb/OpenRTB](http://github.com/openrtb/OpenRTB)
开发者社区邮件列表 [http://groups.google.com/group/openrtb-dev](http://groups.google.com/group/openrtb-dev)
用户社区邮件列表 [http://groups.google.com/group/openrtb-user](http://groups.google.com/group/openrtb-user)

## 1.5 术语
| 术语 | 解释 |
| --- |---|
| RTB |实时竞价 Real-Time Bidding|
| Exchange | 为一次展现管理不同竞价者之间的竞拍行为的服务 |
| Bidder | 在实时竞拍中为获取一次展示参与竞价的实体 |
| Seat |  |
| Publisher ||
| Site ||
| Deal ID | |

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
