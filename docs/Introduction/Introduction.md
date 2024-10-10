---
layout: default
title: "Introduction"
---
# Introduction


💡 Questions will be answered in this page:

1. What is RoboCup? 
2. What is B-Human and its relation to our codebase ([BadgerRLSystem](/docs/BadgerRLSystem/BadgerRLSystem.html))?


# RoboCup

[**RoboCup**](https://robocup.org/) is an annual international robotics competition founded in 1996. It has six major domains of competition, each with a number of leagues and sub-leagues. 

The league we are currently participating in is [Standard Platform League (SPL)](https://www.robocup.org/leagues/5), which happens during summer. The current standard robot is the humanoid robot NAO. In the past years, we participated in the SPL Challenge Shield Division, which features 5 vs. 5 matches. In RoboCup 2025, we will participate in the SPL Champions Cup Division, which features 7 vs. 7 matches.

# B-Human

B-Human is a RoboCup team that participated in the Standard Platform League. They release their codebase every year in the [**BHumanCodeRelease**](https://github.com/bhuman/BHumanCodeRelease) repo, which consists of about 150000 lines of C++ code. The codebase is long but has a clear structure, and they have a detailed [doc](https://docs.b-human.de/master/) for their codebase.

Our codebase, BadgerRLSystem, is forked from BHumanCodeRelease, with modification to enable reinforcement learning policy running on simulation and physical robots.