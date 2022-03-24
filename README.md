# Entropy-Based Binning

## Summary
The function here is designed for binning continuous independent variables, in the way minimizing total entropy of corresponding response.  
Also this function can plot the change of the entropy in the process.  
Test dataset is from: https://www.kaggle.com/rashikrahmanpritom/heart-attack-analysis-prediction-dataset

## Use guide
1. Make sure u put the test file into correct path, which is "sample_data/heart.csv" in google colab.  
2. If the response variable is not dummy, u shoud transfer it first.
3. The function here is designd for binary response only, if ur response is not binary, u should change the entropy base and revise the probability and entropy calculating on your own, which is not that difficult so I just skip the tutorial.

## Structure

Every round we will cut out two bins from a leaf node of binary tree in oeder to minimize entropy, then we insert these two bins under that node and these two bins will become new leaf nodes, recursively doing this process until the entropy is optimized, also we can set a threshold using bins count or information gained.

### Entropy
Using [scipy.stats.entropy]https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.entropy.html?highlight=entropy to calculate the entropy of every bin, and weight them according to the lenth of bin divided by total lenth of the data. Every round of bining it will find the binning method with most information gained, which is new entropy minus orginal entropy.  

Given a set of samples S, if S is partitioned into two intervals S1 and S2 using boundary T, the entropy after partitioning is:  
![image](https://user-images.githubusercontent.com/77425545/159634298-185c5311-4312-4871-8220-e8da7f3a536b.png)

### Binary tree
The binary tree is to store the data, every node is a double list containing independent and response variables, the root node means whole data and the leaf nodes mean the remaining bins in that time point, we use leaf nodes to do further bining every round.  

## Result
In this case, we set threshold as bins count is equal to 4 and keep it running till the entropy is optimized to draw the change of the entropy.  
The output is shown below:  
![image](https://user-images.githubusercontent.com/77425545/159637424-594ec42c-d734-485e-aabe-eaee34744aea.png)
