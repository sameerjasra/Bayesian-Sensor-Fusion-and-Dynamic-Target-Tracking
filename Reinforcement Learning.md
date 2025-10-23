**Reinforcement Learning (RL)** is used in a conceptual and illustrative way rather than to directly control the sensor fusion pipeline in this demo. But it demonstares the future possible extension that dynamically calculates real rewards based on actual MSE improvement or information gain from each sensor. 
This demo is based on random rewards.

<br>**The Purpose of Reinforcement Learning in this Demo**

<br>The RL component models a simple decision-making agent that learns which sensor to prioritize or re-task (Radar vs. LiDAR) based on reward feedback. It’s a simplified abstraction of how an intelligent system might dynamically manage sensor usage to optimize information gain, energy, or tracking accuracy in real time.

<br> From the code:
<br>Actions (n_actions=2) → represent choosing Radar (action 0) or LiDAR (action 1).
<br>Rewards → synthetic feedback simulating how informative or accurate each sensor was in the last step.
<br>Q-values → represent the agent’s learned preference for each sensor, based on long-term average reward.

<br>So, over time, the agent learns which sensor tends to yield better tracking accuracy or information gain.

<br>In a real Aerospace application:
<br>Sensors have different strengths and limitations (range, weather robustness, energy cost).
<br>All of them can't be used all the time as that’s expensive and redundant.
<br>RL allows the system to autonomously decide which sensor (or combination) to use in each situation.

<br>Thus, this demo shows a foundation for adaptive sensor management, also called **dynamic retasking or sensor scheduling**.
