# MCDM Techniques in Python
This repository contains Python :snake: implementations of multi-criteria decision-making techniques.

:triangular_flag_on_post:Weighted-Sum Method, Goal Programming (Weighted and Lexicographic), Epsilon Constraint, and Augmented Epsilon Constraint (Augmecon) have been implemented as multi objective methods using Pyomo :grey_exclamation:

:triangular_flag_on_post:From compensatory techniques, Entropy, SAW, WASPAS, Pairwise Comparison Matrix, Best-Worst Method, AHP, Topsis, Vikor, Dematel, Promethee I, and Electre I have been implemented :grey_exclamation:

:triangular_flag_on_post:The non-compensatory :thumbsdown::thumbsup: techniques are completed so far, which include Dominance, Maximin, Maximax, Hurwicz, Conjunctive, Disjunctive, Lexicographic, SemiLexicographic and Permutation methods :grey_exclamation:

## MODM
### Weighted-Sum Method (WSM)
The Weighted Sum Method (WSM) is arguably the simplest approach for multi-objective optimization. This method works by multiplying each objective function by its assigned weight and then summing them together to form a single composite objective function. Once this combined function is obtained, standard single-objective optimization techniques can be used to solve the problem.
![wsm](https://github.com/user-attachments/assets/d28aa957-60f6-42dd-aadb-2c477bbb2013)
                                                                                                                      
### Goal Programming
Goal Programming is a straightforward and widely used method for multi-objective optimization. It works by converting multiple objectives into specific target goals. The method minimizes the deviations between the achieved results and these predefined goals.

In this approach, objectives are reformulated into constraints, each with associated deviation variables to account for underachievement or overachievement relative to the target. A weighted sum of these deviations is then minimized, with the weights reflecting the relative importance of achieving each goal.

By focusing on reducing deviations rather than optimizing a single composite function, Goal Programming allows decision-makers to prioritize multiple, potentially conflicting objectives in a flexible and structured manner.

Weighted Goal Programming (WGP):
![wgp](https://github.com/user-attachments/assets/cd0228e0-2f07-4afa-bc26-3b9a2c8ab88b)


Lexicographic Goal Programming (LGP):

It is just like weighted goal programming, but W1 >> W2 >> ... >> Wn.



### Epsilon Constraint
The ε-Constraint Method is a popular technique for multi-objective optimization that focuses on optimizing one objective while treating the remaining objectives as constraints. Each of these additional objectives is bounded by a predefined threshold value, ϵ.

In this approach, one objective function is selected as the primary objective to be maximized or minimized. The other objectives are converted into constraints, where their values must not exceed or fall below specified ϵ-values. By systematically varying these ϵ-values, a set of Pareto-optimal solutions can be obtained, representing different trade-offs among the objectives.

The ε-Constraint Method is particularly useful for exploring the trade-off space in detail and generating solutions that satisfy specific decision-maker preferences or practical requirements.
![ep](https://github.com/user-attachments/assets/c00646bf-6cca-4130-94d2-06f6a4afdfc9)

**The main drawback of the ε-Constraint Method is that it also produces weakly efficient solutions.**


### Augmented Epsilon Constrain (Augmented)
The Augmented ε-Constraint Method is an enhanced version of the ε-Constraint Method that optimizes one objective while converting the remaining objectives into constraints, augmented by a small penalty term to ensure a more balanced exploration of the Pareto front.

In this approach, a penalty term proportional to the sum of constraint violations is added to the primary objective function. This modification encourages solutions that not only optimize the primary objective but also remain feasible with respect to the other objectives' ϵ-values. By systematically varying ϵ-values, the method generates Pareto-optimal solutions while improving solution diversity and stability.

![aug](https://github.com/user-attachments/assets/a64e0fb3-518f-4127-81bf-067df131a089)

**This method's key advantage is that it only produces efficient solutions (no weakly efficient solutions are produced)**


## MADM
### 🧠:PCM
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
 
  
### Best-Worst Method (BWM)
You can find this method in [2]. This method reduces the computations a lot; however, it requires solving a nonlinear mathematical model. 
The baseline code is from https://github.com/Valdecy/pyDecision.git repository. However, there were some issues 📰, which I corrected.

There are two methods for computing consistency in BWM: 
1. Input-based consistency
2. Output-based consistency

Both of which have been added to the code.

Also, there are two models to find the weights. You can find both of them in the code.


### AHP
I used https://github.com/PhilipGriffith/AHPy.git repo for this method. Amazing implementation, but it does not support qualitative values :x:

You can find an example of AHP in Figure.2.

![AHP](https://github.com/user-attachments/assets/b430085d-747e-4784-8f75-d3e39b832406)

&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;*Figure.2 An example of AHP [3]*

### TOPSIS
The TOPSIS method considers not only the distance from the ideal solution but also the distance from the worst-case scenario. According to this approach, the best option is the one with the shortest distance to the ideal solution and the greatest distance from the worst-case scenario.

To achieve this, the decision matrix is first normalized, followed by the calculation of the weighted decision matrix by multiplying the criteria weights with the decision matrix. Next, the Euclidean distance of each option from the ideal and worst-case scenarios is computed, and the relative closeness index (rci) is determined.

The closer the rci value is to one, the closer the option is to the ideal solution and the farther it is from the worst-case scenario, and vice versa.


### VIKOR
The VIKOR method, similar to TOPSIS, is a technique used to select the best option among several alternatives based on their distance from the ideal solution. In this method, the average distance of each option from the ideal solution across all criteria is calculated (denoted as Si), as well as the maximum distance (Ri). Using these two values, Qi is computed, which combines the average distance and the maximum distance from the ideal solution. Finally, based on a set of conditions applied to Ri, Si, and Qi, the best option is selected.

A limitation of this method is that it does not provide a complete ranking of the alternatives; it only identifies the best options.


### DEMATEL
The DEMATEL method is a decision-making approach used to analyze and model the cause-and-effect relationships among multiple criteria. Unlike TOPSIS and VIKOR, which focus on ranking or selecting the best alternative, DEMATEL emphasizes understanding the interdependencies and influence of criteria on one another.

In this method, an initial direct-relation matrix is constructed based on expert evaluations, capturing the direct influence of one criterion on another. This matrix is then normalized to ensure comparability of values. By iteratively summing the direct and indirect effects, a total-relation matrix is obtained, which represents the overall influence of each criterion on all others.

From the total-relation matrix, two key indices are calculated for each criterion: the sum of rows (D) and the sum of columns (R). The value of D+R indicates the overall importance of the criterion (its role in the system), while D−R reflects whether the criterion is a net cause (positive D−R) or a net effect (negative D−R).

DEMATEL's primary strength lies in its ability to identify and visualize the cause-and-effect relationships among criteria, providing valuable insights for structuring complex decision-making problems. However, its focus on relationships rather than ranking alternatives can limit its application in certain scenarios.

I used https://github.com/Valdecy/pyDecision/blob/master/pyDecision/algorithm/dematel.py as a source code for my own implementaion.


## PROMETHEE I :godmode:
The PROMETHEE I method is a multi-criteria decision-making approach designed to provide a partial ranking of alternatives based on pairwise comparisons of criteria. PROMETHEE I does not produce a complete ranking but instead identifies the relationships between alternatives, such as which options are preferred, indifferent, or incomparable.

The method begins by calculating preference indices for each pair of alternatives across all criteria. These indices are determined using predefined preference functions that quantify the degree to which one alternative is preferred over another for each criterion. Next, the weighted preference indices are aggregated, considering the importance (weights) of the criteria.

Using these aggregated indices, two key measures are calculated for each alternative:

  •	Positive outranking flow (ϕ+): Reflects how much an alternative outranks all others.
  
  •	Negative outranking flow (ϕ−): Reflects how much an alternative is outranked by all others.
  
Based on these flows, PROMETHEE I establishes a partial ranking by determining which alternatives are better or worse and identifying those that are incomparable due to conflicting outranking relationships.
The main advantage of PROMETHEE I is its ability to handle complex decision-making scenarios with multiple conflicting criteria while accommodating the decision-maker's preferences. However, its limitation lies in providing only a partial ranking, which may require further analysis (e.g., PROMETHEE II) for a complete ranking of alternatives.


## ELECTRE I ⛈️
The ELECTRE I method (Elimination and Choice Expressing Reality) is a multi-criteria decision-making technique used to identify the most suitable alternatives by comparing them against each other through pairwise analysis. ELECTRE I focuses on selecting a subset of alternatives that are not outranked by others, rather than providing a complete ranking.

The process begins with constructing a decision matrix, followed by normalizing it and applying criteria weights to create a weighted normalized decision matrix. Next, two matrices are derived:

1.	Concordance matrix: Represents the extent to which one alternative is better than another based on the criteria that support this preference.
2.	
3.	Discordance matrix: Measures the extent of disagreement, reflecting how much one alternative performs worse than another on certain criteria.
4.	
Thresholds for concordance and discordance are then defined, allowing the construction of an outranking matrix. This matrix identifies whether an alternative AAA outranks another alternative BBB based on the agreement and disagreement levels.

Finally, alternatives that are not outranked by any others (or have minimal outranking relations) are selected as the preferred options.

ELECTRE I’s strength lies in its ability to handle complex problems with conflicting criteria and incomplete or imprecise data. However, its limitation is that it does not provide a complete ranking of alternatives, focusing instead on identifying a set of feasible solutions. For more detailed rankings, extended versions like ELECTRE II or ELECTRE III may be used.


# Citation

[1] *Aguilar N., Galindo G., Contreras C., Fontanelli J. (2012). A meth-odological approach to sugar mill diversification and conversion. Ingeniería eInvestigación. Vol. 32, No. 2, August 2012, pp. 23-27. 
(PDF) A methodological approach to sugar mill diversification and conversion. Available from: https://www.researchgate.net/publication/262752979_A_methodological_approach_to_sugar_mill_diversification_and_conversion [accessed Nov 07 2024].

[2] *Jafar Rezaei, Best-worst multi-criteria decision-making method, Omega, Volume 53, 2015, Pages 49-57 ISSN 0305-0483, https://doi.org/10.1016/j.omega.2014.11.009, https://www.sciencedirect.com/science/article/pii/S0305048314001480.

[3] *Akarte, M. M., Surendra, N. V., Ravi, B., & Rangaraj, N. (2001). Web based casting supplier evaluation using analytical hierarchy process. Journal of the Operational Research Society, 52(5), 511–522. https://doi.org/10.1057/palgrave.jors.2601124
