---
title: 2024-11-12 WISC Meeting
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

## Yuhao
  - Fix performance problem in PYLogReader
  - Write the doc for PYLogReader
  - Has collected and parsed data 
  - Currently experiencing issues with imitation learning training environment
  - Algorithm crashes periodically during execution

## Edison
* Edison's brief update:
  - Working with Abhinav on testing AbstractSim
  - Reading and understanding the codebase in his own time
  - Focused on code comprehension
* Limited progress this week

## Abhinav
* Project status:
  - Coordinating with Zhihan about V2 transfer
  - Planning to train policy in V2's new branch
  - Will test deployment on SimRobot
* Performance metrics:
  - CHTC: 1500-2000 FPS
  - Adam Desktop: also 1500 FPS
  - CHTC slower due to single core training limitations ?
* Current status: Policy training ongoing

## Zisen
* Multiple workstreams:
  1. PyLogReader:
     - Yuhao has completed debugging
     - Not tested yet by Zisen
  2. Research:
     - Reading imitation learning literature
  3. Referee Gesture Recognition:
     - 99% accuracy on training and validation
     - Model inference time: 0.2 seconds 
       - Adam ask if Zisen use the network of BHuman and make a reminder that the network need to be small enough to be run on Nao
     - Considering architecture options:
       * Build CNN from scratch
       * Use transfer learning with ImageNet
* Competition Rules Discussion:
  - Referee uses whistle signal
  - Robot moves to field center
  - 12 different gestures to recognize
  - Robot outputs sound for recognized gesture

## Dmitry, Abhinav & Edison
* Setup Issues & Solutions:
  1. AbstractSim V2 Problems:
     - CV2 import errors
     - Missing libGL package
  2. Solutions provided:
     - Comment out CV2 import line
     - Install libGL package on WSL
     - Use conda.yaml file
* Environment Setup:
  - Edison confirms conda environment works on Mac with modifications
  - Abhinav recommends using provided conda environment to avoid issues

## Adam
* Mujoco Project Status:
  - No significant progress
  - Pending RL environment integration
* Bottlenecks:
  - Time constraints ?
* Open invitation for collaboration
