---
layout: post
title: "Game Theory Course Note"
subtitle:
date: 2019-11-15
published: True
tags:
  - 博弈论-game theory
  - 公开课-MOOC
  - 学习笔记-course note
---
# Introduction
Lately, I'm working on a project related to poker AI, which is related to game theory. To learn more about game theory, I choose the [Game Theory from Stanford University and the University of British Columbia in Cousera](https://www.coursera.org/learn/game-theory-1).(I still don't know how to display the math charactors correctly)

# Basic Concepts of Week 1
### Define Game
**Three key ingredients:**
1. Player
2. Actions
3. Payoffs/utility

**Two forms:**
1. Normal form
2. Extensive form: beside player, action, payoff(utility), there are timeing, information(state?)

**Categoty:**
1. Game of pure competition
2. game of cooperation

### Best response and Nash equilibrium
For ith player, his action profile is $A_i$, then the left players's action profiles in the game are:$a_(i-1) = (a_i, ...a_(i-1), a_(i+1)...a_n)$

**Best response:**

$a*_i \in BR(a_(-i)) iff \foralla_i \in A_i, u_i(a*_i, a*_(-i)) \geq u_i(a_i, a_(-i)))$

**Nash Equilibrium**

$a = (a_1, a_2,....a_i,....a_n) is a (pure strategy) Nash equilibrium iff \forall i, a_i \in BR(a_(-i))$

### Dominant strategies and Nash equilibrium
Let s_i and s_i^{\prime} be two strategies for player i and S_{-i} be the set of all possible strategies for the other players

**Domination**

$s_i **strictly dominates** s_i^{\prime} if \forall s_{-i} \in S_{-1}, u_i(s_i, s_{-i}) > u_i(s_i^{\prime}, s_{-i})$

$s_i **weekly dominates** s_i^{\prime} if \forall s_{-i} \in S_{-1}, u_i(s_i, s_{-i}) \geq u_i(s_i^{\prime}, s_{-i

**Pareto Optimality**
As for game outcome, sometimes one outcome O is at least as good for every agent as another O', and there is some agent who strictly prefers O to O'. We say O Pareto-deminates O'.

$An outcome O* is Pareto-optimal if there is no other outcome that Pareto-optimal it$
