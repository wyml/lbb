---
layout: "../../layouts/postsLayout.astro"
title: "CATIA飞机建模教程【01】- 创建工程项目以及引入翼型参考"
pubDate: 2024-08-14 03:02:28
description: "CATIA飞机建模教程【01】- 创建工程项目以及引入翼型参考"
author: "Jiabin Lan"
tags: ["catia"]
---

## 00 写在前边
本教程的初衷，是为了方便城大或者其他院校的同学们，在参加CUADC或者其他相关系列的飞行器/机械类比赛时，能够有个系统的CATIA建模教程，不至于网上抓瞎。当然，网上也存在很多非常优秀的视频教程，例如：[【【北航】飞机总体设计 CATIA军机建模教程（已完结）】]( https://www.bilibili.com/video/BV1MP4y1p7gM/?share_source=copy_web) 等等优秀的视频教程。本教程主要从文字与配图的方式，逐步的进行设计，同时对于一些在设计过程中存在的问题提供一些个人的解决方法。

教程尽量争取做到面向小白，不足之处还望谅解。🥳

本教程的大体结构如下：
- 1.创建工程项目、引入翼型参考（包含翼型库以及翼型工具的使用等等）
- 2.机翼主体结构的建模、上反、前掠/后掠的画法
- 3.创成式外形设计的使用
- 4.机身主体的建模
- 5.结构的填充

希望和各位同学一起进步，学习😊

## 01 创建工程项目
在CATIA中，工程项目的管理是由Product（后统称 产品 ）文件统一创建的，使用根产品进行工程项目的管理是一个良好的行为规范。因此，在本课程中，你将完全遵循产品管理原则。

首先，我们在一个空白窗口中，点击“文件” -> “新建产品”，创建一个名为`huaxiangji`的产品，像下图这样。需要注意的是，在CATIA中，不建议使用中文作为产品/零件的编号，因此我们在课程中采用的均为汉字拼音。
CATIA的工程结构类似于Windows系统中的文件管理，是一个树状结构，根结点是一个总产品，也就是刚才我们新建的`huaxiangji`，而在产品总产品下。可以新建子产品、子零件。这时，这些子产品和子零件就归属于根产品。

那么产品与零件有什么区别？这个问题，是我们需要实际探究的。
产品，在机械领域当中，实际所属的是一个机械/机构，他们是由若干个机构/零件组成的。因此产品可以快速的管理下属的结构，无论是在CATIA中对产品进行属性修改，还是赋予物质，都可以直接对下属的产品/零件进行统一赋予。

同时，我们在子产品中，对零件进行装配，其结果并不会对父产品产生影响，其装配关系，也是保存在子产品中的。此时如果对子产品进行装配，那么其下的零件会根据子产品的装配关系进行约束，使得装配的难度大幅度减少。使用者仅需要从小到大逐一装配，最后就能得到总装产品。

而零件，是一个单一组成单元。在CATIA中，零件仅表示某一个不能活动的结构。他是CATIA中的最小单元。因此，在对零件进行设计时，我们务必遵循`一个零件一个结构`的要求。在一个零件内，不能够创建两个独立结构。否则装配时，会因两独立结构同属一个零件，而导致无法装配的情况。

## 02 导入翼型

翼型是飞行器的重要参数，导入这一步骤对飞机设计来说是至关重要的。一般而言，翼型的导入流程如下：
1. 使用翼型工具，寻找一个合适的翼型
2. 将翼型数据导入EXCEL或其他工具进行处理
3. 将处理后的翼型数据导入CATIA

### 翼型数据

为了更好的理解这三个步骤。首先我们需要了解翼型导出数据的本质。进入翼型工具或翼型网站，这里推荐使用翼型网站：[AirfoilTools](http://airfoiltools.com/)  或 windows翼型库 [Profili 2 - wing airfoils managing, printing and analysis software](https://www.profili2.com/eng/default.asp)

首先，进入AirfoilTools，点击Airfoil Search，搜索 *NACA2414* 或任意你喜欢的翼型。

![QQ_1724040363013.png](/storage/H25gNUFWqnKjOMTK3spLTHss46dr1xHyoEDosMz6.png)

点击 *NACA2414* 进入详情页，可以看到此翼型的基础数据，包括最大曲面位置、最大厚度位置的、不同雷诺数下的升阻比等等。

![QQ_1724034836028.png](/storage/srKtIvSHHsYvHEaxkfvnj0UoB3T4Z8FvZaSHUkU6.png)

点击 *Send to airfoil plotter* 进入翼型绘图仪，我们可以找到如下的选项界面，此界面主要用于绘制你所需要的翼型。

![QQ_1724035927746.png](/storage/gKvyO9a4TlDvltKwNTay7CLGhlXkriQml4aVTYDe.png)

将界面翻译，便于使用，主要用到的参数包括 `弦长、厚度、上反角` 这几个参数，后续我们会根据实际需要，修改这几个参数便于设计。

![QQ_1724040142681.png](/storage/AamvQ8ZB03I9b5zw55R5ycOwmbb9YD5tXUJQdf3D.png)

现在，我们下载一个翼型数据用于学习。点击 *CSV file of coordinates* 我们可以得到一个 CSV 翼型文件，使用 EXCEL 打开，就可以看到所下载翼型的点位坐标。

![QQ_1724040538276.png](/storage/tNMZKm0r71WVMBUH7Lw3odM7JKss6Do1E65EI5z4.png)

仔细观察数据不难发现，该文件主要分为三个部分：翼型参数、翼型点位、中线坐标。

![QQ_1724041005811.png](/storage/z2VVV4IgsbDWoJd67ta0R9sxRV5XivpzUzY48TvY.png)
**翼型参数**

![QQ_1724041062250.png](/storage/w6WjnIlfSNNclxeM6CpbItXBCvC7qlbvWG04ZNNZ.png)
**翼型点位**

实际上，翼型就是在平面上绘制的特定的点的坐标，通过样条曲线方式，将点在平面上链接，即可得到翼型。
在案例中，我们下载的翼型为 *NACA2414* 弦长 100mm，100% 大小。

### 导入翼型

导入翼型可以使用多种方式，这里介绍两种：

1. 对翼型数据进行处理后，采用CATAI的三维曲线指令导入
2. 采用辅助软件导入

#### 1.对翼型数据进行处理后，采用CATAI的三维曲线指令导入

打开上一部分下载的 NACA2414-il.csv 文件，保留Airfoil surface 内容，其余内容全部删除。最后结果如图：

![image.png](/storage/SkTrDdTSJojxbnpNhiqYGXNiZIWl2J1CjE2eI7da.png)

由于空间坐标为三维坐标系，目前仅有二维点位坐标，因此，我们需要对第三维进行补充。假设我们需要将翼型导入到yz平面中，则我们需要补充x轴信息。

在数据表中，我们规定，A 列为 X 轴，B 列为 Y 轴，C 列为 Z 轴。因此对于上述的翼型导入，就需要在 X 轴上补0，也就是令 A 列为的值均为0。

![image.png](/storage/zZg3asgRcerXXyINkiVrHOig020pi9NZftVsitWy.png)

完成后另存为 txt 文件，同时需要注意，保存编码设计设置为 ANSI 类型。

![image.png](/storage/J6wzJGomxSTPLasyFEdO3ZZtCB9HuMXJkvOJFdds.png)

打开 CATIA 新建零件，在开始菜单中选择 `开始->形状->Digitized Shape Editor`，在插入中选择`Import` ![image.png](/storage/sJqT9aV2bp1VlRMSSmRDFTWCgZuEqnPdut5eH749.png) 

弹出的对话框中进行如下配置：

![image.png](/storage/ZxsivW70XdXmZYsmeK9BW2vXhLOmgWkt7lBkFCuT.png)

点击`应用`可以预览导入情况，随后点击`确定`完成导入。导入完成的翼型数据仅有点位，还需要通过`3D Curve`指令将点位转化为样条曲线。

![image.png](/storage/gryxjOkYBPzNaLEYpJgJ3zDGtXm5MXcRLrl5dlwn.png)

在`插入`中找到`Curve Creation->3D Curve`，先选中导入的翼型数据，随后点击`3D Curve`指令并直接确定，完成翼型截面参考的创建。

![image.png](/storage/bWt4QXGV0w6jzcHBBNtF6eohF25a4yTpjpr6aLK7.png)

完成后，隐藏导入的翼型数据，仅留下3D曲线即可。

![image.png](/storage/Eqa7btFNZ3aNZ4AlL4zMaqYqnRm621jNgmotIjOf.png)


#### 2. 采用辅助软件导入

采用辅助软件，主要是利用CATIA的二次开发功能，前人开发了翼型导入软件，可以很快的完成翼型的导入，并且可以修改导入的位置等参数。

软件下载：https://gxcvucnc.feishu.cn/file/KvsNboHKNoHPjLxvQfHcsrw9n1f?from=from_copylink


下载后解压，得到软件本体，运行`翼型工具.exe`，添加一个翼型。

添加点击`生成CATIA草图`选项卡，在下方填入需要的参数。
![image.png](/storage/DNhyNX2azK1jYgkagnXxCiYMoTEDT4k7aSPBIIE6.png)

参数设定完成后，回到CATIA软件，新建一个零件并在新窗口中打开（这一步非常重要，必须！）将翼型工具激活，底下为CATIA软件，点击`添加`按钮，将翼型添加进零件草图。完成零件导入。