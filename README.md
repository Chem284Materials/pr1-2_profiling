# Project 1, Part 2

In the second part of this project, you will profile your code from Part 1 and use the results of the profiling experiments to make informed optimizations.

## Task 1 - Strong Scaling

If a code exhibits ideal parallelism, it should complete twice as fast when running on two cores vs. running on one core - a speedup of 2.
Likewise, if we run on 4 cores, it should run 4 times faster than on a single core - a speedup of 4.
Of course, in reality we never acheive these ideal speedups; our actual speedups will always be smaller than the ideal values.
Comparing our real-world speedups vs ideal is a very good way to determine the efficiency of our parallelization scheme.

One of the most common ways to do this is to construct a plot of the **strong scaling** of our code.
For a problem of **fixed size** (e.g., number of atoms, size of matrices, etc.) we run calculations with various numbers of cores.
We then plot our observed speedups vs. number of cores.
We also plot the ideal speedup vs. number of cores (this will just be a straight line).
For an example, see [here](https://waterprogramming.wpcomstaging.com/2021/06/07/scaling-experiments-how-to-measure-the-performance-of-parallel-code-on-hpc-systems/).

Construct a strong scaling plot of your calculation, from 1 to at least 64 cores on the Perlmutter CPU nodes.
Use a system size (number of atoms) that takes roughly 5-10 minutes to run 100 iterations in serial; you'll need to experiment a bit to find a good size.
*In addition to plotting the strong scaling of the entire calculation, also plot the strong scaling of relevant components of the calculation, including force evaluation, neighborlist evaluation, and anything else that appears particularly relevant.*

Add to this `README.md` file your raw data (timings vs. number of cores) and your plots.

## Task 2 - Communication Cost

One of the primary challenges in distributed-memory parallelization is ensuring that communication is handled efficiently.
For the same system size that you used in Task 1, measure and plot the walltime associated with inter-process communication vs. number of cores.
Include the raw data and plot in this README.md

## Answers
