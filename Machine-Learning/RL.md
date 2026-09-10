- 日期: 2026.9.1
# Reinforcement Learning 强化学习
- Definition: Reinforcement learning is a machine learning paradigm in which an agent learns how to make decisions by interacting with an environment and receiving rewards, with the goal of maximizing the expected cumulative reward over time.
- 定义: 强化学习（Reinforcement Learning）是一种机器学习范式，其中智能体（Agent）通过与环境（Environment）不断交互并获得奖励（Reward），学习如何采取动作（Action），其目标是最大化长期累积奖励的期望
  
Observation -> Actor/Policy -> Action -> Environment -> Reward + Next Observation + Done -> Next Actor

## 强化学习基本元素
Agent、Environment、Observation、Action、Reward、Episode、Policy、Return

1. Agent 智能体: A1机器狗及控制A1行动的决策系统
 - 项目: Agent 是使用Actor策略网络, 根据A1的Observation输出12维Action, 并在训练阶段由PPO不断优化的决策系统

2. Environment 环境: 智能体进行交互的外部系统
 - 项目: Environment 是Isaac Gym中包含A1机器人、地形、重力、摩擦、碰撞和任务规则的仿真世界

3. Observation 观测: 智能体在当前时刻能够获得的、用于决策的环境信息
 - 项目: Observation 是legged_gym从Issac Gym读取A1的物理数据, 经过处理和拼接后, 送入Actor的一维数据向量
 - 区分: Observation 和 State, 前者是允许Agent看到的部分状态, 后者是环境真实的完整状态
 - 概括: Observation 是A1在当前时刻交给Actor的“身体信息和任务信息”

4. Action 动作: Agent根据当前Observation, 选择并输出给Environment的决策结果
 - 项目: Action 是Actor根据A1当前观测输出的12维连续向量, 对应12个可控制关节

5. Reward 奖励: Environment在每一步交互后返回给Agent的一个数值, 用来评价刚才的行为好不好
 - 项目: Reward 是legged_gym根据A1执行动作后的运动效果, 计算出来的综合得分
 - 概括: Reward 是环境对A1刚才这一步动作给出的评分, 也是PPO判断策略应该怎样改进的核心信号

6. Episode 回合: Agent从一次初始状态开始, 与环境连续交互, 直到终止条件满足为止的一整段过程
 - 项目: Episode 是一只A1从被重置到初始姿态开始, 一直运动到摔倒、发生严重碰撞或达到时间上限的完整训练回合
 - 概括: Episode 是A1从一次重置开始, 到摔倒或超时结束的一整轮运动经历

7. Policy 策略: Agent根据当前Observation选择Action的规则
 - 项目: Policy是A1的控制策略, 它接收当前Observation, 并决定12个关节应该输出什么Action; 通常由Actor神经网络来实现
 - 概括: Policy是A1“看到当前身体状态后, 决定下一步怎样控制12个关节”的决策规则

8. Return 回报: 从当前时刻开始, 未来多个Reward按一定方式累积得到的总收益
 - 项目: Return 表示A1从当前时刻继续运动下去, 直到Episode结束, 预计能够获得的累计奖励
 - 概括: Return 是A1从当前时刻开始, 未来一连串Reward累积得到的长期成绩

## 如何评价一个状态和动作的长期好坏
Discount Factor, Value Function, Q Value, Advantage

1. Discount Factor 折扣因子: 计算Return时, 用来降低未来Reward权重的系数
 - 项目: 折扣因子决定A1在学习走路时, 是更重视当前一步的表现, 还是更重视未来一段时间的长期表现
 - 概括: 折扣因子决定A1在评价一个动作时, 对未来运动结果看得有多远、看得有多重

2. Value Function 价值函数: 估计智能体处于某个状态时, 未来能够获得多少Return的函数
 - 项目: 价值函数用来估计A1处于当前身体状态后, 继续运动下去预计能获得多少累计奖励
 - 概括: 价值函数是在评价“A1当前这个局面未来有多好”; Return是未来累计奖励的实际结果, Value是Critic对这个结果的提前预测
 - Actor负责输出动作, Critic负责输出Value; Actor决定A1下一步怎么动, Critic判断A1当前局面未来有多好

3. Q Value 动作价值: 估计智能体再某个状态下选择某个Action后, 未来能够获得多少Return
 - 项目: Q Value 用来评价A1在当前身体状态下, 执行某个12维Action之后, 后续整体表现会有多好
 - 概括: Q Value 是在评价“当前这个局面下, 这个动作到底值不值得做”
 - 区分: Value 是指当前状态整体多好, Q Value 是指当前状态下, 选择某个动作后有多好

4. Advantage 优势函数: 衡量在当前状态下, 某个Action相比平均水平好多少
 - 项目: Advantage 用来判断A1在当前身体状态下, 刚执行的12维Action是否比当前Policy通常会选择的动作更好
 - 概括: Advantage 是在评价“这个动作比正常水平好多少”
 - 区分: Value 评价当前局面, Q Value 评价当前局面下的某个动作, Advantage 评价这个动作比当前局面的平均水平好多少

 - 总结：Return 是未来总共能拿多少奖励; Value 是现在预计未来能拿多少奖励; Advantage 是这次动作比预计水平好多少


- 日期：2026.8.8

# RL算法结构
Actor, Critic, Actor-Critic

1. MLP 多层感知机：是一种由输入层、若干全连接隐藏层和输出层组成的前馈神经网络
 - 项目：Observation是一串数值, Actor可以使用MLP, 把48维Observation映射为控制12个关节所需的输出
 - 概括：MLP是Actor的计算主体, 负责把A1现在的状态一步步加工成动作
 - Linear Layer 全连接层/线性层：通过权重矩阵和偏置向量，对输入进行仿射变换
 - Activation Function 激活函数：施加在线性层输出上的非线性函数，使神经网络能够学习复杂的非线性映射
 - Forward Propagation 前向传播：输出数据按照网络结构，从输入层依次经过各隐藏层直到输出层，计算得到网络输出的过程
 - Weight / Bias 权重 / 偏置：权重决定不同输入信息对下一层神经元的影响程度; 偏置是在线性组合以后额外加入的可训练偏移量


2. Actor 行动者 / 策略网络： Actor-Critic架构中负责表示策略并根据当前状态或观测选择动作的部分
 - 项目：Actor接收A1的48维Observation，并产生12维关节Action 
 - Actor和Policy的关系：Policy是规则; Actor是用神经网络实现和学习这个规则的部分
 - Actor的输入是什么？ 是智能体当前用来做决策的信息，该项目是48维Observation
 - Actor的输出是什么？ 是用于决定智能体当前采取的Action


3. Critic 评论家：Actor-Critic架构中用于估计价值函数的部分，它评价智能体当前所处状态在当前策略下的长期价值
 - 项目：Critic根据A1当前Observation，估计从现在开始继续按照当前Policy运动，未来大约能够获得多少Return
 - Actor看到Observation是判断怎么做； Critic看到Observation是判断现在这个局面有多好
 - Critic的输入是什么？ 是48维的Observation，Actor和Critic可以看到同样的信息，但做的事情完全不同
 - Critic的输出是什么？ 是一个数值，从当前状态开始，按照当前Policy继续运行下去，未来能够获得的期望Return大约是多少

 - Actor和Critic的联系：Critic通过估计V（s）提供一个正常水平基准，帮助判断Actor刚才的动作比预期好还是差


4. Actor-Critic：Actor-Critic是一种同时学习参数化策略和价值函数的强化学习框架，其中Actor表示策略并负责选择动作，Critic估计价值函数并提供评价信号，用于直到Actor的策略优化
 - 概括：Actor负责选择动作，Critic负责评价当前状态和Actor的行为，Critic产生的价值信息帮助Actor改进策略
 - Actor-Critic是一种框架思想，PPO是一种具体的策略优化算法


# Actor怎么学习
Policy Gradient，Rollout，On-Policy，Gaussian Policy，Log Probability，GAE

1. Policy Gradient 策略梯度：直接通过梯度调整策略网络参数，使能够带来更高回报的Action出现概率增大，使表现较差的Action出现概率降低
 - 项目：根据A1执行Action后得到的Advantage，调整Actor网络参数，让好的Action以后更容易出现，让差的Action以后更不容易出现
 - 利用Advantage判断动作好坏，再通过梯度修改Actor参数，使Policy朝更好的方向变化
 

2. Rollout 轨迹采样：指智能体按照当前策略与环境连续交互若干时间步，并记录这一过程中状态/观测、动作、奖励等数据的过程及其所得数据序列
 - 概括：让当前的Policy真的去环境里跑一段时间，把交互数据收集下来
 - 项目：让大量A1并行运行若干step，收集一批运动交互数据


3. On-Policy 在策略：使用由当前待优化策略或与其紧密对应的行为策略采集的数据来更新该策略
 - 概括：用当前这套Policy采出来的数据，主要训练当前这套Policy
 - 谁采集的数据，主要拿来训练谁，PPO用这批数据更新，更新完后，再让新的Policy去环境采新的Rollout
 - 项目：当前Actor控制A1采集Rollout，PPO利用这些数据更新Actor，更新后再重新采集数据


4. Gaussian Policy 高斯策略：是一种用于连续动作空间的随机策略，通过高斯分布对动作的概率分布进行参数化
 - 概括：用高斯分布表示连续动作的策略，不是死死输出一个动作，而是在合理动作附近进行随机探索
 - u 均值表示动作分布的中心，可以理解为Actor当前最倾向的侗族
 - sigma 标准差表示允许动作在u范围随机波动多大

 - 在这种连续控制PPO中，Actor网络本身通常主要输出动作分布的均值u，再配合标准差sigma构造Gaussian Policy，最后采样得到真正的Action


5. Log Probability 对数概率：动作概率的对数
 - 选用对数概率的原因：数值稳定；数学优化更方便
 - 项目：A1 Actor根据Observation生成Gaussian Policy，采样得到12维关节Action，同时计算该Action对应的Log Probability，用于后续PPO比较新旧Policy变化


6. GAE 广义优势估计
 - 概括：GAE是PPO中计算Advantage的方法，它在“估计准确性”和“训练稳定性”之间做平衡

 - TD Error 时间差分误差：表示实际发生的结果，比Critic原本预测的结果好多少


# PPO (Proximal Policy Optimization, 近端策略优化)
 - 定义：是一种基于策略梯度的强化学习算法，通过限制每次策略更新的幅度，在提高策略性能的同时保持训练稳定性
 - 概括：是一套“怎么训练Actor和Critic”的具体强化学习算法，它让好的动作更容易出现、坏的动作更少出现，同时限制Policy每次不要改得太猛
 - 项目：PPO利用机器狗采集的Rollout数据训练Actor和Critic，让A1逐渐学会根据Observation输出更好的12维Action

PPO Ratio，PPO Clip，Actor Loss，Critic Loss，Entropy

 - Advantage 判断动作好不好; PPO Ratio 判断Policy改变了多少; Clip 限制过大的Policy更新

1. PPO Ratio 策略概率比
 - 定义：指对于同一个状态—动作样本，当前策略与采集该样本时的旧策略所赋予的动作概率（连续动作中更严格地说是概率密度）之比，用于衡量策略更新前后对该动作选择倾向的相对变化
 - 概括：比较新 Policy 和旧 Policy 对同一个 Action 的“态度”改变了多少
 - 项目：A1 用旧 Actor 采集完 Rollout 后，PPO 更新 Actor；PPO Ratio 用来比较更新后的 Actor 和采数据时的旧 Actor，对当时那个 12 维 Action 的选择倾向改变了多少


2. PPO Clip PPO裁断机制/裁剪机制
 - 定义：PPO Clip 是 PPO 中通过将策略概率比限制在旧策略附近的一个区间，并构造截断代理目标函数，以抑制策略单次更新幅度过大的机制
 - 概括：Ratio 负责告诉我们“新 Policy 比旧 Policy 改了多少”，Clip 负责告诉它：“可以改，但改太多就不给你继续奖励了。”
 - 项目：A1 用 Rollout 更新 Actor 时，PPO Clip 防止 Actor 一次更新过猛，避免刚学到的稳定步态因为 Policy 突然变化太大而被破坏


3. Actor Loss 策略损失
 - 定义：Actor Loss 是用于优化策略网络参数的损失函数，在 PPO 中通常由 Advantage、PPO Ratio 和 Clip 共同构成，使策略提高高优势动作的选择倾向、降低低优势动作的选择倾向，同时限制策略更新幅度
 - 概括：Actor Loss 就是把“这个 Action 好不好”和“Policy 已经改了多少”综合起来，最终告诉 Actor 参数应该怎么改
 - 项目：A1 采集完 Rollout 并计算出 Advantage 后，Actor Loss 利用这些数据更新 Actor，让机器狗以后更倾向产生表现好的 12 维 Action，同时避免策略一次变化太大


4. Critic Loss 价值函数损失
 - 定义：Critic Loss 是用于优化价值函数网络的损失函数，通过衡量 Critic 预测的状态价值与目标价值之间的误差，使 Critic 的价值估计逐渐接近实际的长期回报
 - 概括：Critic Loss 就是检查 Critic “估价估得准不准”，估错了就通过反向传播修正它
 - 项目：A1 的 Critic 根据当前 Observation 预测一个 Value，Critic Loss 将这个预测值与 Rollout 得到的价值目标比较，从而训练 Critic 更准确地评价机器狗当前状态


5. Entropy 熵/策略熵
 - 定义：Entropy 是衡量策略动作分布随机性或不确定性的指标，在强化学习中通常作为正则项加入优化目标，以鼓励策略保持一定的探索能力，防止策略过早变得过于确定
 - 概括：Entropy 就是衡量 Actor 还有多少“探索欲”；Entropy 高说明动作比较随机，Entropy 低说明 Actor 越来越确定自己该怎么做
 - 项目：A1 训练过程中，Entropy 防止 Gaussian Policy 太早把动作分布收得特别窄，让机器狗在训练早期仍能尝试不同的 12 维关节动作，从而有机会找到更好的运动方式




