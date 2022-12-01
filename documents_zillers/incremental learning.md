# incremental learning

## core : solving **catastrophic forgetting**

Reason:

做task2的时候优化的方向让task1的loss变高了，所以regulazation

![image-20221006013530908](../../Library/Application%20Support/typora-user-images/image-20221006013530908.png)

![image-20221025225144764](../../Library/Application%20Support/typora-user-images/image-20221025225144764.png)

其实就是EWC这篇论文



通过bi控制哪些$\theta$比较重要

所以core就是bi该怎么设置：

![image-20221025230952326](../../Library/Application%20Support/typora-user-images/image-20221025230952326.png)

## features:


* **多任务的，但它允许在进入下一个任务之前多次处理当前任务的数据**
* 学习新知识的同时能够保留以前学习到的大部分知识，也就是模型在旧任务和新任务上均能表现良好。
* 计算能力与内存应该随着类别数的增加固定或者缓慢增长，最理想的情况是一旦完成某一任务的学习，该任务的观测样本便被全部丢弃。
* 模型可以从新任务和新数据中持续学习新知识，当新任务在不同时间出现，它都是可训练的。

## 基于正则化的增量学习

![image-20221006013322204](../../Library/Application%20Support/typora-user-images/image-20221006013322204.png)

**通过给新任务的损失函数施加约束的方法来保护旧知识不被新知识覆盖**



![img](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9pbWctYmxvZy5jc2RuaW1nLmNuL2ltZ19jb252ZXJ0L2IwNjUwMTIyZDEwN2JjNjkzNWI5MDYxZThhZjNhMGE1LnBuZw?x-oss-process=image/format,png)

![image-20221006013914405](../../Library/Application%20Support/typora-user-images/image-20221006013914405.png)

## evaluation

![image-20221006013144351](../../Library/Application%20Support/typora-user-images/image-20221006013144351.png)

所以uppercase就是把新旧任务放在一起训练

## Baseline

主要就是要把所有task顺序训练一遍以后才可以说

Acc:准确率

MF1: 求取每一类的F值之后求平均值

![image-20221011010438592](../../Library/Application%20Support/typora-user-images/image-20221011010438592.png)

### 知识蒸馏

![image-20221026004628240](../../Library/Application%20Support/typora-user-images/image-20221026004628240.png)

![image-20221026005249707](../../Library/Application%20Support/typora-user-images/image-20221026005249707.png)

<img src="../../Library/Application%20Support/typora-user-images/image-20221026005325338.png" alt="image-20221026005325338" style="zoom:50%;" />

## Typical paper

### iCaRL 基于回放的增量学习

以类增量学习的方式，只需要存储旧数据的少量类训练数据和少量新类的数据



#### 类增量的标准

a) 当新的类别在不同时间出现，它都是可训练的
b) 任何时间都在已经学习过的所有类别中有很好的分类效果
c) 计算能力与内存应该随着类别数的增加固定或者缓慢增长

#### 主要方法

- 用最接近平均的例子这一规则进行分类(classification by a nearest-mean-of-exemplars rule)
- 基于群的优先示例选择(prioritized exemplar selection based on herding)
- 利用知识蒸馏和原型演练进行表征学习(representation learning using knowledge distillation and prototype rehearsal)



### 通过给新任务的损失函数施加约束的方法来保护旧知识不被新知识覆盖（regulization,目前发展的最好）

LWC

EWC的fisher怎么算呢

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200118202409497.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RoYWl1ZGE=,size_16,color_FFFFFF,t_70)

![image-20221026204849831](../../Library/Application%20Support/typora-user-images/image-20221026204849831.png)

### 参数隔离的增量学习...

a
