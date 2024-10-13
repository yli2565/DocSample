---
layout: default
title: "RoboCup 2025 Tasks List"
---

# RoboCup 2025 Tasks List

{:.hint}
This page gives a brief overview of the ongoing project and directions for RoboCup 2025.
<br>
For more information, please check the doc [**Toward RoboCup 2025**](https://docs.google.com/document/d/1a_Rvacxm9Vnnckz90d_8mO7Fn6WeP1KawXRMKFru5fg/edit) and [**Gitub project**](https://github.com/orgs/Badger-RL/projects/1).

# Current Ongoing Fall Goals:

- Multi-agent coordination
  - Passing
  - Multi-agent RL
    - Revisit MARL efforts with improved action space:
      - Collaborative learning with hand-coded opponents
      - Self-play
  - Role switching
    - need to supports 7 robots on the field
  - Set plays
    - Define a general representation for set plays
    - Learn parameters of set plays
  - Adversarial behaviors
    - Set picks on opponents (check this is allowed)
    - Block opponent vision
  - Action space reconsideration
    - Go from ball-centric to a generalized walkToPoint
    - Learn which action space to use
  - Fall Goals:
    - Generalizing the new action space: call x,y,angle
    - Revisiting approaches to self-play, learning with hand-coded adversaries
    - Learned high-level role-playing
- SimRobot Training
  - Sometimes during training, the process crashes or fails to start the next episode.
  - It's a pain to run long-running training on your personal laptop. It would be better to kick off training on a remote machine.
  - Also could be good to training on multiple machines in a cluster
  - Fall Goals:
    - Adding robustness to the training pipeline (can’t run for many hours)
    - Cluster-based training
- More realistic AbstractSim
  - It could be similar to DeepMind’s abstract Mujoco soccer sim.
  - Fall Goals:
    - Reproduce v1 policies in v2
    - Some updates to align with the real robot deployment
    - Loading pre-trained policies
- B-Human Imitation Learning
  - Can we learn a neural network version of B-Human’s behavior?
  - Can we learn a goal probability estimator for B-Human’s behavior? I.e., predict the probability of a goal being scored from anywhere on the field. This could then be used as a shaping reward or a heuristic for planning.
  - Fall Goal:
    - Overlaps with SimRobot training: need to add robustness to the environment
    - Aim to clone goalline and goalie behavior
    - Goal is to be able to toggle between our behavior and B-Human behavior.
- Vision
  - Need to detect and respond to referee hand gestures
  - Fall Goal:
    - Robots recognize and respond to visual referee gestures
    - Data-free approach(it is hard to get dataset) vs. Supervised learning approach(find a way to get dataset)
- Smoothing rough edges (Shielding + patching)
  - Policy patching
    - Fix the behavior of a policy in a narrow region of the state space while preserving its behavior outside of that region.
    - In our case, we have a region of the state space that we can define with conditional logic and within that region, we can programmatically say what the right action is for any state.
  - Reduce penalties
    - Someone could look into a more principled shielding approach. The challenges of RoboCup could lead to a nice paper here.
- Goalie behavior (learning based approach)
  - Learning the goalie behavior, particularly when the ball is close.
    - Need to identify when the “stay in the position that maximizes goal coverage” strategy is not the best thing to do.
  - Some room for improvement:
    - when to clear the ball
    - when clearing, where to clear the ball; don't want to kick it toward the opponent
    - how to coordinate with our own defender
- Motion Control
  - Sim2real walk and kick learning
  - On-robot walk / kick improvement (e.g., through blackbox optimization)

---

# Potential Future Projects

- Localization
  - Predict the behavior of other robots when you don’t see them
    - Unclear what our belief is about where other robots are when we stop receiving observations of them.
    - Can we improve our prediction about where an adversary is likely to move to?
    - Model uncertainty in their position increasing the longer they’re not observed
  - Localization from off-field landmarks
- Real-time planning architectures
  - Currently, we have based our behavior on model-free learning which requires a ton of computation ahead of games and is hard to change at competitions but it is then fast to get an action during games. Real-time planning approaches (e.g., Monte Carlo tree-search, model-predictive control) doesn’t require pre-computation of the right action at any state, might be easier to change at the competition, and might better handle compound tasks. The downside is more computation is required at decision-time. RoboCup is an excellent domain for studying how to balance real-time planning and model-free reactive control.
