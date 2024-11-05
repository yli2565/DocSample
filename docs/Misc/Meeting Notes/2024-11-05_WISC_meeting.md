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

## Doc Page / Meeting Notes

- Put web page link on slack
- Yuhao will take meeting notes

## Update from BHuman Team - Josiah

- BHuman team provided some feedback
- Battery pack issues noted (repaired in summer)
- Change "cite them" to "cite us" in codebase

## Behavior Cloning Update - Zisen & Yuhao & Josiah

- Collecting near-goal data for behavior cloning
- Focus specifically on near-goal scenarios

## Technical Discussion on BCO - Zisen & Yuhao & Josiah

- Identified challenges with kick actions in BCO approach
- Discussed walk-to-point and kick implementation (might be hard in BCO)
- Proposed solution: Manual annotation for kicks in expert data
- Or just BCO control walk and heuristic control kick

## GRU Model Discussion - Zisen & Josiah

- GRU model implementation showing suboptimal results
- Poor validation performance attributed to small dataset size
- Discussion about temporal information necessity
- Reference to BeHuman's successful 2022 approach
- Consideration of data augmentation needs

## Log Reader Issues - Yuhao & Josiah

- Significant performance issues with log reader
- Processing time increased to 600 hours
- Investigating potential memory leak issues
- Discussion about I/O and latency concerns
- Memory management strategy review

## Logging Infrastructure Discussion - Yuhao & Josiah

- Detailed review of logging infrastructure
- Challenge with selective data logging
- Discussion about unnecessary data storage (camera images)
- Consideration of memory optimization strategies

## Google Humanoid Update - Adam & Josiah

- Limited progress reported due to other commitments
- Plans to work on basic training tasks (like standing)
- Discussion about Simulated Humanoid
- Noted issues with model behavior and bouncing in Mujoco
- Received assistance from Hanweng on technical challenges - suggest joint actuation

## Undergraduate Recruitment - Zhihan

- First UT meeting completed with demo and Q&A
- 6-8 students showed interest
- Coordinating weekly meeting schedules
- Using existing documentation for onboarding process
- Planning demo session for visiting high school students

## Critical Bug Discovery - Zhihan & Edison

- Major bug found in walking implementation
- Issue: Policy output 3 dimensions, but 5th dimension (garbage value) is used to determine whether to stand
- Impact: Robot alternating between walking and standing
- Discussion about bug's competition impact
- In the competition, we are using V1 which have that option to stand

## Abstract Sim V2 Progress - Team Discussion

- Reality gap assessment between robot and simulation
- Walking issues less significant post-bug fixes
- Implementation and testing plans discussed
- Down grade the priority of neural network to predict transition
- Documentation needs identified

## Abstract Sim V2 Implementation - Edison & Josiah

- Edison working on getting Abstract Sim V2 setup
- Collaborating with Abhinav for implementation
- Discussion about calibration with actual robots
- Zhihan notes qualitative assessment looking positive

## Robot Movement Calibration - Zhihan & Josiah

- Process for measuring robot movement speeds outlined
- Video recording method for speed calibration
- Consideration of surface variations impact
- Discussion about configurable movement parameters

## Brief Update - Parve

- Limited progress due to midterm preparations
- Some work completed on goalkeeper code
- Discussion about future coordination needs

## V2 Implementation Planning - Zhihan & Abhinav & Josiah

- Plans for transitioning team to V2 usage
- Interface compatibility confirmation - Zhihan
- Documentation status from Abhinav
- Config hierarchy discussion
- Testing requirements before merge

## Extended Team Coordination on V2 - Zhihan & Abhinav & Josiah

- Training success rates reported (90% in Abstract Sim)
- SimRobot transfer testing requirements outlined
- V2 merge criteria discussed
- Performance metrics and frame rate considerations
- V2 need to have good performance for training hours or even days
- Coordination with absent team members (Will, Brennan, Alan)
- Plans for simulation calibration assessment

## Processing Gesture Recognition Data - Jeffery

- Looking at the Visual Referee Detection on Nao Robots for RoboCup SPL 2022 - Lukas Molnar
- Follow up next week

## Streamline Data Collection & Imitation Learning - Sidant

- Streamlining data collection process
- Improving training pipeline efficiency
- Discussion about initialization points
- Coordination between imitation learning efforts (with Yuhao and Zisen)
- Knowledge sharing about BCO implementation

## Gesture Recognition Rule? - Zisen & Josiah

- 2024/2025 rules under development now
- Shouldn't anticipated much changes in gesture recognition
- Reference to 2024 June 17th SPL rules

## Meeting Wrap-up

- Next week's meeting planning
- Josiah's absence next week noted
- Will/Adam to coordinate next meeting
- Next meeting with Josiah in two weeks
