# GENETIC ALGORITHM
Genetic Algorithms are search and optimisation algorithms that are based on theory of evolution. It is a derivative free, random approach that 
aims that finding the optimal value. Here we are using Genetic Algorithm to find the top N features in a dataset.

## Dataset Used
Breast Cancer Wisconsic(Diagnostic) Dataset(https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29)

## Fitness Function 
Cross validation F1 score from a MLPClassifier() model trained on the solution subset.

## Stopping Criteria
Upper limit on the variance of fitness values in a population
