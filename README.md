# MCDM Techniques in Python
This repository contains Python :snake: implementations of multi-criteria decision-making techniques.

:triangular_flag_on_post: I have added Pairwise Comparison Matrix, Best-Worst Method, and AHP to the code :grey_exclamation:

:triangular_flag_on_post:From compensatory techniques, only Entropy, SAW, and WASPAS have been implemented :grey_exclamation:

:triangular_flag_on_post:The non-compensatory :thumbsdown::thumbsup: techniques are completed so far, which include Dominance, Maximin, Maximax, Hurwicz, Conjunctive, Disjunctive, Lexicographic, SemiLexicographic and Permutation methods :grey_exclamation:


## 🧠:PCM
In this method, a matrix is used (like Figure.1) to compute the weights of each criteria.

![Pairwise-comparison-matrix](https://github.com/user-attachments/assets/409096b1-030c-4c28-93b6-6e2b4eb9b8d5)

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;*Figure.1 A Pairwise Comparison Matrix [1]*

🌵Before computing the weights, the consistency of the matrix should be checked. If the matrix is consistent there are four methods to find the weights: 

  1. Sum of Rows 
  2. Sum of Columns
  3. Arithmetic Mean 
  4. Geometric Mean

🥑Geometric Mean is the best, and the Sum of Rows is the worst one. However, if the matrix is inconsistant, there are four methods to compute the weights:
  1. Least Square Method
  2. Logarithmic Least Square Method
  3. Eigenvalue Method
 
  
## Best-Worst Method (BWM)
You can find this method in [2]. This method reduces the computations a lot; however, it requires solving a nonlinear mathematical model. 
The baseline code is from https://github.com/Valdecy/pyDecision.git repository. However, there were some issues 📰, which I corrected.

There are two methods for computing consistency in BWM: 
1. Input-based consistency
2. Output-based consistency

Both of which have been added to the code.

Also, there are two models to find the weights. You can find both of them in the code.


## AHP
I used https://github.com/PhilipGriffith/AHPy.git repo for this method. Amazing implementation, but it does not support qualitative values :x:

You can find an example of AHP in Figure.2.

![AHP](https://github.com/user-attachments/assets/b430085d-747e-4784-8f75-d3e39b832406)

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;*Figure.2 An example of AHP [3]*


# Citation

[1] *Aguilar N., Galindo G., Contreras C., Fontanelli J. (2012). A meth-odological approach to sugar mill diversification and conversion. Ingeniería eInvestigación. Vol. 32, No. 2, August 2012, pp. 23-27. 
(PDF) A methodological approach to sugar mill diversification and conversion. Available from: https://www.researchgate.net/publication/262752979_A_methodological_approach_to_sugar_mill_diversification_and_conversion [accessed Nov 07 2024].

[2] *Jafar Rezaei, Best-worst multi-criteria decision-making method, Omega, Volume 53, 2015, Pages 49-57 ISSN 0305-0483, https://doi.org/10.1016/j.omega.2014.11.009, https://www.sciencedirect.com/science/article/pii/S0305048314001480.

[3] *Akarte, M. M., Surendra, N. V., Ravi, B., & Rangaraj, N. (2001). Web based casting supplier evaluation using analytical hierarchy process. Journal of the Operational Research Society, 52(5), 511–522. https://doi.org/10.1057/palgrave.jors.2601124
