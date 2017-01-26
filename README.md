# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?

A: Naked twins are two boxes in a unit that have the same value of length 2. For example consider the case where C3 = 45 and C8 = 45, and they both belong in the same row unit C. From the sudoku's local unit constraints this means that the digits 4 and 5 can only be in either C3 or C8 but we don't know exactly which of C3 or C8 has 4 and 5, in other words it creates a local *constraint* that 4 and 5 cannot be in boxes other than C3 and C8, hence we can **eliminate** the presence of 4 and 5 from boxes in row unit C other than C3 and C8. Such an elimination is one of the many strategies of constraint propagation, where we trim down the infeasible cases by enforcing a local constraint. Since each unit can have naked twins, we have to apply the 'eliminate' step for each unit of the sudoku board.

# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?

A: The diagonal sudoku problem has an additional constraint that digits cannot repeat per each diagonal in addition to the regular row, column and square constraints. Like the regular constraints of sudoku, the diagonal constraint is also a local constraint which can be used to reduce the search space without changing the solution of the problem which is exactly what constraint propagation does hence constraint propagation method is an appropriate method to find its solution. The application of constraint propagation with search to diagonal sudoku is similar to how it is applied to normal sudoku, except that there are two more extra units which are the diagonals of the sudoku board. Each unit has the constraint that the digits from 1 to 9 are not repeated. The constraint-propagation-steps involved are :

1. Elimination :- For each solved box, with single digit x in it, we remove the presence of digit x from all of its peers. This is the enforcement of the sudoku rule that there should not be any repeated digit in a unit.

2. only_choice : In each unit if a digit appears only in exactly one of its boxes, then the value of that box can be reduced to that single digit.

3. naked_twins elimination strategy : As described in answer to question 1, this step finds any naked twin in each unit and enforces the constraint that no squares outside the two naked twins squares can contain the twin values.

Just repeating the above three steps may not solve the diagonal sudoku problem especially for harder problems, so we use Depth First Search(DFS) to search in the current solution space and apply the above 3 steps for each traversed step of DFS.

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solutions.py` - You'll fill this in as part of your solution.
* `solution_test.py` - Do not modify this. You can test your solution by running `python solution_test.py`.
* `PySudoku.py` - Do not modify this. This is code for visualizing your solution.
* `visualize.py` - Do not modify this. This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the ```assign_values``` function provided in function.py

### Data

The data consists of a text file of diagonal sudokus for you to solve.
