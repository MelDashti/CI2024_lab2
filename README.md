# Traveling Salesman Problem (TSP) Solver

## Lab Requirements
The requirements for the lab are as follows:
- Solve the given TSP instances using both a fast but approximate algorithm and a slower, yet more accurate one.
- Report the final cost and the number of steps taken in each approach.
- The instances considered are provided in a CSV file containing the names and coordinates (latitude and longitude) of cities in Italy.

## Dataset
The dataset used for this project is a CSV file containing a list of cities in Italy with their corresponding latitude and longitude coordinates.

## Evolutionary Algorithm Experiments

### Configuration Parameters
Base configuration for all experiments:
- Number of Cities: 46
- Population Size: 100
- Number of Parents: 20
- Number of Generations: 5000 & 10000
- Elite Size: 5

### Experiment Results

#### Selection Method Experiments
| Selection Method | Best Distance | Generations to Best | Observations |
|-----------------|---------------|---------------------|--------------|
| Basic Roulette Wheel | 4591 | 3916 | A slower convergence compared to the rest |
| Tournament (size=3) | 4182.42 | 1632 | Best distance found after 1632, indicates that it converges very quickly |
| Rank-Based | 4175 | 4365 | A slower convergence with a slightly better distance compared to the rest |

Tournament Selection is used in the following experiments.

#### Mutation Experiments
| Mutation Type | Rate | Best Distance | Generations to Best|  Observations |
|--------------|------|---------------|--------------| --------------|
| Basic Swap | 0.3 | 7054.69 |1631|  Worst performance compared to the others |
| Inversion | 0.1 | 4560 |2299 |  Significantly better than the basic swap mutation| 
| Inversion | 0.3 | 4337 |1135 |  Better results with 0.3 mutation |
| Inversion | 0.5 | 4688.8 | 2943 | Slower convergence and worse fitness compared to 0.3|
| Inversion | 1.0 | 4419 |4145|  Similar to 0.5|
| Scramble | 0.3 | 7340.92 | 2482| Performed worse than other mutation types |
| Scramble (10000 gen) | 0.5 | 8150 | 2938| Remains as the lowest performing mutation type |

Adaptive mutation didn't help improve the performance by much.
Inversion Mutation is used with a mutation rate of 0.3 for the following experiments. 

#### Crossover Experiments
| Crossover Type | Best Distance | Generations to Best| Observations |
|----------------|---------------| -------------|--------------|
| Basic Order | 4257.6 |3206 |  Moderate performance with relatively slow convergence. Maintains good balance between exploration and exploitation |
| PMX | 4173.3 | 3131 | Best performing crossover operator with shortest distance achieved. Good preservation of relative positions between cities|
| Edge Recombination | 4272.74 | 2593 | Fastest convergence among all operators but slightly worse final distance than PMX. Good at preserving adjacency information between cities|
| Cycle Crossover | 4654.5 | 3662 | Worst performance in terms of both distance and convergence time. May be too restrictive in preserving absolute positions|

 

### Key Findings and Observations

1. **Selection Methods**:
   - Tournament selection led to faster convergence and better fitness scores compared to basic Roulette Wheel and Rank-Based selection.

2. **Mutation Impact**:
   - Inversion mutation at a rate of 0.3 produced the best results, outperforming both higher and lower rates.
   - Higher mutation rates (0.5-1.0) did not yield improved results, likely due to excessive path disruptions.
   - Scramble mutation showed consistently poor performance, possibly due to lack of directional improvement.

3. **Crossover Effects**:
   - PMX crossover produced the shortest routes, likely due to effective preservation of city relative positions, which helps maintain local substructures.
   - Edge Recombination performed well in convergence speed but fell slightly short on final distance.
   - Cycle Crossover was too restrictive, yielding the worst results among crossover methods.

### Best Configuration Found

```python
Best Configuration:
- Selection Method: Tournament Selection (size=3)
- Mutation Type: Inversion
- Mutation Rate: 0.3
- Crossover Type: PMX
- Best Distance Achieved: 4173.3

