# RL

- 日期: 2026.9.8
- 1. Basic Concepts: state, action, reward, return, episode, policy; MDP; 
- 2. Bellman Equation: state value; Bellman equation; Policy evaluation
- 3. Bellman Optimality Equation: Optimal policy 最优策略; Optimal state value;    Bellman Optimality equation 贝尔曼最优公式
- 4. Value Iteration & Policy Iteration: 迭代算法; Policy update, value update
- 5. Monte Carlo Learning: model-free learning
- 6. Stochastic Approximation: Incremental manner 增量式算法思想
- 7. Temporal-Difference Learning 时序差分方法
- 8. Value Function Approximation
- 9. Policy Gradient Methods
- 10. Actor-Critic Methods

- 日期: 2026.9.9

# 第 1 课 - 基本概念 (State, Action, Policy等)
- 智能体的任务是从一个初始区域出发, 最终达到目标区域 (针对例子而言)

## State 状态
- State 状态: 描述了智能体与环境的相对状况
- State space 状态空间: 所有状态的集合 S

## Action 动作
- Action 动作: For each state, there are many possible actions.
- Action space 动作空间: 所有动作的集合 A

## State transition 状态转移
- State transition 状态转移: 当执行一个动作时, 智能体可能从一个状态转移到另一个状态
- 每一个状态的每一个动作都会对应一个状态转移过程
- 表格法: 只能描述确定性的状态转移过程; 条件概率分布: 描述随机性的状态转移过程

## Policy 策略
- Policy 策略: 告诉智能体在每一个状态应该采取什么样的动作

Policy representation
- Intuitive representation 直观表示: We use arrows to describe a policy.
- Mathematical representation 数学表示: using conditional probability

Two Policy
- Deterministic policy 确定性策略: For a given state s, the policy always selects the same action a.
- Stochastic policy 随机策略: For a given state s, the policy defines a probability distribution over possible actions.

## Reward 奖励
- Reward 奖励: 在一个状态执行一个动作后, 智能体会获得奖励r
- 正的奖励表示我们鼓励智能体采取相应的动作; 负的奖励表示我们不鼓励智能体采取该动作

## Trajectory and return 轨迹和回报
- Trajectory 轨迹: 指的是一个 “状态-动作-奖励” 的链条

- Return 回报: 沿着一条轨迹, 智能体会得到一系列的即时奖励, 这些即时奖励之和称为回报
- 回报由即时奖励(immediate reward)和未来奖励(future reward)组成
- 回报可以用于评价一个策略的 “好坏”

- Discounted Return 折扣回报: 不同时刻得到的奖励添加相应的折扣再求和
- 用处1: 轨迹可能是无限长的, 不用担心回报会发散到无穷
- 用处2: 折扣因子可以用来调整对近期或远期奖励的重视程度 

- Discount rate 折扣因子: 计算Return时, 用来降低未来Reward权重的系数
- 概括: 折扣因子决定A1在评价一个动作时, 对未来运动结果看得有多远、看得有多重

## Episode 回合
- Episode 回合: 智能体从初始状态开始到终止状态停止的过程

## Markov decision process (MDP) 马尔可夫决策过程
- MDP 定义: 智能体在一个环境中，根据当前状态选择动作，环境随后转移到新的状态并给予奖励，智能体不断重复这一过程，以最大化长期累计回报。
- Markov Property 马尔可夫性质: 在给定当前状态的条件下，未来与过去的完整历史无关。表示下一个状态和奖励仅依赖于当前时刻的状态和动作, 而与之前时刻的状态和动作无关
- Markov process 马尔可夫过程: 马尔可夫过程是满足马尔可夫性质的随机过程，即未来状态的概率分布只依赖于当前状态，而不依赖于过去的历史状态


# 第 2 课 - Bellman Equation 贝尔曼公式
- 状态值 可以作为评价一个策略好坏的指标
- 贝尔曼方程 描述了所有状态值之间的关系; 求解贝尔曼方程 可以得到状态值 进而评价一个策略的好坏
- Boostrapping 自举法: 利用已有的价值估计（Value Estimate），来更新当前状态或动作的价值估计
- 自举的思想: v1, v2, v3, v4 可以从其自身v2, v3, v4, v1得到

## State Value 状态价值
- 引入: 回报不适用于一般化的随机情况, 从一个状态出发可能会得到不同的轨迹和回报, 提出状态值来评价随机情况
- 定义: 在给定策略 π 下, 智能体从某一状态 s 出发, 该策略所能获得的未来累计折扣奖励（Return）的期望值
- 公式 (.ipynb)
- Question1 

## Bellman equation 贝尔曼公式
- 引入: 贝尔曼公式 描述了所有状态值之间的关系, 帮助我们计算状态值
- 定义: 贝尔曼方程描述在给定策略 π 下，当前状态价值与即时奖励及下一状态价值之间的递归关系
- 定义式, 展开形式, 推导 (.ipynb)

## Matrix-vector form of Bellman equation 矩阵-向量形式的贝尔曼方程
- 引入: 每个状态都有一个 Bellman Equation，将所有状态的方程组合成线性方程组，引出矩阵向量形式
- 定义: 矩阵形式使用状态价值向量、期望奖励向量和状态转移矩阵，统一表示给定策略下所有状态的价值递归关系
- 作用: 将 Policy Evaluation 转化为线性方程组的求解问题，为后续迭代策略评价提供数学基础
- 核心公式, 解析解 (.ipynb)

## Action Value 动作价值
- 引入: Action Value 来评价具体动作的长期价值
- 定义: 在一个状态采取一个动作之后获得的回报的期望值
- 作用: 评价当前状态下各个 Action 的长期价值，为动作选择和 Policy Improvement（策略改进）提供依据
- 定义式, 核心公式, 与状态值的关系 (.ipynb)


# 第 3 课 - Bellman optimality equation(BOE)
- 强化学习终极目标：寻找最优策略
- 核心概念：最优状态值 (可以定义最优策略)；核心工具：贝尔曼最优方程


## Optimal Policy 最优策略
- 引入：强化学习的目标是寻找能够获得最大长期回报的策略，引入最优策略
- 定义：如果一个策略 π* 在所有状态下的 State Value 都不小于其他任意策略，则称该策略为最优策略，该最优策略对应的状态值是最优状态值
- 作用：明确强化学习的最优策略目标，为Bellman Optimality Equation的建立提供基础
- 定义式 (.ipynb)


## Optimal State Value 最优状态价值
- 引入：不同策略在同一状态下可能产生不同的 State Value，因此引入最优状态价值，描述该状态下能够获得的最大期望长期回报
- 定义：最优状态价值是所有可能策略在状态 s 下所能获得的最大 State Value，即最优策略对应的状态价值
- 作用：描述每个状态能够达到的最大期望长期回报，为求解最优策略提供依据
- 定义式 (.ipynb)


## Bellman Optimality Equation 贝尔曼最优方程
- 引入：来求解最优状态价值和最优策略
- 定义：贝尔曼最优方程描述最优状态价值与即时奖励及下一状态最优价值之间的递归关系
- 作用：用于刻画和求解最优状态价值与最优策略，为后续 Value Iteration、Policy Iteration 等算法提供数学基础
- 公式展开形式，Q Value形式 (.ipynb)


## Greedy Policy 贪心策略
- 引入：Bellman Optimality Equation需要在所有策略中寻找最大价值，而贪婪策略通过选择 Q Value 最大的动作，实现当前状态下的价值最大化
- 定义：贪婪策略是指在给定状态下，选择当前动作价值函数 q(s,a) 最大的动作所对应的策略
- 作用：将 BOE 中对策略的最大化转化为对动作价值的最大化，为最优策略的求解提供依据
- 公式 (.ipynb)


## 矩阵-向量形式
- 引入：每个 State 都有一个 Bellman Optimality Equation，将所有状态的方程组合起来，引出矩阵向量形式
- 定义：贝尔曼最优方程的矩阵向量形式是利用状态价值向量、期望奖励向量和状态转移矩阵，统一表示所有状态的最优价值递归关系
- 作用：将最优价值求解问题表示为向量方程，为后续的不动点分析、压缩映射和 Value Iteration 提供数学基础
- 公式（.ipynb）


## Contraction Mapping Theorem 压缩映射定理
1. Fixed Point 不动点
- 引入：Bellman Optimality Equation 可以写成 v=f(v)，因此可以将求解最优状态价值的问题转化为寻找函数的不动点
- 定义：如果一个点经过函数 f 映射后仍然等于自身，则称该点为函数 f 的不动点
- 作用：将贝尔曼最优方程的求解转化为不动点求解问题
- 公式（.ipynb）


2. Contraction Mapping 压缩映射
- 引入：为了判断反复应用函数 f 能否收敛到不动点，需要研究函数映射前后两点之间的距离变化
- 定义：如果存在常数 0<γ<1，使任意两点经过函数映射后的距离不超过原距离的 γ 倍，则称函数 f 为压缩映射
- 作用：保证任意两点经过反复映射后，其距离不断缩小，为证明迭代收敛提供条件
- 公式 (.ipynb)

3. Contraction Mapping Theorem 压缩映射定理
- 引入：如果函数 f 具有压缩性质，就可以利用压缩映射定理分析其不动点及迭代过程。
- 定义：对于实向量空间上的压缩映射 f，存在唯一的不动点 x∗，且从任意初始值 x0 出发，反复应用 f 都会收敛到该不动点。
- 作用：从数学上保证不动点的存在性、唯一性和迭代收敛性，为后续求解 Bellman Optimality Equation 提供理论依据。
- 公式 (.ipynb)


## Iterative Solution of BOE 贝尔曼最优方程的迭代求解
- 引入：Bellman Optimality Equation 可以写成 v=f(v)，由于 f(v) 具有压缩性质，因此可以通过反复迭代求得其唯一不动点v∗
- 定义：从任意初始状态价值向量 v0出发，反复应用 Bellman 最优算子更新价值向量，直至收敛到最优状态价值 v∗；随后根据 v∗选择最大动作价值对应的动作，得到最优策略 π∗
- 作用：将 Bellman Optimality Equation 转化为可执行的迭代算法，为下一章的 Value Iteration（价值迭代） 奠定基础。
- 公式（.ipynb）

# 第 4 课 - Value Iteration & Policy Iteration

## Value Iteration Algorithm


# 第 5 课 - Monte Carlo Learning 蒙特卡洛方法

## Monte Carlo Estimation 

- 补充: 大数定理 Law of Large Numbers


## MC Basic


## MC Exploring Starts


## MC ε-Greedy

- Soft policy

# 第 6 课 - Stochastic Approximation and Stochastic Gradient Descent 

## Stochastic Approximation 随机近似
- 当目标函数/期望无法精确获得时，用带噪声的采样结果反复迭代，逐渐逼近真实解

## Robbins–Monro (RM)
- 我不知道真实 g(w)，只能得到一个 noisy observation，但我还是可以不断修正 w，最终逼近根 w*

## Stochastic Gradient Descent 随机梯度下降
- GD、BGD、SGD




