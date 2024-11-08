# MCDM Techniques in Python
This repository contains Python implementations of multi-criteria decision-making techniques.

:triangular_flag_on_post: I have added Pairwise Comparison Matrix, Best-Worst Method and AHP to the code. 

:triangular_flag_on_post:From compensatory techniques, only Entropy, SAW, and WASPAS have been implemented.

:triangular_flag_on_post:The non-compensatory techniques are completed so far, which include Dominance, Maximin, Maximax, Hurwicz, Conjunctive, Disjunctive, Lexicographic, SemiLexicographic and Permutation methods.


## PCM
In this method, a matrix is used (like Figure.1) to compute the weights of each criteria.

![Pairwise-comparison-matrix](https://github.com/user-attachments/assets/409096b1-030c-4c28-93b6-6e2b4eb9b8d5)
*Figure.1 A Pairwise Comparison Matrix [1]*

Before computing the weights, the consistency of the matrix should be checked. If the matrix is consistant there are four methods to find the weights: 

  1. Sum of Rows
  2. Sum of Columns
  3. Arithmetic Mean
  4. Geometric Mean
Geometric Mean is the best and the Sum of Rows is the worst ones. However, if the matrix is inconsistant, there are four method to compute the weights:
  1. Least Square Method
  2. Logarithmic Least Square Method
  3. Eigenvalue Method
 
  
