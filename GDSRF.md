A formula I found for a _very_ customizable system that distributes rewards. This formula can be updated in iterations:

![[Pasted image 20240818131916.png]]

Generalized Disinflationary Smart Reward Function (or GDSRF)

Variable meanings:

- R(t) — Rewards with respect to time
- t — Time
- M — Max rewards
- D — Distribution constant
- R(t’) — Rewards at last reward formula change
- t’ — Time at last reward formula change

The distribution constant is a constant that has a negative correlation with the distribution rate: the higher the constant, the slower reward distribution is, and vice versa. Technically, the distribution constant for the first iteration of the GDSRF is 1/9th of the amount of time needed to distribute 90% of the max rewards.

![[Pasted image 20240818131935.png]]

Distribution constants when M=10, R(t’)=0, and t’ = 0; Green: 1.5, Red: 4.7, Black: 12.3, Purple: 37

When this reward function is used in a system such as a staking or yield farming system, a simple function can be used to change the maximum rewards and distribution rate at any time. This can allow for a few neat things that are out of reach for a set-in-stone reward function.

Rewards can be extremely fine-tuned; if the distribution of rewards is not enough to satisfy the greater market or rewards are predicted to burn out too quickly, the distribution constant can always be changed at any time.

![[Pasted image 20240818131947.png]]

Red — Original Reward Distribution, Green — Increased Reward Distribution Rate, Black — Decreased Distribution Rate

The maximum amount of rewards can be changed as well. This allows for some more interesting, game-theory-esque reward systems. For example, a random token TKN could have a built-in transfer tax and a staking system using the GDSRF. The token’s tax mechanism could be programmed to transfer the tax to the staking system and automatically increase the max rewards of the GDSRF every time there is a tax event. This would result in a very game-like feature where the token has a token sink — the tax — and a token tap — the staking system. This could increase the incentive for a user to participate in a given staking system, as staking rewards will always increase as the token is used.

![[Pasted image 20240818132013.png]]