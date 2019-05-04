## 梯度下降

公式：

$$ \theta_{i+1} = \theta_{i} - \alpha \frac{\partial f}{\partial \theta}$$

对于：

$$y_{p,i} = ax_i + b$$

$$loss = \frac{1}{2m} \sum_{i=1}^{m}(y_{p,i} - y_i)^2 $$ 

$$loss = \frac{1}{2} \sum_{i =1}^{m} \frac{1}{m}(ax_i + b  - y_i)^2$$

单独分析一项：

$$loss_i = \frac{1}{2} (ax_i + b - y_i)^2$$

需要优化的参数为a和b，分别求偏微分：

$$\frac{\partial loss_i}{\partial a} = (ax_i +b -y_i)x_i$$

$$\frac{\partial loss_i}{\partial b} = (ax_i +b -y_i)$$

loss函数前加$$\frac{1}{2},目的就是在求偏微分时可以和掉平方项。$$

将每一个$$\frac{\partial loss_i}{\partial a} $$和$$\frac{\partial loss_i}{\partial b}$$累加：

$$\frac{\partial loss}{\partial a} = \frac{1}{m} \sum_{i=1}^{m} \frac{\partial loss_i}{\partial a}$$

$$\frac{\partial loss}{\partial b} = \frac{1}{m} \sum _{i =1}^{m} \frac{\partial loss_i}{\partial b}$$

将$$\frac{\partial loss}{\partial a}$$和$$\frac{\partial loss}{\partial b}$$分别记作$$\triangledown a$$和$$\triangledown b$$:

$$a_{new} = a - \alpha \triangledown a $$
$$b_{new} = b - \alpha \triangledown b $$

##随机梯度下降（Stochasitc Gradient Descent ）
随机梯度一次迭代过程中只选取一个样本进行计算loss。优点：收敛快，计算快，但会有局部震荡。
只计算一个损失：

$$loss = \frac{1}{2} (y_{p,i} - y_i)^2 $$ 

$$loss = \frac{1}{2} (ax_i + b  - y_i)^2$$

$$\frac{\partial loss}{\partial a} = \frac{\partial loss}{\partial a}$$

$$\frac{\partial loss}{\partial a} = (ax_i +b -y_i)x_i$$

$$\frac{\partial loss}{\partial b} = (ax_i +b -y_i)$$

将$$\frac{\partial loss}{\partial a}$$和$$\frac{\partial loss}{\partial b}$$分别记作$$\triangledown a$$和$$\triangledown b$$:

$$a_{new} = a - \alpha \triangledown a $$
$$b_{new} = b - \alpha \triangledown b $$

###mini-batch gradient descent 
小批量梯度下降法（mini-batch gradient descent）主要思想就是每次只拿总训练集的一小部分来训练，比如一共有5000个样本，每次拿100个样本来计算loss，更新参数，50次后完成整个样本集的训练，为一轮（epoch）。由于每次更新用了多个样本来计算loss，就使得loss的计算和参数的更新更加具有代表性，不像原始SGD很容易被某一个样本给带偏。







