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

## State 状态
- State 状态: The status of the agent with respect to the environment.
- State space 状态空间: The set of all states S.

## Action 动作
- Action 动作: For each state, there are many possible actions.
- Action space of a state 动作空间: the set of all possible actions of a state.

## State transition 状态转移
- State transition 状态转移: When taking an action, the agent may move from one state to another.
- State transition describes the interaction with the environment.

- Tabular representation 表格表示: We can use a table to describe the state transition.(Can only represent deterministic cases.)

- State transition probability 状态转移概率: use probability to describe state transition!

## Policy 策略
- Policy tells the agent what actions to take in a state.

Policy representation
- Intuitive representation 直观表示: We use arrows to describe a policy.
- Mathematical representation 数学表示: using conditional probability

Two Policy
- Deterministic policy 确定性策略: For a given state s, the policy always selects the same action a.
- Stochastic policy 随机策略: For a given state s, the policy defines a probability distribution over possible actions.


- 日期: 2026.9.10

## Reward 奖励
- Reward 奖励: a real number we get after taking an action.
- A positive reward represents encouragement to take such actions.
- A negative reward represents punishment to take such actions.

## Trajectory and return 轨迹和回报
- Trajectory 轨迹: A trajectory is a state-action-reward chain.
- Return 回报: The return of this trajectory is the sum of all the rewards collected along the trajectory.

- Discount rate 折扣因子: 计算Return时, 用来降低未来Reward权重的系数
- 概括: 折扣因子决定A1在评价一个动作时, 对未来运动结果看得有多远、看得有多重

## Episode 回合
- Episode 回合: When interacting with the environment following a policy, the agent may stop at some terminal states. The resulting trajectory is called an episode. 

## Markov decision process (MDP) 马尔可夫决策过程
- MDP 定义: 智能体在一个环境中，根据当前状态选择动作，环境随后转移到新的状态并给予奖励，智能体不断重复这一过程，以最大化长期累计回报。
- Markov Property 马尔可夫性质: 在给定当前状态的条件下，未来与过去的完整历史无关。


# 第 2 课 - Bellman Equation 贝尔曼公式
- Return 非常重要, 可以用来评估策略; Calculating return is important to evaluate a policy.

