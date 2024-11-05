---
title: 2024-11-05 WISC Meeting
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
## Initial Setup & Opening
- Brief waiting period for participants to join

## Doc Page Discussion - Josiah & Yuhao
- Josiah requests web page link
- Yuhao confirms it's about documentation
- Yuhao agrees to take meeting notes

## Update from BHuman Team - Josiah
- BHuman team provided some feedback
- Identified helpful pointers and improvements
- Noted battery pack issues (should be repaired)
- Action item: Change credit section from BHuman to Wistex in codebase

## Behavior Cloning Discussion - Josiah & Zisen & Yuhao
- Focusing on near-goal data collection
- Discussing BCO (Behavior Cloning from Observation) approach
- Challenges with kick actions identified
- Proposed solution: Manual annotation for kicks. BCO walk + manual kicks

## Implementation Updates - Zisen
### Code Deployment
- Successfully deployed and verify bhuman appraoch to robot
- Working on classification model integration

### Data Processing & training
- Annotated ~200 gestures from BHuman
- Data is small, distribution on gesture is not uniform, most gesture is static
- Using CNN+GRU model with limited success due to small dataset and lack of temporal information

## Abstract Sim V2 Discussion - Multiple Participants
### Current Status - Edison & Josiah
- Edison working on setup with Abhinav's help
- Need to calibrate sim to match actual robots

### Performance Measurement - Zhihan
- Process: Recording and measuring robot movements
- Consideration of surface variations
- Qualitative assessment of movement speeds

## Technical Infrastructure - Yuhao
### Log Reader Issues
- Significant performance degradation (600hr completion time)
- Investigating memory and I/O issues
- Maybe we can reduce unnecessary data logging (e.g., camera images)

## Simulation Work - Adam
### Progress Update
- Limited progress due to other commitments
- Planning simple training tasks
- Investigating Google Humanoid simulation implementation

### Technical Challenges
- Experiencing bouncing issues in Mujoco
- Getting assistance from (Hanwen?
- Need to resolve joint actuation concerns

## Multi-Agent Implementation - Abhinav
### AbstractSim V2 Integration Status
- Interface remains consistent with V1
- Support for multiple agents confirmed
- Documentation tested by Edison and Will

### Performance Metrics
- 90% success rate achieved in Abstract Sim
- Need to verify SimRobot transfer (don't think there would be any problem)
- Pending video verification of metrics accuracy

## Training Pipeline - Siddhant
### Current Focus
- Streamlining data collection process
- Reducing human bottlenecks in training
- Working on spawn point initialization
- Goals:
  - Simplify policy testing
  - Improve data collection efficiency
  - Enable flexible robot positioning

## Cross-Team Collaboration - Josiah
### Imitation Learning Coordination
- Suggestion to connect Siddhant with Yuhao and Zisen
- Shared challenges in:
  - Logging appropriate data
  - Robot initialization

### BHuman Integration
- Discussion of complex action space
- Challenge: Unifying different command APIs
- Proposed solution: Focus on walk velocities
- Need to infer commands from observations

## Gesture Recognition Rule - Zisen
### Competition Rules - Josiah
- 2024/2025 rules under development now
- Shouldn't anticipated much changes in gesture recognition
- Reference to 2024 June 17th SPL rules

# Meeting Planning - Josiah
- Next week's meeting to proceed without Josiah
- Will/Adam to handle meeting setup
- Regular attendees (Zhihan, Siddhant) to maintain continuity


