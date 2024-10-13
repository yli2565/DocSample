---
layout: default
title: "Code"
nav_order: 10
has_toc: false
---

# Repositories

{:.info}
This page gives a one sentence description of active repositories

- [AbstractSim](./AbstractSim/AbstractSim.html) AbstractSim is a **low-fidelity**, **fast**, 2D simulator for training customized policies. 
- [BHumanCodeRelease](https://github.com/bhuman/BHumanCodeRelease) A **robot control** + **game simulation** codebase for RobotCupSPL.
  - [SimRobot](./BHumanCodeRelease/SimRobot%20Overview/SimRobot%20Overview.html) is a **high-fidelity**, **slow**, 3D simulator for RobotCup Game integrated in BHumanCodeRelease.
  - [Nao](./BHumanCodeRelease/Nao%20Overview/Nao%20OverView.html) is the control code for Nao Robots. 
- [BadgerRLSystem](./BadgerRLSystem/BadgerRLSystem.html) BadgerRLSystem is forked from BHumanCodeRelease, with modification to enable RL policy **training** and **deploy** on physical NAO Robots.
  - SimRobot in BadgerRLSystem is a modified version for RL training.
