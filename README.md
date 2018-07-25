# K-MEANS CLUSTERING

## Overview

Implementation of a simple but powerful clustering algorithm for 2D ('x' 'y') points . Simple and optimal for most data structures that are crawled iteratively, large list searches are avoided, some calculations are strict, and so on. Additionally, the total time of program operation (including IO operations, input parsing and output formatting), and how many iterations the algorithm has completed is measured. Finally, an intra-cluster sum of squares is calculated - the sum of the squares of the distances between each point in a cluster and the cluster center (for all clusters in total). This amount actually tries to minimize the algorithm, but may not reach a global minimum depending on the selected start centers (NP-hard is the task of finding a global minimum). For convenience, the minimum reached is displayed on the standard output, along with the number of iterations and program runtime.

if using method two \#2
* The 'clock` package (https://hackage.haskell.org/package/clock) is required to accurately measure the time (without it the code, of course, does not compile).

One of the most significant and effective tricks is shown in the 'reClusterize' function, which with a linearly iterative and strict crawling of the complete list of points calculates for each of them its new cluster and at the same time monitors whether one changes it , and returns this information as a `Bool` into an ordered pair with the resulting list of points. The same technique for retrieving all the required information with only merged and strict list crawling is also used in the mean and mapAndLength functions.

On the other hand, the `groupToClusters` function can be greatly improved as it is also invoked once in each iteration, and it shines with simplicity rather than efficiency. There are other features that can be optimized in ways the compiler simply can not guess, and may choose different data structures (such as unboxed lists and / or vectors), but these are long-distance goals for improvement. In any case, this is a proof of concept.

The code can be executed with the 'kmeans :: String -> Int -> String -> IO () `function, which gets three arguments:

* filename of the input data - a text file in which each row contains the coordinates of a single point separated by an empty space
* Number of search clusters
* file name for output data - clustering result.

## Execution

__METHOD \#1__
The easy way(stack):
1. Clone the repository

2. Build the project:
> - stack build

3. Execute the program 
> - stack exec k-means-exe

__METHOD \#2__
Of course, for faster execution, the code can be compiled into a executable, which at startup gets three similar command-line arguments:
```
> - ghc app/Main.hs
> - . \ k-mean.exe example/input.txt 4 example/output.txt --> General systax (program inputfile clusters outputfile)
```
Arguments are not validated, only their number is tracked (at least three, all after the third are ignored). The only validation of input data is whether the number of desired clusters does not exceed the amount of data.

The file [`input.txt`](./input.txt) serves as an example input and contains 1249 points without any particular internal structure 

## Runtime
On my non-dedicated laptop clustering in 4 clusters takes an average of ~ 0.3 seconds and in 10 clusters - about 0.7 seconds.

## Results
The result of execution are stored as a text file named output.txt inside the directory example.

## Report
View pdf in Documentation folder.
