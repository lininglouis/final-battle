

比如 bn，写出公式、为什么需要额外的两个参数b和y、测试的时候怎么做的、参数怎么存储的、均值方差用的是训练哪一阶段的、如何更新参数、caffe中BN的实现分几层、测试的时候是否可以将卷积核BN参数合并？公式是什么，caffe中如何修改参数、如果batch只能容纳一个图像怎么训练。恩，我只是举了一个问题的例子，有很多类似问题 代码，计算两个候选框的overlap

https://www.nowcoder.com/discuss/58508?type=0&order=4&pos=27&page=1


* depth-wise卷积时间复杂度
* anchor机制如何改进？
* 给定特征，如何估计概率密度？一般估计概率密度的常见思路？
* 特征选择的常见思路？
* nms写出来， def(bbox_list, score_list, topK, threshold=0.7)
* rfcn和fastercnn对比
* roi align和roi pooling不同
* fastercnn yolo对比
* 多个无序小文件，如何合并为一个大文件，有内存2g要求
* 1000w个视频，现在有一个新的文件，确定是否是相同视频。 如何选取特征，完成这个任务。
