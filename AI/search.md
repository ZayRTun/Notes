**Home**
- [Home](../index.md)
---
## Introduction to Artificial Intelligence with Python
# Search


## Search Problems
- initial state  
- actions  
- transition model  
- goal test  
- path cost function  

### Agent  
Entity that perceives its environment
and acts upon that environment  

### State
A configuration of the agent and
its environment

### Initial state
The state in which the agent begins  

### Actions
Choices that can be made in a state

**Actions**  
ACTIONS(s) returns the set of actions that
can be executed in state s

### Transition model
A description of what state results from
performing any applicable action in any
state  
**Transition model**
RESULT(s, a) returns the state resulting from
performing action a in state s

### State space
The set of all states reachable from the
initial state by any sequence of actions  

### goal test
way to determine whether a given state
is a goal state  

## path cost
numerical cost associated with a given path  
## solution
a sequence of actions that leads from the
initial state to a goal state  
## optimal solution
a solution that has the lowest path cost
among all solutions

## node
**a data structure that keeps track of**
- a state
- a parent (node that generated this node)
- an action (action applied to parent to get node)
- a path cost (from initial state to node)  

# Approach
- Start with a frontier that contains the initial state.
- Repeat:
 - If the frontier is empty, then no solution.
 - Remove a node from the frontier.
 - If node contains goal state, return the solution.
 - Expand node, add resulting nodes to the frontier.  

Find a path from A to E.
• Start with a frontier that contains the initial state.
• Repeat:
• If the frontier is empty, then no solution.
• Remove a node from the frontier.
• If node contains goal state, return the solution.
• Expand node, add resulting nodes to the frontier.