**Information Gain (IG)** is a measure from information theory that quantifies how much uncertainty (entropy) is reduced when new evidence or data is observed. In simpler terms, it tells us how much “new, useful information” a sensor provides about the true state of the world.

Mathematically, it’s the difference between the prior uncertainty and the posterior uncertainty after receiving sensor data:  IG = H(prior) − H(posterior) where, H is the entropy (uncertainty) of a probability distribution.

In this demo, the system has two sensors: Radar and LiDAR.
The prior represents equal belief (0.5, 0.5) i.e. both sensors are assumed equally informative before we observe any new data.
The evidence (0.6, 0.4) means that, after looking at the actual data, the model believes Radar contributes 60% of the information and LiDAR 40%.
The function then calculates how much the overall uncertainty decreased after observing this evidence.

So, the printed value 'Information Gain from Sensor Update: 0.029 bits' means that adding new data from sensors reduced the system’s uncertainty by 0.029 bits.
In essence, Radar provided slightly more information than LiDAR in this demo.

Usually in Aerospace Tracking System:
Radar provides coarse but long-range detection.
LiDAR provides precise short-range spatial details.

The information gain tells the system which sensor is currently more informative or worth re-tasking i.e., which sensor should be prioritized for the next measurement or tracking update.

**Information Gain**: Reduction in uncertainty after receiving new data. In this demo, IG quantifies how much new info radar vs. LiDAR provides.
**<br>Higher IG**: The sensor provides more valuable or novel information.
**<br>Purpose**: Helps the AI agent dynamically decide which sensor to use or trust more

This demo, does not dynamically computes information gain for both sensors at every time step but does a static one time change. This demo can be enhanced to plot how each sensor’s contribution evolves over time if we have data (CSV File) for each sensor.
