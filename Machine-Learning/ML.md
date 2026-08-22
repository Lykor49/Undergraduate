# ML

- date: 2026.8.15

# 1. What is Machine Learning?  
- Definition: Field of study that gives computers the ability to learn without being explicitly programmed.

- Supervised learning / Unsupervised learning

## Supervised learning
- Supervised learning: Learns from being given "right answers"

- Regression: Predict a number infinitely many possible outputs

- Classification: Predict categories, small number of possible outputs

## Unsupervised learning
- Unsupervised learning: Find something interesting in unlabeled data

- Clustering: Group similar data points together
- Anomaly detection: Find unusual data points
- Dimensionality reduction: Compress data using fewer numbers

- date: 2026.8.16

# 2. Linear Regression 线性回归
- Definition: Linear regression is a supervised learning model that predicts numbers as the output.
- 定义: 线性回归是一种监督学习模型，通过线性函数对输入特征进行建模，用于预测连续的数值输出
- 线性回归的目标: 寻找参数w和b使得代价函数J达到最小值

## Cost Function 代价函数
- Definition: A cost function measures how well a machine learning model is performing by measuring the difference between its predictions and the actual values.
- 定义: 代价函数用于衡量机器学习模型的预测效果，通过计算模型预测值与真实值之间的差异来评价模型的性能
- J 用于衡量平方误差有多大的代价函数
- 线性回归代价函数是个碗状, 神经网络模型可能是多谷结构

- date: 2026.8.18

# 3. Gradient Descent 梯度下降
- Definition: Gradient descent is an algorithm for finding values of the model parameters that minimize the cost function.
- 定义: 梯度下降是一种通过不断调整模型参数，使代价函数逐步减小并趋近最小值的优化算法
- 趋近局部极小值, 导数会变小, 更新的步长也会变小
- 对于凸函数（Convex Function），梯度下降可以找到全局最小值
- 对于非凸函数（Non-convex Function），梯度下降可能收敛到局部极小值，因此不保证找到全局最小值

## Learning Rate 学习率
- 学习率过小, 梯度下降会很慢; 学习率过大, 梯度下降可能会超过, 可能永远不会达到最小值, 无法收敛

## "Batch" gradient descent 批量梯度下降
- Definition: Each step of gradient descent uses all the training examples.
- 定义: 在批量梯度下降中，梯度下降的每一次参数更新都会使用全部训练样本来计算梯度


# 4. Multiple Linear Regression 多元线性回归: 具有多个特征的线性回归
- Definition: Multiple linear regression is a linear regression model that uses multiple input features to predict an output.
- 定义: 多元线性回归是一种使用多个输入特征，通过线性函数来预测连续数值输出的回归模型

## Vectorization 向量化
- Definition: Vectorization is a technique for implementing mathematical operations on entire vectors or matrices instead of using explicit loops.
- 定义: 向量化是一种直接对整个向量或矩阵进行数学运算、而不是使用显式循环逐个计算的实现方法，可以使代码更简洁、计算效率更高

## Normal equation 正规方程 (仅了解)
- Definiton: The normal equation is an alternative to gradient descent for linear regression. It can solve for $w$ and $b$ directly without iterations.
- 定义: 正规方程是线性回归中梯度下降法的一种替代方法，可以不经过迭代，直接求解参数 $w$ 和 $b$
- 缺点:
  - 主要用于线性回归
  - 不能推广到其他学习算法
  - 当特征数量很大时（如 > 10,000）计算较慢

## Feature Scaling 特征缩放
- Definition: Feature scaling is a technique that rescales the features so that they have comparable ranges of values.
- 定义: 特征缩放是一种将不同特征的取值范围调整到相近尺度的方法，使各个特征具有可比较的数值范围，从而帮助梯度下降更快地收敛
- 常用方法: Mean normalization (均值归一化)、Z-score normalizaiton (Z-score归一化)

## Feature Engineering 特征工程
- Definition: Using intuition to design new features, by transforming or combining original features.
- 定义: 特征工程是通过对已有特征进行变换或组合，构造新的特征，从而帮助学习算法更好地进行预测的过程

## Polynomial Regression 多项式回归
- Definition: Polynomial regression is a form of linear regression that uses polynomial features, such as $x^2$, $x^3$, and higher-order terms, to model nonlinear relationships between features and the target.
- 定义: 多项式回归是在线性回归中加入 $x^2$、$x^3$ 等多项式特征，从而使模型能够拟合输入特征与目标值之间非线性关系的方法

- 日期: 2026.8.20

# 5. Logistic Regression 逻辑回归
- Definition: Logistic Regression is a supervised learning algorithm used for classification that models the probability that an input belongs to a particular class.
- 定义: 逻辑回归是一种用于分类问题的监督学习算法，它通过将输入特征的线性组合输入 Logistic（Sigmoid）函数，来估计样本属于某一类别的概率

## Decision Boundary 决策边界
- Definition: A decision boundary is the boundary that separates regions of the input space assigned to different classes by a classification model.
- 定义: 决策边界是分类模型在输入空间中用于划分不同类别区域的边界

## Logistic loss function 损失函数
- Definition: The loss function measures how well the logistic regression model predicts the true label of a single training example. For binary classification, logistic regression uses the log loss (binary cross-entropy loss).
- 定义: 逻辑回归的损失函数用于衡量模型对单个训练样本预测结果与真实标签之间的误差。对于二分类问题，逻辑回归通常使用对数损失（Log Loss），也称二元交叉熵损失（Binary Cross-Entropy Loss）

## Gradient descent for logistic regression 梯度下降
类似线性回归的概念: 
- Gradient descent
- Vectorization 
- Feature Scaling 

## Overfit / Underfit 过拟合 / 欠拟合
- Overfit <-> high variance  underfit <-> high bias
- 过拟合: 指模型对训练数据拟合得过于充分，甚至学习了其中的噪声和无关模式，从而导致模型在未见过的新数据上表现较差
- 欠拟合: 指模型过于简单，无法充分学习训练数据中的基本规律，因此在训练数据和未见过的新数据上都表现较差

## 解决过拟合的方法
- Collect more training examples 更多的数据集
- Select features to include/exclude 减少特征选择
- Regularization 正则化 (通常 Reduce the size of parameters $w_j$)

## Regularization 正则化
- Definition: Regularization is a technique used to reduce overfitting by adding a penalty term to the cost function, discouraging excessively large model parameters and helping the model generalize better to unseen data.
- 定义: 正则化是一种用于减少过拟合的技术，通过在代价函数中加入惩罚项，限制模型参数过大，从而降低模型复杂度并提高对未见数据的泛化能力
- 正则化的代价函数
- 正则化的线性回归的梯度下降
 - 扩: 正则化的数学原理, 数学推导(移项, $w_j$每次乘一个小于1的数(限制))
- 正则化的逻辑回归的梯度下降


日期: 2026.8.22

# 6. Neural Networks 神经网络
- Definition: A neural network is a machine learning model composed of interconnected layers of computational units called neurons, which learn hierarchical representations from data by applying weighted linear transformations followed by nonlinear activation functions.
- 定义: 神经网络（Neural Network）是一类由多层相互连接的计算单元（神经元）组成的机器学习模型，通过对输入进行加权线性变换并结合非线性激活函数，从数据中学习分层特征表示

## Forward Propagation 前向传播
- Definition: Forward propagation is the process of passing input data through the layers of a neural network, from the input layer to the output layer, by computing weighted sums and applying activation functions to produce the final prediction.
- 定义: 指输入数据从神经网络的输入层开始，逐层经过加权求和与激活函数计算，最终传递到输出层并得到模型预测结果的过程



