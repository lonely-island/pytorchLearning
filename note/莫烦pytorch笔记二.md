## pytorch

类似numpy，pytorch就是在神经网络领域代替numpy的模块

**神经网络在做什么？**

- 线性拟合
- 分类

## 安装

pytorch类似tensorflow使用tensor表示高维信息

参考[pytorch环境搭建](https://www.cnblogs.com/lonelyisland/p/12809422.html)

或者看pytorch官方文档

官网命令安装了两个东西

- torch
- torchvision:有一些数据库以及预训练好的网络，可以直接下载到本地的直接用--transform learning)

## 对比numpy和pytorch

可以进行一些矩阵相关的运算

[莫烦](https://morvanzhou.github.io/tutorials/machine-learning/torch/2-01-torch-numpy/)

另外参考pytorch官方网站文档

## variable变量

[莫烦](https://morvanzhou.github.io/tutorials/machine-learning/torch/2-02-variable/)

## 为什么需要激励函数？

- 线性方程

  y = Wx

- 非线性方程

  y = AF(Wx) ---掰弯了233

![image-20200608163055519](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608163101.png)

激励函数必须使可微分的，在反向传播back propagation的时候，只有可微分的才可以把误差传递回去

![image-20200608163248878](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608163251.png)

需要注意的是，如果隐藏层比较少，可以随便选择激活函数，在隐藏层比较多的时候，需谨慎考虑，存在[梯度爆炸和梯度消失]([https://www.google.com/search?q=%E6%A2%AF%E5%BA%A6%E7%88%86%E7%82%B8%E5%92%8C%E6%A2%AF%E5%BA%A6%E6%B6%88%E5%A4%B1&oq=%E6%A2%AF%E5%BA%A6%E7%88%86%E7%82%B8%E5%92%8C%E6%A2%AF%E5%BA%A6%E6%B6%88%E5%A4%B1&aqs=chrome..69i57.4453j0j7&sourceid=chrome&ie=UTF-8](https://www.google.com/search?q=梯度爆炸和梯度消失&oq=梯度爆炸和梯度消失&aqs=chrome..69i57.4453j0j7&sourceid=chrome&ie=UTF-8))的问题

**默认首选**

- 少量隐藏层中可以尝试各种

- CNN中推荐relu
- RNN 推荐relu 和 tanh

## 激励函数activation function

学习资料：

- 

- 见莫烦python的介绍激励函数视频

几种激活函数图像

![image-20200608163811659](https://raw.githubusercontent.com/lonelyislandXD/picLib/master/img/20200608163813.png)

另外softmax是一种做出来是概率图，不是线图

关于图像可以看莫烦python教程关于matplotlib，numpy以及pandas的介绍

## 回归（关系拟合）

回归：损失函数一般使用`torch.nn.MSELoss()`

```python
import torch
import matplotlib.pyplot as plt

x = torch.unsqueeze(torch.linspace(-1, 1, 100), dim=1)  # x data (tensor), shape=(100, 1)
y = x.pow(2) + 0.2*torch.rand(x.size())                 # noisy y data (tensor), shape=(100, 1)

# 画图
plt.scatter(x.data.numpy(), y.data.numpy())
plt.show()
```

## 分类

分类：损失函数一般使用`torch.nn.CrossEntropyLoss()`:比如类别[0,0,1] 计算出的概率[0.1,0.2,0.7]



## 快速搭建法

主要直接采用`torch.nn`提供的类来搭建-->对比之前使用`import torch.nn.functional as F`之后使用一系列函数如`relu()`

使用`import torch.nn.functional as F`搭建

```python
import torch
import torch.nn.functional as F

class Net(torch.nn.Module):
    def __init__(self, n_feature, n_hidden, n_output):
        super(Net, self).__init__()
        self.hidden = torch.nn.Linear(n_feature, n_hidden)
        self.predict = torch.nn,Linear(n_hidden, n_output)
        
    def forward(self, x):
        x = F.relu(self.hidden(x))
        x = self.predict(x)
        return x
```



使用`torch.nn`提供的类搭建

```python
import torch

net = torch.nn.Sequential(
	torch.nn.Linear(2,10)
    torch.nn.ReLU()
    torch.nn.Linear(10,2),
)
```

## 保存提取

主要有两种方式：

- 保存整个网络

  ```python
  torch.save(net1, 'net.pkl')
  ```

  

- 只保存网络中的参数（速度快，占内存少）

  ```python
  torch.save(net1.state_dict, 'net_params.pkl')
  ```

