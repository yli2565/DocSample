---
title: 2024-12-10 WISC Meeting
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

## Professor Josiah Hanna
- Provided feedback on motion mapping concerns in Mujoco, particularly highlighting dependencies on historical sensor data for calculations like swing foot
- Emphasized need for quality assurance metrics between AbstractSim V1 and V2 policies
- Discussed trade-offs between flexibility and configurability in simulator architecture
- Facilitated discussion about future meeting schedules

## ZiSen
- Found updates in rule book regarding new robot gestures
- Planning collaboration with Erika on gesture-related work
- Proposed using Unreal Engine for gesture recognition data collection, citing support from relevant papers in Peter's repository
- Will continue engineering work on Nao gesture implementation

## Adam
- Attempted walk engine binary compilation and export
- Taking alternative approach by collecting simulated joint data from Nao's forward walking
- Working on replicating walk patterns in Mujoco
- Plans to collect and utilize game data for further development

## Zhihan
- Collaborating with Edison and Abhinav on AbstractSim V2 integration
- Training policies on Abhinav's branch while learning codebase structure
- Identified cross-platform compatibility challenges between MacOS and Ubuntu
- Working on documentation needs for different platforms

## Edison
- Leading policy transfer efforts from AbstractSim V2 to SimRobot
- Identified key technical issues:
  - Value normalization discrepancy between simulators (AbstractSim not clipped to [-1,1])
  - Unusual curved paths observed in both simulators
- Considering replay buffer implementation to address policy behavior
- Expressed appreciation for Abhinav's configurable design approach

## Abhinav
- Spearheading configurable AbstractSim V2 development
- Collaborating with Edison on SimRobot transfer implementation
- Working toward completing unified V2 version within the week
- Focus on creating consolidated codebase for training and simulator transfer

## Dmitry
- Present but experienced technical difficulties with audio

## Action Items
- Develop cross-platform documentation for AbstractSim V2
- Complete unified version of AbstractSim V2
- Advance gesture recognition implementation
- Establish quality metrics for comparing V1 and V2 policies

## Next Steps
- Team confirmed next week's meeting
- Noted scheduling considerations for Wisconsin's finals week
- January meetings to be scheduled on demand