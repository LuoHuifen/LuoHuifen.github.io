layout: post
tags: project python
date: 2016-9-05 22:10
title: 阿里流行音乐预测大赛——数据分析
published: true
excerpt: 离上一篇博客写了已经过去了大半年，决定还是用博客记录下自己的项目经历。这次参加天池大赛感触很深，

一是团队协作很重要，二是科研与实际应用还是有很大不同的。我在本次项目中主要承担数据分析的职责，做了两件事

：Time Series Decomposition, word embedding。
---
### 问题介绍 ###
这是阿里天池的一个比赛，比赛给出了虾米音乐上50个艺人歌曲的基本信息如歌曲发行时间、歌曲的初始播放次数、歌

曲语言等，以及与这些歌曲相关的过去6个月的用户播放记录，如用户播放时间、用户行为类型（播放、下载、收藏），

要求根据这些数据，预测这50个艺人在接下来2个月每天的播放量。

为了解决这个问题，我们同时从数据和模型两个角度入手。一个队友进行模型调研、一个队友进行代码实现，我则进行

**数据分析**。

### 数据分析 ###
反推数据采样方法
我首先考虑的是问题是：虾米音乐上歌曲和用户记录数量巨大，而比赛给的只有50个艺人的歌曲信息以及大约35万用户

的播放记录，这些数据是如何从所有数据中提取出来的？官方说明是先随机抽取艺人以及相应的歌曲，然后将这些歌曲

相关的用户行为记录历史提起出来。问题在于，**有了歌曲清单之后，如何提取出相应的用户行为记录？是首先获得所

有与歌曲相关的用户记录，然后随机抽样？还是先随机抽样出一部分用户，然
后提取出他们对于所选歌曲的用户记录？**

如果第一个猜想成立的话，也就是比赛的用户记录数据是从所有与歌曲相关的用户记录中随机抽样而来的。那么所有用

户记录中的用户应该是随机的，考虑到虾米音乐庞大的数据量，我们几乎不可能随机抽取到同一个用户的多个用户记录

。但比较后发现，我们有大量的同一个用户对同一首歌曲在不同时间点的记录。最后，我们认为比赛数据的获得过程是

这样的：

1.随机抽取50名艺人，然后得到这些艺人的所有歌曲（10278首）；
2.随机抽取35万用户，然后得到这些用户在目标时间段的与提取的歌曲相关的用户操作；

这次分析让我们将流行音乐预测比赛的重心放在了三个基本构成元素上：**歌手**、**歌曲**、**用户**。

### 歌手日播放量时间序列分解 ###

为了快速构建baseline开始模型迭代，经过队内讨论，我们首先考虑了最简单的情况，也就是直接对歌手每天的播放量

进行建模，而不对歌曲、用户进行建模。为此，我首先对每个歌手每日的播放量进行时间序列分解，将一个时间序列分

解为 `Trend  + Seasonal + residual` 三部分，**trend** 表示歌手播放量的趋势，**seasonal** 表示歌手播放量的

周期变化，**residual**是总播放量减去trend 和 seasonal 之后剩下的残差。下面举几个例子：

<div><img src="/images/ali-music-competition/Fig1.png" width="100%"></div>

上图是代号2e14d32266ee6b4678595f8f50c369ac歌手的用户每日操作记录，红色表示播放量，蓝色表示下载量，绿色表

示收藏量。我们以7天为周期对播放量进行时间序列分解，得到下图：

<div><img src="/images/ali-music-competition/Fig2.png" width="100%"></div>

可以看到，该歌手除了在三个时间点出现了播放量剧增以外，其他时间点都较为平稳，因此，后续如果没有更多事件发

生，我们估计该歌手的播放量不会有剧烈变化。

又如下图所示，该歌手发生了两次播放量激增的情况，但对于新用户的吸引力明显不够，播放量在激增后迅速下降并且

趋于平稳。

<div><img src="/images/ali-music-competition/Fig3.png" width="100%"></div>

<div><img src="/images/ali-music-competition/Fig4.png" width="100%"></div>

### 歌手辅助信息收集 ###
经过上面的分析，我们意识到，对于歌手播放量而言，如果没有突发事件的发生则一般不会发生大的变化，因此一个最

简单的预测模型是将歌手过去6个月播放量的平均值作为后面2个月的播放量预测，事实上，这样一个简单的方法取得了

非常不错的效果。另一方面，即便播放量因为某些事件发生了大的变化，这个歌手对新用户的吸引力也决定了播放量增

长持续的时间。比赛并没有提供与歌手相关的其他信息，因此我们决定在网上寻找与歌手相关的辅助数据。

寻找的方式主要利用以下信息：歌曲发布时间、歌曲语言、歌手性别、平均播放量、播放量激增时间点。一般来说，平

均播放量大的歌手较为有名，播放量小的歌手则较为小众，而比赛评分明显更注重播放量大的歌手的预测，因此我首先

将精力集中在这些歌手身上。另外，因为更加有名，关于他们的新闻也更容易发现。

因为比赛对数据进行了脱敏处理，我首先需要恢复id所代表的具体含义。根据数据的特性基本可以猜出它的属性是什么

：


<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-

width:1px;overflow:hidden;word-break:normal;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-

style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg .tg-slkj{font-family:"Lucida Console", Monaco, monospace !important;;text-align:center}
.tg .tg-kkwu{font-weight:bold;font-family:"Lucida Console", Monaco, monospace !important;;text-

align:center}
.tg .tg-gq9a{font-family:"Lucida Sans Unicode", "Lucida Grande", sans-serif !important;;text-

align:center}
.tg .tg-k9ij{font-family:"Lucida Sans Unicode", "Lucida Grande", sans-serif !important;;text-

align:center;vertical-align:top}
.tg .tg-m2jw{font-family:"Lucida Console", Monaco, monospace !important;;text-align:center;vertical-

align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-kkwu">语种ID</th>
    <th class="tg-gq9a">0</th>
    <th class="tg-gq9a">1</th>
    <th class="tg-k9ij">2</th>
    <th class="tg-k9ij">3</th>
    <th class="tg-k9ij">4</th>
    <th class="tg-k9ij">100</th>
    <th class="tg-k9ij">11</th>
    <th class="tg-k9ij">14</th>
    <th class="tg-k9ij">12</th>
  </tr>
  <tr>
    <td class="tg-kkwu">真实值</td>
    <td class="tg-slkj"></td>
    <td class="tg-slkj">中文</td>
    <td class="tg-m2jw"></td>
    <td class="tg-m2jw"></td>
    <td class="tg-m2jw">英文</td>
    <td class="tg-m2jw"></td>
    <td class="tg-m2jw">粤语</td>
    <td class="tg-m2jw"></td>
    <td class="tg-m2jw"></td>
  </tr>
</table>

<p></p>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-

width:1px;overflow:hidden;word-break:normal;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-

style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg .tg-slkj{font-family:"Lucida Console", Monaco, monospace !important;;text-align:center}
.tg .tg-kkwu{font-weight:bold;font-family:"Lucida Console", Monaco, monospace !important;;text-

align:center}
.tg .tg-gq9a{font-family:"Lucida Sans Unicode", "Lucida Grande", sans-serif !important;;text-

align:center}
.tg .tg-k9ij{font-family:"Lucida Sans Unicode", "Lucida Grande", sans-serif !important;;text-

align:center;vertical-align:top}
.tg .tg-px6o{font-family:"Lucida Console", Monaco, monospace !important;;text-align:center}
.tg .tg-pztl{font-family:"Lucida Console", Monaco, monospace !important;;text-align:center;vertical-

align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-kkwu">性别ID</th>
    <th class="tg-gq9a">1</th>
    <th class="tg-gq9a">2</th>
    <th class="tg-k9ij">3</th>
  </tr>
  <tr>
    <td class="tg-kkwu">真实值</td>
    <td class="tg-px6o">男</td>
    <td class="tg-slkj">女</td>
    <td class="tg-pztl">组合</td>
  </tr>
</table>

<p></p>

（接下来仅对播放量大的歌手做此以下猜测，在这里将播放量大定义为日播放量超过1000首，经过调查，这样的歌手并

不多）

将50位歌手过去6个月的所有歌曲的日播放量总和绘制成图表。首先是，播放量大的一组数据：分析出属性是组合&中文

，凭这两个条件猜想了一下国内较火的组合，SHE。虚线部分为有新歌发布，第一首新歌发布带来的效应是巨大的，从日

播放量2000+直线上升到20,000+。果真，根据SHE的专辑发布时间和虾米音乐上的专辑发布时间是一致的，并且

2016.05.20有一首新歌《你曾是少年》作为电影主题曲发布，风靡一时。

<div><img src="/images/ali-music-competition/Fig5.png" width="100%"></div>

同样地，我们根据组合&英文猜测出下图歌手为Beatles，看到播放量有骤增的几天，例如2016.05.18出现播放量骤增的

原因极有可能是“花儿与少年”在利物浦游玩，并演唱了团队著名歌曲《hey, judy》，带来的怀旧效应。

<div><img src="/images/ali-music-competition/Fig6.png" width="100%"></div>

通过这种方式，我们确认了接近10位歌手的身份，让我们对播放量骤增情况出现的原因有了进一步的了解。更加重要的

是，由此我们可以引入一个新的特征：歌手某日的新闻总数。当某歌手当日有大量新闻出现时，我们可以推测该歌手会

出现日播放量骤增。为此，我写了一个爬虫程序，以“歌手”+“日期”为关键字爬取歌手的每日新闻数量。对于没有猜

出身份的歌手，我们默认该歌手没有出现爆炸性新闻。



### 用户记录分析 ###
到目前为止，我都没有从微观层面使用用户操作数据。但考虑到用户记录数据是最多的，因此我打算从用户的角度进行

建模。首先我画出了用户每日的操作记录，如下图所示：

<div><img src="/images/ali-music-competition/Fig7.png" width="100%"></div>

图中横坐标为日期，纵坐标为歌曲id，我们将同一个歌手的歌曲给定连续的id。蓝色正方形表示下载，红色圆圈表示播

放。可以看到，这位用户只听两位歌手的歌曲，并且都是下载之后开始播放。另外，他的探索欲望较低，歌曲一次性下

载完成之后就没有新增歌曲了。

<div><img src="/images/ali-music-competition/Fig8.png" width="100%"></div>


这位用户有一定的探索欲望，对于喜欢的歌曲会下载下来间断性地听，但也会不下载地尝试新鲜歌曲。通过上面的图示

，我们可以知道：1）下载后的歌曲，用户一般会间断性的持续听；2）用户会对同一个歌手的不同歌曲更感兴趣。


在分析单个用户的用户记录时，我突然发觉到用户操作记录与文本的相似性，并进行了这样的类比：

一首歌                               <==>        一个字

一个用户某段时间的操作记录           <==>        一段文字

一个用户的所有操作记录               <==>        一篇文章

进行这样的类比之后，所有关于自然语言处理的研究都可以应用到用户行为分析上面。如使用主题模型对用户进行聚类

，使用word embedding对歌曲进行聚类，等等。

通过上面的类比，我首先将每首歌曲映射到一个独特的id，然后将用户操作记录按照时间顺序排序转换为文本。然后利

用开源的word embedding代码，以这些文本为输入，计算歌曲的embedding vector。为了方便视觉查看，我用TSNE将高

维数据降维到2维。最后，因为歌曲数量较多，规律不明显，我将歌曲映射到歌手。结果如下图：

<div><img src="/images/ali-music-competition/Fig10.png" width="100%"></div>



图中不同的符号标记代表不同的歌手。可以看到，虽然在计算歌曲的embedding vector时我们并没有使用任何跟歌手有

关的信息，但同一个歌手的歌依然很好地聚集在一起，这说明通过用户记录得到的歌曲embedding确实具备某些语义信息

，侧面也反映了歌手是用用户选择听歌的重要依据。但图形中央明显有几个歌手聚集在一起，这说明单凭歌手信息无法

区分这一部分的歌曲。

同样地方式，我将歌曲映射到歌手性别，得到如下结果：

<div><img src="/images/ali-music-competition/Fig11.png" width="100%"></div>


这一次可以看到，中间部分区分地稍好一些了。说明歌手性别也是用户听歌的重要选择标准。

最后，我们将歌曲映射到歌曲语言，得到如下结果。上面的分析同样适用，说明歌曲语言也是用户选择听歌的依据之一

。

<div><img src="/images/ali-music-competition/Fig12.png" width="100%"></div>

当然，上面分析的歌手、性别、语言对用户选择歌曲的重要性是不言而喻的。我的分析除了以数据的形式印证了这一结

论以外，更加重要的是，现在我们对歌曲有了一种矢量化的定量表达，利用这种表达，可以方便地对歌曲进行聚类。通

过上面的分析，也可以确信，这种聚类会具有某些隐含的语义信息。