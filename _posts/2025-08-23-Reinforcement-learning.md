---
layout : post
date : 2025-08-23
title : Post training methods in LLM using RL 
---

Tags : Reinforcement Learning, RL , Machine learning , deep learning , ML , DL  

[PPO](https://www.youtube.com/watch?v=TjHH_--7l8g)

### Maths 
Reinforcement learning, here the agent takes / decides some action to take based on the current state and other variables present at timestep t, and then its takes that action and a reward is followed and weights are updated based on the rewards received by model 

Consider this basic `hello world` example of RL 

State : Any place / position where the agent can be

Action : Up , down , left , right these are the action the agent can take 

Values : The best place we can go from the current state that maximises the return is called Values, we need to find the value function, like there its (Cell Value = Nearby best Value - 1)

<img width="1151" height="770" alt="image" src="https://github.com/user-attachments/assets/05d333ee-ce5d-4944-b1fc-e3d7be8328a2" />

Policy : Given the current state and the neighbouring values , we can create a policy function , a good policy function is `max(up, down, left, right)` and whichever number gives you the best answer that leads to this policy. 

<img width="1658" height="915" alt="image" src="https://github.com/user-attachments/assets/61f413f7-c575-4475-a982-1601829674bf" />

So this is the policy , followung these arrows we can reach the best / optimal position 

So we need a Value function and a Policy function to navigate the landscape and solve the RL problem successfully. 

#### But the catch is with increasing no. of states , finding the Policy and value function is very difficult 

So we use Neural Nets for approximating both the policy and value models 

### VALUE NEURAL NETWORK  

> Value model is deterministic and PNN is approximated  
> The goal is to find the best direction / way to reach to next state given the current state   

<img width="1833" height="804" alt="image" src="https://github.com/user-attachments/assets/e07862e3-c969-4e5b-bb0e-601e1c5196d5" />

Training the Value Neural nets: 
`L_value ( theta ) = (model_pnn - actual_value )^2`

<img width="1780" height="889" alt="image" src="https://github.com/user-attachments/assets/3ef46ff4-66e0-4336-8003-495356dbeddf" />

### POLICY NEURAL NETWORK 

Policy model tells model where to take the next step to go from the current state and increases the probability in the current direction 

<img width="1275" height="800" alt="image" src="https://github.com/user-attachments/assets/d3d59a62-564e-4978-bb96-a77e379ca2a0" />

Training a policy neural net, we are taking scenarios and seeing the gain if the Value network predicted that in the right direction the gain value is 10, means the actual Value is more compared to the predicted value then its means the Value model should increase the value there and the policy model should increase the probabily of going in that direction 

<img width="4993" height="2253" alt="image" src="https://github.com/user-attachments/assets/92b993cb-c896-42f3-b6c3-7c98a6561b21" />

`Loss_policy_theta = (PNN_t(a|s) / PNN_t-1(a|s)) * momentum in that direction`




## SFT 
Supervised finetuning, (SFT)
We have the supervised dataset, that is , the training dataset contains both input and defined output to train the model on and the model learns based on the samples provided like classic supervised training     

```
Dataset: 
Input Examples
Output Examples
```

### PPO 
Value and policy model both get rained at the same time



### GRPO 


