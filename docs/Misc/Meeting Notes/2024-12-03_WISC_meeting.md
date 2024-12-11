---
title: 2024-12-03 WISC Meeting
layout: default
parent: Meeting Notes
---

<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Initial Discussion - Josiah
- Discussed merging diverged simulator versions
- Need to check status with team members
- Goal: merge versions to establish main v2 simulator

## Motion Control Work - Josiah & Adam
### Mujoco Implementation
- Adam working on Mujoco motion control
- Options for BHuman motion control:
  - Behavior cloning approach
  - Direct code implementation
- Considering Isaac Gym with PPO/SAC training

### Walk Engine Integration
- Discussed porting BHuman walk to Mujoco
- Proposal: implement as standalone binary with velocity commands
- Challenges:
  - Walk cloning complexity
  - Managing internal state variables
- Possible solution: recurrent neural network approach
- Critical timing: Changes needed by February/March

## Self-Play Implementation - Josiah & Will
- Will exploring RLlib for self-play
- Implementation challenges:
  - Example not working out of box
  - Performance issues with multiple policies
- Discussing stable baselines integration

## Multi-Agent Implementation - Yuhao
- Provided insights on multi-agent approaches
- Suggested reviewing Tianshou's implementation

## AbstractSim V2 Status - Josiah & Abhinav
- Fixed push ball to goal policy issues
- Need to verify transfer performance
- Working on main V2 branch development

## Implementation Progress - Josiah & Edison
- Edison working with latest commit
- Current challenges:
  - Dimension mismatch errors
  - Policy integration issues

## Vision Recognition - Zisen & Josiah
### Data Collection
- ETH team cannot share data (privacy concerns)
- Exploring alternatives:
  - Unreal Engine
  - SimRobot for data collection

### Implementation Priority
- Focus on NAO robot deployment
- Direct hardware implementation preferred over simulation
- Network architecture appears suitable based on literature

## Goalkeeper Development - Josiah & Parv
- Parv working on goalkeeper implementation
- Recommendations:
  - Use existing stable baselines
  - Avoid new RL algorithm implementation
- Arranged mentoring with Abhinav for V2 setup

## Meeting Wrap-up - Josiah
### Timeline
- Approaching semester end
- RoboCup application due after winter break

### Spring Semester Focus
- Emphasis on practical implementations
- Key areas:
  - Multi-agent aspects
  - V2 migration
  - Practical applicability of research