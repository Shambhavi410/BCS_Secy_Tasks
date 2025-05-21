Link to Colab file:
https://drive.google.com/file/d/1bTQbMuR-0o4zJ1PFqoIFqMuorwFW_IyJ/view?usp=sharing

This project implements a Q-learning reinforcement learning agent to navigate a custom maze environment. 
The agent, representing Harry Potter, must reach a Cup while avoiding a Death Eater who uses a BFS strategy to chase him.

Overview
Environment: Grid-based maze loaded from a text file.
Agent Goal: Reach the Cup without getting caught by the Death Eater.
Death Eater Strategy: Uses Breadth-First Search (BFS) to find the shortest path to Harry.
Learning Algorithm: Q-learning with epsilon-greedy action selection.

Assumptions
Maze files are stored as plain text, where:
'X' represents a wall
Empty spaces are passable
Harry, the Death Eater, and the Cup are placed randomly on valid, non-overlapping, free spaces at the start of each episode.
The state is represented as a tuple: ((harry_row, harry_col), (death_row, death_col), (cup_row, cup_col)).
The Q-table is stored as a Python dictionary with state tuples as keys.

Rewards
Step penalty: -1 for each move.
Goal reward: +100 if Harry reaches the Cup.
Penalty: -100 if Harry is caught by the Death Eater.

How to run the code:
The code is currently working for maze2. If for any other maze, then the file name will have to be changed.

Also, I wasn't able to upload the Q_Table as the size was too large. On running the code, the Q table will get saved.
