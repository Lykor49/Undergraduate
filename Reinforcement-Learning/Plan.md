# RL

Reinforcement-Learning
├── Basic Concepts 基本概念
│   ├── State 状态
│   ├── Action 动作
│   ├── Policy 策略
│   ├── State transition 状态转移, State transition probability 状态转移概率
│   ├── Reward 奖励, Reward probability 奖励概率
│   ├── Trajectory and return 轨迹和回报
│   ├── Episode 回合
│   └── Markov decision process (MDP) 马尔可夫决策过程
│
├── Bellman Equation 贝尔曼公式
│   ├── State Value / Action Value
│   ├── Bellman Equation (elementwise form)
│   └── Bellman Equation (matrix-vector form)
│
├── Bellman Optimality Equation 贝尔曼最优公式
│   ├── Optimal policy / Optimal state value
│   ├── Bellman Optimality Equation (elementwise form)
│   ├── Bellman Optimality Equation (matrix-vector form)
│   ├── Greedy Policy
│   ├── Contraction Mapping Theorem
│   └── Iterative Solution of BOE
│
├── Value Iteration & Policy Iteration 值迭代 & 策略迭代
│   ├── Value Iteration
│   ├── Truncated Policy Iteration
│   └── Policy Iteration
│
├── Monte Carlo Learning 蒙特卡洛方法
│   ├── MC Basic
│   ├── MC Exploring Starts
│   └── MC ε-Greedy
│
├── Stochastic Approximation and Stochastic Gradient Descent 随机近似与随机梯度下降
│   ├── Incremental Mean Estimation 增量均值估计
│   ├── Robbins-Monro Algorithm 罗宾斯-门罗算法 (RM)
│   ├── Gradient Descent / Batch Gradient Descent / mini-batch Gradient Descent (GD / BGD / MBGD)
│   └── Stochastic Gradient Descent 随机梯度下降 (SGD)
│
├── Temporal-Difference Learning 时序差分方法
│   ├── TD-Learning (状态值估计)
│   ├── Sarsa (动作值估计)
│   ├── Expected Sarsa
│   ├── n-Step Sarsa
│   ├── Q-Learning (最优动作值估计)
│   ├── on-policy / off-policy
│   └── 时序差分算法统一框架
│
├── Value Function Approximation 值函数估计
│   ├── 表格法过渡函数法的思想
│   ├── 基于值函数的时序差分算法: 状态值估计 (蒙特卡洛、TD算法)
│   ├── 基于值函数的时序差分算法: 动作值估计 (Sarsa、Q-Learning)
│   └── 深度Q网络 (DQN)
│
├── Policy Gradient 策略梯度
│   ├── Policy-based 基于策略的 (从表格到函数 -> 引出函数表示策略)
│   ├── Metric of define optimal policy 定义最优策略的目标函数 (平均状态值、平均奖励)
│   ├── Gradient of metric 目标函数的梯度
│   └── Monte Carlo policy gradient 蒙特卡洛策略梯度 (REINFORCE)
│
└── Actor-Critic Methods
    ├── Q Actor-Critic (QAC)
    ├── Advantage Actor-Critic (A2C)
    ├── Off-policy 策略梯度定理
    └── Deterministic Actor-Critic (DPG) 




算法学习模版
1. 背景与目标 (Why + What)
算法为什么出现、前面方法有什么局限、具体想解决什么问题
2. 核心思想
用一段话把算法最核心的机制讲清楚
3. 算法流程
按照真正执行顺序将算法从输入到输出完整跑一遍 (Input -> Processing -> Update -> Output)
4. 核心公式与数学原理
真正决定算法本质的公式, 并解释公式为什么这样设计
5. 算法特性与关键问题
ex.on-policy/off-policy、优缺点、相邻算法区别、常见面试问题

