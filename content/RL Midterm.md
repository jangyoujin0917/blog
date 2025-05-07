### 1. Markov Decision Process (MDP)
#### Markov Property
- State is **Markov** if
$$
\mathbb{P}[S_{t+1}|S_{t}] = \mathbb{P}[S_{t+1}|S_{1},\cdots,S_{t}]
$$
- Markov ⇔ Fully observable ($O_{t}=S_{t}^{a}=S_{t}^{e}$)
- If partially observable, agent must construct own $S_{t}^{a}$
#### Markov Process
- $\langle \mathcal{S}, \mathcal{P} \rangle$ : state, transition probability
#### Markov Reward Process (MRP)
- $\langle \mathcal{S}, \mathcal{P}, \mathcal{R}, \gamma \rangle$ : reward function, discount factor
- Return $G_{t}=R_{t+1}+\gamma R_{t+2}+\gamma R_{t+3}+\cdots$
- Value function $v(s) = \mathbb{E}[G_{t}|S_{t}=s]$
	- $v(s)=R_{s}+\gamma\sum\limits_{s'}\mathcal{P}_{ss'}v(s')$
	- $\mathbf{v}=\mathbf{R}+\gamma\mathcal{P}\mathbf{v}$
#### Markov Decision Process (MDP)
- $\langle \mathcal{S}, \mathcal{A}, \mathcal{P}, \mathcal{R}, \gamma \rangle$ : finite set of action
- Policy $\pi(a|s)=\mathbb{P}[A_{t}=a|S_{t}=s]$
- Value function
	- State value function $v_{\pi}(s)=\mathbb{E}[G_{t}|S_{t}=s]$
	- Action value function $q_{\pi}(s,a)=\mathbb{E}[G_{t}|S_{t}=s, A_{t}=a]$
- Bellman Expectation Equation
> $v_{\pi}(s)=\sum\limits_{a\in\mathcal{A}}\pi(a|s)q_{\pi}(s,a)$
> $q_{\pi}(s,a)=R_{s}^{a}+\gamma\sum\limits_{s'\in\mathcal{S}}\mathcal{P}_{ss'}^{a}v_{\pi}(s')$
> $v_{\pi}(s)=\sum\limits_{a\in\mathcal{A}}\pi(a|s)\left(R_{s}^{a}+\gamma\sum\limits_{s'\in\mathcal{S}}\mathcal{P}_{ss'}^{a}v_{\pi}(s')\right)$
> $q_{\pi}(s,a)=R_{s}^{a}+\gamma\sum\limits_{s'\in\mathcal{S}}\mathcal{P}_{ss'}^{a}\sum\limits_{a'\in\mathcal{A}}\pi(a'|s')q_{\pi}(s', a')$
- Optimal Value Function
	- $v_{\ast}(s)=\max\limits_{\pi}v_{\pi}(s)$
	- $q_{\ast}(s, a)=\max\limits_{\pi}q_{\pi}(s, a)$
- Bellman Optimality Equation
> $v_{\ast}(s)=\max\limits_{a}q_{\ast}(s, a)$
> $q_{\ast}(s,a)=R_{s}^{a}+\gamma\sum\limits_{s'\in\mathcal{S}}\mathcal{P}_{ss'}^{a}v_{\ast}(s')$
> $v_{\ast}(s)=\max\limits_{a}\left(R_{s}^{a}+\gamma\sum\limits_{s'\in\mathcal{S}}\mathcal{P}_{ss'}^{a}v_{\ast}(s')\right)$
> $q_{\ast}(s,a)=R_{s}^{a}+\gamma\sum\limits_{s'\in\mathcal{S}}\mathcal{P}_{ss'}^{a}\max\limits_{a'}q_{\ast}(s',a')$

### 2. Dynamic Programming (DP)
- To solve known MDP
#### Iterative Policy Evaluation (Prediction)
- *Synchronous* backup
$$
v_{k+1}(s)\leftarrow\sum\limits_{a\in\mathcal{A}}\pi(a|s)\left(R_{s}^{a}+\gamma\sum\limits_{s'\in\mathcal{S}}\mathcal{P}_{ss'}^{a}v_{k}(s')\right)
$$
#### Policy iteration (Control)
1. Evaluate policy $\pi$ → $v_{\pi}(s)$
2. Policy improvement $\pi'=\mathrm{greedy}(v_{\pi})$
- Always converges to $v_{\pi}$
#### Value iteration (Control)
- *Synchronous* backup
$$
v_{k+1}(s)\leftarrow\max\limits_{a\in\mathcal{A}}\left(R_{s}^{a}+\gamma\sum\limits_{s'\in\mathcal{S}}\mathcal{P}_{ss'}^{a}v_{k}(s')\right)
$$
$$
\mathbf{v}_{k+1}=\max\limits_{a\in\mathcal{A}}\mathbf{R}^{a}+\gamma\mathcal{P}^{a}\mathbf{v}_{k}
$$
#### Asynchronous DP
1. In-place
$$v(s)\leftarrow\max\limits_{a\in\mathcal{A}}\left(R_{s}^{a}+\gamma\sum\limits_{s'\in\mathcal{S}}\mathcal{P}_{ss'}^{a}v(s')\right)$$
2. Prioritized Sweeping (largest Bellman error first)
$$
\left|\max\limits_{a\in\mathcal{A}}\left(R_{s}^{a}+\gamma\sum\limits_{s'\in\mathcal{S}}\mathcal{P}_{ss'}^{a}v(s')\right)-v(s)\right|
$$
3. Real-Time (Agent's Experience) : $v(S_{t})$
#### Extensions
- DP is full-width backup ↔ Sample backup(MC, TD)
- Approximate DP : $\hat{v}(s, \mathbf{w})$

### 3. Model-Free Prediction
- Prediction for **unknown** MDP
#### Monte-Carlo(MC)
- complete episode
- $v_{\pi}(s)=\mathbb{E}_{\pi}[G_{t}|S_{t}=s]\approx\sum\limits_{n=1}^{N}G_{t}^{(n)}|_{S_{t}=s}$
- First visit vs. Every visit
- Incremental mean
	- $\mu_{k}=\mu_{k-1}+\frac{1}{k}(x_{k}-\mu_{k-1})$
	- $V(S_{t})\leftarrow V(S_{t})+\frac{1}{N(S_{t})}(G_{t}-V(S_{t}))$
	- $\frac{1}{N(S_{t})}$ can be $\alpha$ for non-stationary problem
#### Temporal Difference(TD)
- incomplete episode, bootstrapping
- TD can learn without final outcome
- TD exploits Markov property
- TD is biased / lower variance (Bias-Variance tradeoff)
- $V(S_{t})\leftarrow V(S_{t})+\alpha(G_{t}-V(S_{t}))$
	- TD target : $G_{t}\approx R_{t+1}+\gamma V(S_{t+1})$
	- TD error : $R_{t+1}+\gamma V(S_{t+1}) - V(S_{t})$
- n-step TD
	- n=1 (TD) ↔ … ↔ n=$\infty$ (MC)
### 4. Model-Free Control
- Control for **unknown** MDP
#### Monte-Carlo Policy Iteration
1. Policy evaluation (MC) : $q_{\pi}(s,a)$
	- For greedy policy $\pi'(s)=\arg\max\limits_{a\in\mathcal{A}}q_{\pi}(s,a)$
2. Policy improvement : $\epsilon$-greedy (for exploration)
#### SARSA
- on-policy algorithm
- $Q(S,A)\leftarrow Q(S,A)+\alpha[R+\gamma Q(S', A')-Q(S, A)]$
- action $A$ is chosen from $Q$ (e.g. $\epsilon$-greedy)
- SARSA converge if
	- GLIE of $\pi(a|s)$ : $\epsilon \to 0$ while exploring
	- Robbins-Monro sequence $\sum a_{t}=\infty$, $\sum a_{t}^{2}<\infty$
- n-step SARSA : $q_{t}^{(n)}=R_{t+1}+\cdots+\gamma^{n-1}R_{t+n}+\gamma^{n}Q(S_{t+n})$
#### Importance Sampling
$$
\mathbb{E}_{X \sim P}[f(X)]=\mathbb{E}_{X \sim Q}\left[\frac{P(X)}{Q(X)}f(X)\right]
$$
- MC
$$
G_{t}^{\pi/\mu}=\frac{\pi(A_{t}|S_{t})}{\mu(A_{t}|S_{t})}\cdots\frac{\pi(A_{T}|S_{T})}{\mu(A_{T}|S_{T})}G_{t}
$$
$$
V(S_{t})\leftarrow V(S_{t})+\alpha\left(G_{t}^{\pi/\mu}-V(S_{t})\right)
$$
- TD
$$
V(S_{t})\leftarrow V(S_{t})+\alpha\left(\frac{\pi(A_{t}|S_{t})}{\mu(A_{t}|S_{t})}(R_{t+1}+\gamma V(S_{t+1}))-V(S_{t})\right)
$$
#### Q-learning
- off-policy, no importance sampling
$$
Q(S,A)\leftarrow Q(S,A)+\alpha[R+\gamma\max\limits_{A'} Q(S', A')-Q(S, A)]
$$
### 5. Function Approximation
$\hat{v}(s, \mathbf{w})\approx v_{\pi}(s)$ / $\hat{q}(s, a, \mathbf{w}) \approx q_{\pi}(s,a)$
#### Incremental Methods
##### Prediction
- Value Function Approximation
	- $J(\mathbf{w})=\mathbb{E}_{\pi}[(v_{\pi}(s)-\hat{v}(s, \mathbf{w}))^{2}]$
	- $\Delta\mathbf{w}=-\frac{1}{2}\alpha\nabla_{\mathbf{w}}J(\mathbf{w})=\alpha\mathbb{E}_{\pi}[(v_{\pi}(s)-\hat{v}(s, \mathbf{w}))\nabla_\mathbf{w}\hat{v}(s, \mathbf{w})]$
	- MC method : $v_{\pi}(s)\approx G_{t}$
	- TD method : $v_{\pi}(s)\approx R_{t+1}+\gamma \hat{v}(S_{t+1}, \mathbf{w})$

| Convergence | Lookup Table | Linear                | Non-linear |
| ----------- | ------------ | --------------------- | ---------- |
| MC          | O            | O                     | O          |
| TD          | O            | O(only for on-policy) | X          |
| Gradient TD | O            | O                     | O          |
| LSMC        | O            | O                     | -          |
| LSTD        | O            | O                     | -          |
#### Control
| Convergence         | Lookup Table | Linear          | Non-linear |
| ------------------- | ------------ | --------------- | ---------- |
| MC Control          | O            | O(near-optimal) | X          |
| SARSA               | O            | O(near-optimal) | X          |
| Q-learning          | O            | X               | X          |
| Gradient Q-learning | O            | O               | X          |
| LSPI (Batch)        | O            | O(near-optimal) | -          |
#### Batch Methods
- Iteration methods
	- SGD with Experience Replay
		- Sample $\mathcal{D}\sim\langle s, v^{\pi}\rangle$, update with $\Delta\mathbf{w}$
	- DQN with Experience Replay
		- Sample $\mathcal{D}\sim\langle s, a, r, s'\rangle$
		- $\mathcal{L}_{i}(w_{i})=\mathbb{E}\left[\left(r+\gamma\max\limits_{a'}Q(s', a', w_{i}^{-}-Q(s, a, w_{i})\right)^{2}\right]$
		- $w_{i}^{-}$ is old fixed parameter (stability for learning)
- without iteration
	- Linear approximation : $\hat{v}(s,\mathbf{w})=\mathbf{x}(s)^{T}\mathbf{w}$, Optimal when $\Delta\mathbf{w}=0$
	- LSMC : $v_{t}^{\pi}\approx G_{t}$
	- LSTD : $v_{t}^{\pi}\approx R_{t+1}+\gamma \hat{v}(S_{t+1}, \mathbf{w})$
### 6. Policy Gradient
- $p_{\theta}(\tau)=p_{\theta}(s_{1}, a_{1}, \cdots, s_{T}, a_{T})=p(s_{1})\prod_{t=1}^{T}\pi_{\theta}(a_{t}|s_{t})p(s_{t+1}|s_{t},a_{t})$
- $J(\theta)=\mathbb{E}_{\tau\sim p_{\theta}(\tau)}[r(\tau)] = \int p_{\theta}(\tau)r(\tau)d\tau$
- $\nabla_{\theta}J(\theta)=\int\nabla_{\theta}p_{\theta}(\tau)r(\tau)d\tau=\int p_{\theta}(\tau)\nabla_{\theta}\log p_{\theta}(\tau)r(\tau)d\tau=\mathbb{E}_{\tau\sim p_{\theta}(\tau)}[\nabla_{\theta}\log p_{\theta}(\tau)r(\tau)]$
#### REINFORCE
1. sample from $\pi_{\theta}(a_{t}|s_{t})$ → make history $\tau$
2. $\nabla_{\theta}J(\theta)=\mathbb{E}_{\tau\sim p_{\theta}(\tau)}[\nabla_{\theta}\log p_{\theta}(\tau)r(\tau)]\approx \sum_{i}(\sum_{t}\nabla_{\theta}\log \pi_{\theta}(a_{t}|s_{t}))(\sum_{t}r(s_{t},a_{t}))$
3. $\theta \leftarrow \theta + \alpha\nabla_{\theta}J(\theta)$