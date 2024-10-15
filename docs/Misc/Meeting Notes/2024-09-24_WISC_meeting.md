---
title: 2024-09-24 WISC Meeting
layout: default
parent: Meeting Notes
---

- (Vision) Trying to replicate what BHuman has done for gesture recognition.
- (Imitation Learning) Logging BHuman attacker vs. goalie data for imitation learning on the goalie.
    - Think about what variables are useful for IL and should be logged.
    - BHuman uses different action spaces (walk to point, walk at velocity) for different scenarios so difficult to define what the IL policy should output.
    - Can try matching low-level states with our own predefined API.
- (SimRobot Training) Trying to wrap SimRobot scenes into PettingZoo environments.
    - Moving more C++ code into Python for easier development (?).
- (MARL) Generalizing the walk to pose action space is not straightforward; an unconstrained action space has the same struggles as the original walk at velocity setup—need a smarter way to design a constraint.
- Reproducing AbstractSim V1 policies in AbstractSim V2 to verify that its working properly.
- Working on getting the Nao model into Mujoco.
- Thinking about ways to ramp up new people—create a wiki on GitHub?