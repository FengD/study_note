## CUDA Study

https://zhuanlan.zhihu.com/p/263526076 （各种卷积介绍）
离散卷积是一种能够保留数据结构属性的一种线性变换，它是稀疏的（仅利用部分输入单元得到输出）并且是参数复用的（同样的权重参数被用于与输入的不同部分进行乘法操作）。



https://www.cnblogs.com/rainbow70626/p/6498738.html （cuda grid block 区别）


1. 激活函数 激活函数是为了使卷积后的线性结果变为非线性结果。  
https://blog.csdn.net/kangyi411/article/details/78969642
https://blog.csdn.net/qq_30815237/article/details/86700680
https://blog.csdn.net/qq_23269761/article/details/80901411
例如：

input feature map  -》  kernal -》 linear result （y = ax + b）  -> 激活函数f（y） 激活函数可以是任何一个  -> output feature map

1. sigmod
1) 当输入稍微远离了坐标原点，函数的梯度就变得很小了，几乎为零。在神经网络反向传播的过程中，我们都是通过微分的链式法则来计算各个权重w的微分的。当反向传播经过了sigmod函数，这个链条上的微分就很小很小了，况且还可能经过很多个sigmod函数，最后会导致权重w对损失函数几乎没影响，这样不利于权重的优化，这个问题叫做梯度饱和，也可以叫梯度弥散。

2) 函数输出不是以0为中心的，这样会使权重更新效率降低。对于这个缺陷，在斯坦福的课程里面有详细的解释。

3) sigmod函数要进行指数运算，这个对于计算机来说是比较慢的。

2. tanh
tanh是双曲正切函数，tanh函数和sigmod函数的曲线是比较相近的，咱们来比较一下看看。首先相同的是，这两个函数在输入很大或是很小的时候，输出都几乎平滑，梯度很小，不利于权重更新；不同的是输出区间，tanh的输出区间是在(-1,1)之间，而且整个函数是以0为中心的，这个特点比sigmod的好。

一般二分类问题中，隐藏层用tanh函数，输出层用sigmod函数。不过这些也都不是一成不变的，具体使用什么激活函数，还是要根据具体的问题来具体分析，还是要靠调试的。

3. ReLU



2. flops = 2 * macs  

Most of modern hardware architectures uses FMA instructions for operations with tensors.
FMA computes a*x+b as one operation. Roughly GMACs = 0.5 * GFLOPs

https://www.jianshu.com/p/b5157e31c409
