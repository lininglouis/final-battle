# 提升知识点
排序稳定性，复杂度，   归并，堆排序，快排
python所有的关键字 \__getitem__   \__call__含义

python Method Resolution
手推神经网络

递归的使用，在排列组合里面
宽度优先搜索高级模板
动归

python resnet zeropadding是否需要新参数？
卷积时间复杂度
宽度优先搜索的时间复杂度



Resnet的bottleeck和buildingblock对比
1. bottleneck 维度更深
2. 时间计算复杂度一样
3. bottleneck维度更深，输入输出的参数更多。空间复杂度高
也就是说bottle计算复杂度不高，可以学习更深特在，但是空间复杂度高（输入输出参数多）

以两个(3x3,64)的卷积 输入输出都是64  和 三个（1x1,64) (3x3,64), (1x1, 256)  输入输出都是256 为例子

卷积层参数只和 kernelsize，出入channel有关， 参数量 = (kernel_size * kernel_size * inchannel + 1) * outchannel
buildblock  (3*3*64+1）*64  *2 = 73856
bottleneck  (1*1*256+1)*64 + (3*3*64+1)*64 + (1x1x64+1)*256 =  70016



时间复杂度
注1：为了简化表达式中的变量个数，这里统一假设输入和卷积核的形状都是正方形。 
注2：严格来讲每层应该还包含1个Bias参数，这里为了简洁就省略了。
M:输出特征图（Feature Map）的尺寸。
K:卷积核（Kernel）的尺寸。
Cin:输入通道数。
Cout:输出通道数。
横向做 M2次运算，  纵向做Cout次运算  每次cube运算是 K2*Cin
M^2*K^2*Cin*Cout = O(M^2 * K^2 * Cin * Cout)

空间复杂度
空复杂度复杂度：Time~O(K^2 * Cin * Cout)   因为参数共享了，所有的卷积层K都只有一个，所以M^2次运算并不影响空间复杂度。


# Past Puzzles

--------------------------0811----------------------
```
8邻域编码
卡方检验
abcde依次入栈，b开头的序列有多少
细化，开运算，闭运算区别
排序稳定性
堆排序复杂度
重采样？上采样？
有向图的邻结矩阵可以计算某个节点的 出度入度么？
t分布，高斯分布
后续中序遍历，推先序序列
二差搜索数和二分的关联。
中小数据集用什么模型好？

一道排列组合题，递归思想

深度学习综述方法方向理解
计算机视觉流程。
```

--------------------------0812   NE Lab----------------------
```
欠拟合  过拟合  和 (variance, bias)关系
boosting bagging有没有类似nn dropout效果？
cnn共享卷积有没有抗拟合效果？
Representation learning指的是那些？ Rf gbdt nn？
dqn的经验回放理解
一个python list 为a，len(a)操作和 a[-1] = 0的时间复杂度  （https://wiki.python.org/moin/TimeComplexity）
gbdt和xgboost区别
random walk 从1到10, 每次可以50%一步，或者移动两步，请问到4停止需要多少步（期望）
softmax 输入是否可以输入全都是0
hmm 知道观察序列和状态序列，用什么方法来估计参数
resnet zero padding 会不会导致参数增多
宽搜的时间复杂度
word2vec, fasttext,等那种方法适合处理oov（out of vacabulary)
VAE
t-sne和pca各自优缺点 适用数据情况

大题
一个（4,4,6,16）卷积的权重参数个数计算。
dqn设计flappybird思路
宽度优先搜索大题
Lstm  推导


```


### Thoughts 思考

#### 内排序 外派序-排序稳定性
* 所谓的内排序是指所有的数据已经读入内存，在内存中进行排序的算法。排序过程中不需要对磁盘进行读写。同时，内排序也一般假定所有用到的辅助空间也可以直接存在于内存中。
* 与之对应地，另一类排序称作外排序，即内存中无法保存全部数据，需要进行磁盘访问，每次读入部分数据到内存进行排序。

一般归并排序空间复杂度为o(n) 占用空间较多，不经常作为内排序，而是作为外派序用到
而快排空间为o(1) ，经常做为内排序。

插入排序是o(n2)的时间复杂度
o(nlogn) 堆排序（o(n)空间。不稳定）     归并排序(o(n+logn))空间,稳定排序）    和冒泡排序(o(1) 不稳定)


### resnet 参数free---------------------------
resnet的zero_padding是参数free的，不增加新的学习参数
