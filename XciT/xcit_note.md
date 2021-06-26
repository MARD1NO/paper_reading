repo：https://github.com/facebookresearch/xcit

#### 主要思想

类似Linear Attention的做法，对求attention操作中的QK操作反过来

$K^TQ$，这样能把复杂度从$O(N^2D)$降低为$O(ND^2)$

### 细节

1. 没有像原始attention除以一个$\sqrt{D_k}$，而是做了个l2norm
2. 为了避免l2norm后特征值过小，参考CaiT，加入了个temperature可学习参数，来进行缩放
3. 沿用分头机制
4. 分类采取CaiT的做法，引入classify attention
   



