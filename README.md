# GENETIC ALGORITHM
Genetic  algorithms are  search  and  optimization algorithms based on the principles of natural evolution, first introduced by John Holland  in  1970. It is majorly used as an optimization technique to find the best possible output. It tries to mimic the concept of human evolution by modifying a set of individuals called a population, followed by a random selection of parents from this population to carry out reproduction in the form of mutation and crossover. This produces a new generation and the process continues till the stopping condition is met. 

The whole idea behind the algorithm is based on the fact that ‘good’ parents produce ‘good’ offspring which causes the algorithm to converge to an optimal value over time. Since it is a randomized algorithm, we can expect it to converge to the global optimal value. 

Here we are using Genetic Algorithm to find the top N features in a dataset.

## Dataset Used
Breast Cancer Wisconsic(Diagnostic) Dataset(https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29)

## Fitness Function 
Cross-validation F1 score from an MLPClassifier() model trained on the solution subset.

## Stopping Criteria
Upper limit on the variance of fitness values in a population

## Steps carried out in the algorithm
1. Initialising the population:  A very large population size will cause the algorithm to slow down, while a very small size will not show diversity. According to the literature, the optimal size roughly equals 1.5 times the input layer. Hence, we take population size to be 1.5N. Initialization is done by taking an array having a length equal to the maximum number of features (N_max). Since we want to find top N features, we randomly initialize N digits to 1 and the rest to 0.

2. Calculation of fitness value: The fitness value of each individual of the population is calculated. Here the fitness value is the f1 score obtained by the feature subset using a simple MLP model from sklearn library.

3. Reproduction: The initial population is then allowed to undergo reproduction which consists of forming a new population with the same size by selecting from members of the current population with a process that depends on their fitness values. We use Roulette Wheel Selection for selecting the parents wherein a circle is formed by using the cumulative normalised fitness values,  we then generate n random numbers between 0-1 where n is the size of the population. The individual corresponding to the generated normalised value is selected. 

4. Low intensity crossover: The selected parents are subjected to Two-point Crossover where two random bits with opposite. An overall probability is assigned to this process which indicates the chance of crossover for a given pair. A crossover rate of 0.65-0.80 is considered optimal. Here a crossover rate of 0.78 is chosen.


5. Mutation: After crossover, the population is subjected to mutation which involves flipping bits at random. Its probability is kept as low as 0.001 to preserve the integrity of the population by avoiding unnecessary randomness. In order to find the top n features, we carry out mutation by swapping a ‘0’ bit with ‘1’ bit. In this way, the number of features are preserved.

The mutated population is now checked with the stopping criteria, if it satisfies, then the algorithm stops, otherwise the procedure is repeated with the mutated population as the new population.


For more in-depth information checkout my medium article on the same - https://medium.com/@radhajayaraman11/feature-selection-using-genetic-algorithm-2f915d1349b0. If you like it, dont forget to clap! Thanks :)
