---
title: 2024-10-29 WISC Meeting
layout: default
parent: Meeting Notes
---
## Jeffery

- Discussed dataset approach with Zisen

- BHuman dataset: select 2-3 most important images per second for training

## ZiSen

- Confirmed BHuman logic working in wistex system

- Referee thread: BHuman loads move net and heuristic logic

- Questions raised:

  - Entry point for running onnx?

    - Yuhao's suggestion: Trace BHuman code for onnx usage

  - Number of trajectories needed for IL algorithm?

    - Yuhao's response: As many as possible

- Note: Referee thread needs to infer onnx after whistle

## Yuhao

- Performance issues with py-log-reader

  - Parsed first data batch (1.39GB) in 8 hours

- BHuman2024 merge failed due to skill implementation changes:

  - Skills changed from separate classes to CABSL options under SkillBehaviorControl

  - Uses reflection mechanism for data storage

- Zhihan's question: Location of reflection data storage?

  - Yuhao's response: Possibly in SkillBehaviorControl or blackboard (uncertain)

- Will share skill change details in Slack

## Edisen Shen

- Investigating Walkengine

- Features walk phases with interpolated step position and velocity

- Adam's question: Control of desired angle at each time step?

  - Response: Yes, takes speed request, sends desired angle

## Adam

- Received assistance from mechanical engineering team

- Progress with mujoco:

  - Nearly achieved good standing behavior

  - Planning to use Deepmind soccer env for training

## Zhihan

- Discussed log usage with Yuhao

- Haven't implemented py-log-reader infrastructure

- Working with Siddhant on UT-Austin undergrad recruitment

- Focus on data collection and 2024 codebase transfer

- William's question: Status of abstractSim policy deployment

  - Response: Main challenge is action gap between simRobot and real robot

  - Working on neural network solution to bridge walk engine dynamics

## Siddhant

- Working on policy patching

- Removing game controller

- Peter's question: Whether to remove GameController or modify for constant playing state

  - Response: Will evaluate easiest modification approach

## Abhinav

- Working on abstractSim v2

  - Improved user understanding

  - Collaborating with Zhihan on SimRobot to abstractSim V2 migration

## Parv

- Examining goalkeeper code simulation

- Studying RL implementation for goalkeeper scenarios

## Zhihan

- BHuman Fast showing unusual behavior

  - Robot reported as broken

  - Adam: Confirmed similar previous observations

<!-- Jeffery:
    Discuss with Zisen about the dataset approach for the dataset 
    BHuman dataset have many image in each second, just pick 2 -3 image of the most important to do the training

ZiSen:
    Currently in wistex system, BHuman logic work

    In referee thread BHuman load move net, and heuristic logic to detect logic

    ZiSen ask: What should be the entry point to run the onnx?
    Yuhao suggest: Trace BHuman code to see where they use their onnx

    Referee thread need to infer the onnx after a whistle

    ZiSen ask: How many trajectory we need to train an IL algorithm ?

    Yuhao: As many as possible 

Yuhao:
    py-log-reader have performance issue, trying to profile that

    Finish parsing the first bunch of data (1.39GB) in 8 hours

    Fail to merge BHuman2024, as the skill implementation is changed drastically
        Originally each skill is a separate class, now each one is a CABSL option (method) under SkillBehaviorControl
        Use reflection mechanism to store field they need, I'm not familiar with it, maybe some senior people can help

    Zhihan ask: Where does the reflection store the data?

    Yuhao answer: In the SkillBehaviorControl I think, or in a blackboard, I'm not very sure

    Zhihan: Can you share the skill change point in slack?

    Yuhao: Sure

Edisen Shen

    Looking into Walkengine

    There are walk phase, between phase it interpolate the step position and velocity

    Adam ask: Control the desired angle at each time step?

    Edisen Shen answer: Yes. Take a request of speed, send desire angle



Adam:
    Get some help from people in mechanical engineering

    Close to working in mujoco

    Almost get good standing behavior

    If finished, can use Deepmind soccer env for more interesting training

Zhihan:

    Talk with Yuhao about how to use the log

    Haven't use the py-log-reader infrastructure 

    Work with Siddhant to send email to undergrad that is interested in this research at UT-Austin

    Working on data collection

    Consider transfer from current code base 2024

    William ask:
        Have we deploy some policy from abstractSim

    Zhihan:

        Currently biggest problem is that there is a huge gap of action in simRobot and real robot

        We are trying to bridge this gap by training a neural network that is a close enough proxy that capture the dynamic of the walk engine 


    Siddhant:
    
        Policy patching

        Remove game controller (? not hear clearly)

        Patch their policy right away and make a pipeline that don't need to care about BHuman stuff like game controller

        Peter ask:

            Is that the correct thing to do to remove GameController or is that easier to always make the game controller sending playing state?

            Maybe ask BHuman and they will give a much easier way

        Siddant answer:

            I can see which one is the easiest to modify

    Abhinav:

        Working with the abstractSim v2

        More understandable for people (?)
        
        Talking with Zhihan to migrate from SimRobot to abstractSim V2

    Parv:

        Looking at the simulation of goal keeper code

        Try to understand how RL works and should be implemented in the goal keeper case

    Zhihan:

        BHuman Fast have strange behavior, saying something strange like the robot was broken

        Adam:
        
        Also seen this before
    
    
 -->
