# POLICY ITERATION ALGORITHM

## AIM
The aim of this experiment is to implement the Policy Iteration Algorithm in Reinforcement Learning to determine the optimal policy and corresponding value function for a given environment. Policy Iteration combines iterative policy evaluation and policy improvement steps to achieve convergence towards an optimal policy.

## PROBLEM STATEMENT
In Reinforcement Learning, the agent interacts with an environment modeled as a Markov Decision Process (MDP).
The challenge is to find an optimal policy that maximizes the long-term cumulative reward.
Policy Iteration addresses this by:

Evaluating the value of a given policy (Policy Evaluation).
Improving the policy based on the evaluated value function (Policy Improvement).
Repeating these steps until the policy converges to the optimal policy.

## POLICY ITERATION ALGORITHM
# STEP 1:
Initialization

Initialize an arbitrary policy π and value function V(s).
A
# STEP 2:
Policy Evaluation

For the current policy π, compute the value function V(s) for all states until convergence.

# STEP 3:
Policy Improvement

Update the policy by choosing actions that maximize the expected return using the current value function.
# STEP 4:
Check for Convergence

If the policy does not change (π′ = π), then the policy is optimal and the algorithm terminates.
Otherwise, repeat steps 2 and 3.

## POLICY IMPROVEMENT FUNCTION
### Name: Karthikeyan R
### Register Number: 212222240045
```
def policy_improvement(V, P, gamma=1.0):
    Q = np.zeros((len(P), len(P[0])), dtype=np.float64)

    for s in range(len(P)):
        for a in range(len(P[s])):
            for prob, next_state, reward, done in P[s][a]:
                Q[s][a] += prob * (reward + gamma * V[next_state] * (not done))

    new_pi = lambda s: {s: a for s, a in enumerate(np.argmax(Q, axis=1))}[s]

    return new_pi

```
## POLICY ITERATION FUNCTION
### Name: Karthikeyan R
### Register Number: 212222240045
```
def policy_iteration(P,gamma=1.0,theta=1e-10):
  random_actions=np.random.choice(tuple(P[0].keys()),len(P))
  pi=lambda s: {s:a for s, a in enumerate(random_actions)}[s]
  while True:
    old_pi={s: pi(s) for s in range(len(P))}
    V=policy_evaluation(pi,P,gamma,theta)
    pi=policy_improvement(V,P,gamma)
    if old_pi=={s:pi(s) for s in range(len(P))}:
      break
  return V,pi

```

## OUTPUT:
### 1. Policy, Value function and success rate for the Adversarial Policy
<img width="782" height="238" alt="image" src="https://github.com/user-attachments/assets/fd77d10b-f72c-45a5-85bf-470f9591e3d4" />

<img width="703" height="217" alt="image" src="https://github.com/user-attachments/assets/82e7a47b-84f5-41db-9f3b-8ef01d2cacdf" />



### 2. Policy, Value function and success rate for the Improved Policy

<img width="555" height="205" alt="image" src="https://github.com/user-attachments/assets/7495f75a-c688-49a3-ac89-c10a4da10618" />

<img width="632" height="187" alt="image" src="https://github.com/user-attachments/assets/4de76266-caa6-4adb-b222-57b0f6839a1a" />




### 3. Policy, Value function and success rate after policy iteration

<img width="551" height="193" alt="image" src="https://github.com/user-attachments/assets/ee3b8594-2006-4b5c-90b4-61b63c94391e" />

<img width="619" height="178" alt="image" src="https://github.com/user-attachments/assets/ddeb7bca-ff24-4dc8-9daf-45687925ff2d" />






## RESULT:
Therefore, policy iteration algorithm to find optimal policy by iteratively maximizing the value function is successfully implemented.
