# Project 1, Part 2

In the second part of this project, you will profile your code from Part 1 and use the results of the profiling experiments to make informed optimizations.

## Task 1 - Strong Scaling

If a code exhibits ideal parallelism, it should complete twice as fast when running on two cores vs. running on one core - a speedup of 2.
Likewise, if run on 4 cores, it should run 4 times faster than on a single core - a speedup of 4.
Of course, in reality we never acheive these ideal speedups; our actual speedups will always be smaller than the ideal values.
Comparing our real-world speedups vs. ideal is a very good way to determine the efficiency of our parallelization scheme.

One of the most common ways to do this is to construct a plot of the **strong scaling** of our code.
For a problem of **fixed size** (e.g., number of atoms, size of matrices, etc.) we run calculations with various numbers of cores.
We then plot our observed speedups vs. number of cores.
We also plot the ideal speedup vs. number of cores (this will just be a straight line).
For an example, see [here](https://waterprogramming.wpcomstaging.com/2021/06/07/scaling-experiments-how-to-measure-the-performance-of-parallel-code-on-hpc-systems/).

Construct a strong scaling plot of your calculation using the Perlmutter CPU nodes, collecting data for at least 1, 2, 4, 8, 16, 32, and 64 cores on a single node.
Use a system size (number of atoms) that takes roughly 5-10 minutes to run 100 iterations in serial; you'll need to experiment a bit to find a reasonable number of atoms and simulation cell length.
*In addition to plotting the strong scaling of the entire calculation, also plot the strong scaling of relevant components of the calculation, including force evaluation, velocities update, and anything else that appears particularly relevant.*

Add to this `README.md` file your raw data (timings vs. number of cores) and your plots.

## Task 2 - Communication Cost

One of the primary challenges in distributed-memory parallelization is ensuring that communication is handled efficiently.
For the same system size that you used in Task 1, measure and plot the walltime associated with inter-process communication vs. number of cores.
Include the raw data and the plot in this `README.md`.

## Task 3 - Load Balance Measurement

Determine the degree to which your code is load balanced.
A common way to do this is to compute the ratio between the average time each processor spends doing computation with the maximum time any processor spends doing computation:

$\beta = T_{avg} / T_{max}$

The closer $\beta$ is to 1, the better load balanced the calculation.

Note that the measurement of "time spent doing computation" shouldn't include communication time or synchronization time.
Depending on how you have parallelized the calculation, it might not be straightforward to get this time for each rank.
If necessary, instead of measuring the time spent in computation, you can simply measure the number `N` of Lennard-Jones interactions evaluated by each rank (i.e., the number of interactions within the short-range cutoff for each rank).
Then your load balance metric would be:

$\beta \approx N_{avg} / N_{max}$

Report your result.

## Task 4 - Analysis

Discuss the efficiency of the code's parallelization.
It is common for classical molecular dynamics simulations to be run on millions or billions of atoms for millions of timesteps.
Is this practical using your code?
Describe some optimizations or algorithmic changes that could improve your code's parallelization and performance.

Note: Sometimes the results of a profiling experiment or optimization effort inspire ideas about other experiments that might be informative.  Feel free to run and include any other profiling results you find relevant.  For example, you might find it helpful to measure the arithmetic intensity of the code.

## Task 5 - Code Optimization

Based on your profiling results, describe and implement an optimization that is likely to improve the code's parallelization efficiency.
Repeat the strong scaling experiment from earlier and include your data and plots in this repository.
Compare your previous results with your new results.

Note: For credit, it isn't necessary to demonstrate a massive performance improvement here - just offer a clear and well-reasoned enhancement.



## Answers
