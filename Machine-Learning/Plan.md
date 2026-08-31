# ML

Machine Learning
├── What is Machine Learning?
│   ├── definition
│   └── Supervised learning / Unsupervised learning
│   
├── Supervised learning 监督学习
│   ├── definition
│   └── Regression / Classification (回归 / 分类)
│
├── Unsupervised learning 无监督学习
│   ├── definition
│   └── Clustering / Anomaly detection / Dimensionality reduction (聚类 / 缺陷检测 / 降维)
│
├── Linear Regression 线性回归
│   ├── Model 模型
│   │   ├── Linear Regression definition
│   │   └── Cost Function 代价函数
│   │
│   ├── Optimization 优化
│   │   ├── Gradient Descent 梯度下降
│   │   ├── Learning Rate 学习率
│   │   └── Normal Equation 正规方程（仅了解）
│   │
│   ├── Multiple Features 多特征
│   │   ├── Multiple Linear Regression 多元线性回归
│   │   ├── Vectorization 向量化
│   │   └── Feature Scaling 特征缩放
│   │
│   └── Feature Engineering 特征工程
│       └── Polynomial Regression 多项式回归
│  
├── Logistic Regression 逻辑回归
│   ├── Model 模型
│   │   ├── Logistic Regression definition
│   │   ├── Sigmoid Function
│   │   ├── Decision Boundary 决策边界
│   │   └── Loss Function / Cost Function 损失函数 / 代价函数
│   │
│   ├── Optimization 优化
│   │   ├── Gradient Descent 梯度下降
│   │   └── Learning Rate 学习率
│   │
│   ├── Multiple Features 多特征
│   │   ├── Vectorization 向量化
│   │   └── Feature Scaling 特征缩放
│   │
│   └── Generalization 泛化
│       ├── Overfitting / Underfitting 过拟合 / 欠拟合
│       └── Regularization 正则化
│  
├── Machine Learning Development 机器学习开发
│   ├── Iterative Development 迭代开发
│   ├── Error Analysis 误差分析
│   ├── Data augmentation 数据增强
│   ├── Transfer Learning 迁移学习
│   └── Machine Learning Project Cycle 机器学习项目完整周期
│
├── Decision Trees 决策树
│   ├── Model 模型
│   │   ├── Decision Tree definition
│   │   └── Node / Branch / Leaf 节点 / 分支 / 叶节点
│   │
│   ├── Learning 学习过程
│   │   ├── Entropy 熵 / Purity 纯度
│   │   ├── Information Gain 信息增益
│   │   └── Splitting Criterion 分裂准则
│   │
│   ├── Features 特征处理
│   │   ├── Categorical Features 类别特征
│   │   │   └── One-Hot Encoding 独热编码
│   │   └── Continuous Features 连续特征
│   │
│   └── Tree Ensembles 树集成
│       ├── Bagging / Sampling with Replacement
│       ├── Random Forest 随机森林
│       └── XGBoost
│ 
├── Unsupervised Learning 无监督学习
│   ├── Clustering 聚类
│   │   ├── Clustering definition
│   │   ├── K-Means Clustering K均值聚类
│   │   ├── Optimization Objective 优化目标
│   │   ├── Initializing K-Means K均值初始化
│   │   └── Choosing Number of Clusters 聚类数量选择
│   │
│   └── Anomaly Detection 异常检测
│       ├── Anomaly Detection definition
│       ├── Gaussian Distribution 高斯分布
│       ├── Evaluation 异常检测评估
│       ├── Anomaly Detection vs Supervised Learning
│       └── Feature Selection 特征选择
│
└── Recommender Systems 推荐系统 (暂时跳过)
    ├── Collaborative Filtering 协同过滤
    │   ├── Collaborative Filtering definition
    │   ├── User / Item Features 用户 / 商品特征
    │   ├── Collaborative Filtering Algorithm 协同过滤算法
    │   └── Binary Labels 二值标签
    │
    ├── Implementation 实现
    │   ├── Mean Normalization 均值归一化
    │   └── Finding Related Items 查找相似项目
    │
    └── Content-Based Filtering 基于内容的过滤
        ├── Content-Based Filtering definition
        ├── Collaborative Filtering vs Content-Based Filtering
        └── Deep Learning for Content-Based Filtering


Deep Learning
├── Neural Networks 神经网络
│   ├── Model 模型
│   │   ├── Neural Network definition
│   │   ├── Neuron / Layer 神经元 / 层
│   │   ├── Neural Network Architecture 网络结构
│   │   └── Forward Propagation 前向传播
│   │
│   ├── Activation Function 激活函数
│   │   ├── Sigmoid
│   │   ├── ReLU
│   │   └── Linear Activation
│   │
│   ├── Training 训练
│   │   ├── Loss Function / Cost Function 损失函数 / 代价函数
│   │   ├── Backpropagation 反向传播
│   │   └── Gradient Descent 梯度下降
│   │
│   ├── Multiclass Classification 多分类
│   │   ├── Softmax
│   │   └── Cross-Entropy Loss 交叉熵损失
│   │
│   ├── Optimization 优化
│   │   └── Adam Optimizer
│   │
└───├── Diagnostic 评价
        └── Precision / Recall / F1 score


Reinforcement Learning 强化学习
├── Basic Concepts 基本概念
│   ├── Reinforcement Learning definition
│   ├── Agent / Environment 智能体 / 环境
│   ├── State 状态
│   ├── Action 动作
│   ├── Reward 奖励
│   └── Policy 策略
│
├── Return 回报
│   ├── Return definition
│   ├── Discount Factor 折扣因子
│   └── Discounted Return 折扣回报
│
├── Value Function 价值函数
│   ├── State-Action Value Function Q(s,a)
│   ├── Bellman Equation 贝尔曼方程
│   └── Stochastic Environment 随机环境
│
├── Q-Learning Q学习
│   ├── Q-Learning Algorithm
│   ├── Exploration / Exploitation 探索 / 利用
│   └── ε-Greedy Policy ε-贪婪策略
│
└── Deep Reinforcement Learning 深度强化学习
    ├── Continuous State Space 连续状态空间
    ├── Neural Network Approximation 神经网络近似
    ├── Deep Q-Network (DQN)
    ├── Experience Replay 经验回放
    ├── Mini-Batch 小批量训练
    └── Soft Update 软更新