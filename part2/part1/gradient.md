## 梯度下降二

符号表示：模型参数 $$\theta$$ ，目标函数$$$J(\theta)$$ , 学习率$$\alpha$$，$$t$$不同时刻。

**1. Gradient Descent**

\(1\)计算目标函数关于参数梯度  
$$g_t = \triangledown  _{\theta}J(\theta)$$  
（2）根据历史梯度计算一阶和二阶动量  
$$m_t = \phi (g_1,g_2,g_3,,,,,,g_t) $$  
$$m_t = \upsilon (g_1,g_2,g_3,,,,,,g_t) $$  
\(3\)更新模型参数

$$\theta_{t+1} = \theta_{t} - \frac{1}{\sqrt{\upsilon _t + \epsilon}}m_t$$  
其中，$$\epsilon$$为平滑项，防止分母为0，通常 1e-8。

**2. 朴素 SGD \(Stochastic Gradient Descent\) **  
不使用无动量  
$$m_t = \alpha g_t$$  
$$\epsilon = 0$$  
$$\theta_{i+1} = \theta_{t} - \alpha g_t$$

