## 入门

人工神经网络靠正向、反向传播，优化数学模型。

## 神经网络

输入层：直接接受传入的信息

输出层：输出的结果，通过结果看出神经网络对事物的认知

隐藏层：输入和输出之间各神经元组成的各个层面

![image-20200608143754228](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608143754.png)

**如何训练**

- 准备很多数据
- 训练（通过对比错误和正确差别，反向传播，改变一点点，通过改进的神经网络可以向正确的方向发展）

**激活/刺激函数(activation function)** 

激活一些神经元，传递的信息是对神经元最有价值的信息，比如传入一只猫的图片，部分神经元被激活，得出一个输出（比如判断结果是一条狗）

![image-20200608144423833](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608144423.png)

此时另一部分神经元被激活，容易被激活的迟钝，另一部分敏感起来，说明一些参数再被改变，逐渐调整后，得出正确的结果，是一只猫

![](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608145028.png)

## 梯度下降

优化问题--optimization

- newton's method
- least squares method
- gradient decent (常用)

![image-20200608145613659](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608145745.png)(wx-y)到(w-0)不是等号，只是一个推导。可以看到梯度下降到最低的地方cost最小

但是往往，w不止一个，两个是一个三维的，超过3个w很难画出来

简化版的只要找到梯度躺平的点， 但是可能有局部最优，全局最优。大部分时候是局部最优

![image-20200608150020738](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608150233.png)

## 黑盒

神经网络是一个黑盒:

输入-->加工(黑盒)-->输出

类比手电筒照亮黑盒子的过程

- 输入层-隐藏层1-隐藏层2-隐藏层3-输出层 （隐藏层123此时为黑盒   
- 输入层-隐藏层2-隐藏层3-输出层（此时输入层+隐藏层1为新的输入端，隐藏层23位新的黑盒
- 。。。

第一个输入层当做features，第二个输入层当做代表特征feature representations

**一个例子**

![image-20200608151648057](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608151648.png)

将输出层拆掉，可以看到一张数字的3个代表特征，通过右边那个图，可以看出一个分布，进而对输入的手写数字图片做一个区分。落在相同区域的数字认定为某个数字

![image-20200608151856901](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608152044.png)

**应用：**迁移学习

![image-20200608152141141](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608152255.png)

去掉输出层并且套上另外一个神经网络的输入层（比如这里已经获取关于右边词汇分类的代表特征，作为下一个神经网络的输入，可以进一步判断各个物品的价值）

![](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608152514.png)

