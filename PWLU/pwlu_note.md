标题：Learning specialized activation functions with the Piecewise Linear Unit

### 主要思想

就整个X区域设置上下界，然后平均分成N份

不同区域均有不同的斜率

而不恰当的输入范围设置，会导致input-boundary misalignment，于是论文采取以下做法

1. 前几轮先把pwlu设置成relu的形状，并对参数不更新
2. 采取running mean/var，统计输入数据的均值方差
3. 运用3-sigma原则，将上下界设置为

$$
\mu - 3*\sigma, \mu + 3*\sigma \\
K_{L}, K_{R} = 0, 1
$$

再开始进行更新

作者将N设置成16，并将这个预热轮数设置为5

一些有趣的观察是：在较浅的层，呈现的是Linear。在较深的层呈现的是V-shape形状

