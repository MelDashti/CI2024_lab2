# Set Cover Problem - Lab 1

## Problem Statement

This lab required solving instances of the Set Cover Problem with varying universe sizes, number of sets, and densities. The objective was to implement a solution that efficiently handles these variations and reports the initial and final fitness values.

![Set Cover Problem Description](image.png)

The goal is to **find the minimum-cost subfamily of `S`** such that the union of these subsets covers `U`.

## Approach

The implemented Tabu Search algorithm for the Set Cover Problem includes:

- **Dynamic Tabu List**: Starts with an initial size and grows as the search progresses, balancing between exploration and exploitation.
- **Aspiration Criteria**: Allows accepting moves in the tabu list if they lead to a solution better than the best found so far.
- **Multiple Mutation**: Generates diverse neighborhood solutions by potentially flipping multiple bits in the solution representation.
- **Fitness Tracking**: Monitors and stores the fitness of solutions throughout the search process.
- **Multi-Instance Testing**: Applies the algorithm to multiple problem instances with varying parameters, demonstrating its adaptability to different problem scales.
- **Results Visualization**: Provides graphical representation of the algorithm's performance for each instance, aiding in analysis and comparison.

The solution was tested across multiple instances, demonstrating its effectiveness in finding optimal or near-optimal solutions.

## Results

| Instance | Universe Size | Num Sets | Density | Initial Fitness | Final Fitness |
|----------|---------------|----------|---------|-----------------|---------------|
| 1        | 100           | 10       | 0.2     | -29.9648       |   0            |
| 2        | 1,000         | 100      | 0.2     | -14241.1775  |  -6409.3919     |
| 3        | 10,000         | 1,000     | 0.2    | -1243184.90   | -571303.45     |
| 4        | 10,0000         | 10,000     | 0.1    | -74629161.782  | -74629161.78218833    |
| 5        | 100,000         | 10,000     | 0.2    | -165060887.250   |  -165014923.3968753)    |
| 6        | 100,000         | 10,000     | 0.3    |   -252231834.97        |               |


## Performance Analysis

- The algorithm consistently improved the initial random solutions, the algorithm doesn't work well for 100,000. Haven't figured out why yet. 
- Larger instances (100,000 universe size) required significantly more computation time.
- Density variations impacted the ease of finding valid solutions.

## Challenges and Optimizations

- **Memory Management**: Implemented efficient data structures for large instances.
- **Runtime Optimization**: Used vectorized operations where possible.
- **Parameter Tuning**: Adjusted tabu list size and mutation rate for different instance sizes.
- **Biggest Challenge**: testing the algo on 100,000 universe size on my 6-year-old laptop was like using the free version of ChatGPT during peak hours. 


## Acknowledgments

For this Computational Intelligence lab submission, I explored various resources. While ChatGPT is a popular choice, I decided to give Claude AI a chance, and it proved to be a great help. As always, Google was my trusty companion throughout the process.

## References

1. Glover, F. (1989). Tabu Search—Part I. ORSA Journal on Computing.
