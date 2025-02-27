# iCaRL Enhanced Exemplar Selection

> **Note**: This repository contains the source code for the research paper titled "Class-Incremental Learning Enhanced:
> Assessing New Exemplar Selection Strategies in the iCaRL Framework", presented at SYNASC 2024 and accepted for 
> publication in the IEEE post-proceedings. This project was also used as the final project for my Master's degree, 
> specializing in Artificial Intelligence and Distributed Computing, at West University of Timișoara (2022/2023 to 
> 2023/2024).

## Week 19 (09.02 - 09.08)

We have modified the code to measure the execution time of each task (including the 
exemplar selection part separately). In the end, we output the overall execution time 
of the executed algorithm. Furthermore, we have rerun all the experiments and redone 
the graphical representation for the results in the notebooks.

## Week 18 (06.24 - 06.30)

This week (or more precisely today), we refactored how the density selection 
criterion was implemented, which required us to rerun the experiments. Additionally,
we have implemented a visualization for all exemplar selections. Lastly, we made 
small refactorings to the folder and file structures of the repository.

## Week 17 (06.17 - 06.23)

We have made several modifications this week: adjusted the code to handle various 
datasets such as MNIST, FashionMNIST and Food-101, not just CIFAR-100. Various 
experiments were conducted with these datasets, and the results were later visualized. 
Another significant modification was the addition and visualization of the results 
from an experimental analysis conducted last year with the assistance of the 
publicly available Framework for Analysis of Class-Incremental Learning (FACIL).

## Week 16 (06.10 - 06.16)

We have partially modified the code in the `ResNet32` file, now named
`ResNet32iCaRL`. We simplified the code by using functions from the original 
PyTorch package and made some small changes to how the layers are defined in the 
architecture of the neural network (without affecting its functionality). 
Additionally, several experiments were run to test our exemplar selection methods 
with 5 and 20 tasks.

## Week 15 (06.03 - 06.09)

This week, we have finalized the refactoring of the code. Furthermore, we have 
added a `requirements.txt` file, which helps make the code more reproducible by 
specifying the exact versions of the packages we used. Lastly, we have created a 
logging system (different from simple printing in the terminal). This is a key 
part to ensure our results can be tracked and compared later on.

## Week 14 (05.27 - 06.02)

This week, we found several possible improvements, especially in the different 
selection criteria parts of the code. We were able to achieve this while still 
continuing with the refactoring process. Next week, we will focus our coding efforts
primarily on the `select_exemplars_by_density` and `select_exemplars_with_kmeans` 
functions. We'll leave the `ResNet32` class for last, tackling it only if time
permits.

## Week 13 (05.20 - 05.26)

We have continued with the refactoring of the code. In addition to enhancing the 
readability of the code, we have also managed to make some minor optimizations. We 
will continue to refactor the remaining two functions: `select_exemplars_by_density`
and `select_exemplars_with_kmeans` (we have already started the latter but need to 
finish it). Furthermore, we will try to rewrite/optimize the `ResNet32` class.

## Week 12 (05.13 - 05.19)

This week, we have refactored/rearranged the code in a manner that almost all the 
functions are in their own files. This makes the code easier to read and more 
manageable. Regarding the results, as we have changed the model from ResNet34 
to ResNet32, they have improved significantly:

original = [0.5570, 0.4213, 0.3248, 0.3000, 0.3112, 0.2744, 0.2578, 0.2491, 0.2328]

kmeans = [0.6060, 0.4640, 0.3855, 0.3540, 0.3510, 0.3234, 0.3014, 0.2887, 0.2650]

median = [0.5815, 0.4140, 0.3245, 0.2962, 0.3037, 0.2723, 0.2553, 0.2583, 0.2348]

density = [0.5745, 0.4170, 0.3223, 0.2976, 0.2958, 0.2617, 0.2491, 0.2518, 0.2387]

## Week 11 (05.06 - 05.12)

We have replaced the ResNet model with our own implementation. Our implementation 
not only simplifies the code but also exponentially improves the inference time 
when extracting features to determine the mean of the features for each class, 
subsequently aiding in the selection of exemplars that best represent the class
(define_class_means).

## Week 10 (04.29 - 05.05)

This week, we cleaned up all the unused files from the original PyCIL framework, 
in which we conducted all the preliminary proof of concept experiments. Currently, 
we have two implementations: the `class-incremental-learning` and 
`class-incremental-learning-2` folders. Most likely, we will continue with the 
aforementioned implementation as its implementation and hyperparameters are 
closer to the original iCaRL paper implementation.

## Week 9 (04.22 - 04.28)

We have reorganized and refactored the structure of the folders and files, as 
well as some parts of the code, to make them more readable and structured. Next
week, we will continue with the refactoring, as our ultimate goal is to make the 
code as easily understandable as possible.

## Week 8 (04.15 - 04.21)

This week, we reimplemented the iCaRL method from scratch in order to reproduce 
results that are even closer to those of the original paper. As we can see, the 
average accuracies per task have increased compared to our first implementation. 
The following two lists represent the accuracies (using the nearest mean 
classifier) for the first five tasks in a 10-task run:

Herding: [0.7860, 0.5415, 0.4210, 0.3320, 0.3000]

K-Means: [0.7850, 0.5760, 0.4537, 0.3623, 0.3266]

## Week 7 (04.08 - 04.14)

The main contribution to the codebase this week was the creation of a logging 
system that not only displays results in real time in the console but also saves 
the outputs to a file if the `LOG_TO_FILE` constant is set to `True`. Additionally,
we have adjusted the hyperparameters according to the original iCaRL method in 
order to reproduce the results of the approach. These settings are actually the 
final results from last week's attempts (Week 6). Furthermore, we have corrected 
some of the errors and warnings that appeared during the runtime of the exemplar 
selection using the K-Means clustering algorithm.
## Week 6 (04.01 - 04.07)

This week, there were no significant changes made to the code because we focused 
more on trying to reproduce the results from the original iCaRL method's paper. 
These attempts mainly involved adjusting the hyperparameters of our model to 
match those specified in the iCaRL paper.

## Week 5 (03.25 - 03.31)

We have implemented two new methods for exemplar selection:

**Median Selection**:
This method selects exemplars based on their proximity to the median of the class 
features instead of the mean. This can be more robust to outliers compared to the 
mean-based selection.

**Density-Based Selection**:
Select exemplars based on a density measure, where exemplars are chosen from dense 
regions of the feature space, assuming that these regions represent the class more 
accurately.

Using these two new methods, we will conduct several experiments to see if we can 
achieve higher accuracies.

## Week 4 (03.18 - 03.24)

We have implemented our own method for exemplar selection using K-means clustering;
however, this function is currently not in use. Furthermore, we have made all the
necessary modifications to ensure the reproducibility of our experiments. This
includes setting the seeds for all the packages we have used.

## Week 3 (03.11 - 03.17)

We have continued to write our own implementation of the iCaRL method. The current 
state of the code theoretically includes all components of iCaRL, but we have
encountered some issues. More precisely, when we use the nearest-mean-of-exemplars, 
the classification is far worse than it is with the base neural network. The 
execution time is also slow, so it could be improved, but it is not a must.

## Week 2 (03.04 - 03.10)

We have continued to write our own implementation of the iCaRL method. The current 
state of the code does not yet contain parts of the iCaRL method, nor does it 
include any other class-incremental learning approach. The code we have written 
reflects how a machine learning model (ResNet18, in our case) would behave if the 
data were to come sequentially. This is the foundation upon which any 
class-incremental learning method can and will be implemented. **The current accuracy
for 5 tasks (each task containing 20 classes) on the CIFAR-100 dataset is as follows:
[36.6, 17.0, 9.83, 9.24, 6.85]. We will use these values as an approximate baseline 
for future implementations and testing.**

## Week 1 (02.26 - 03.03)

We have changed the class-incremental learning framework that we have used for 
experiments until now, as it did not contain the FOSTER method, which we will 
most likely focus on if we cannot achieve the desired results with the modification
of the iCaRL approach. Regarding the iCaRL approach, we have deprecated the 
modification we made in the previous semester, in which we assigned weights to each
of the exemplars based on Pearson’s correlation coefficient and used those weights
to calculate each of the representations of exemplars.

In our new approach, we aim to modify the iCaRL method in a way to choose exemplars
that best represent the distribution of the data within each class, potentially 
offering a more diverse and representative set of exemplars. To do this, to select
exemplars, we have chosen to use the clustering algorithm k-means. The results can
be seen in the 'results.txt' file but can be summarized with the following lines:

**Original iCaRL method accuracy for 3 tasks: [29.7, 16.05, 14.97]**

**K Means iCaRL method accuracy for 3 tasks: [29.7, 16.2, 15.07]**

As we can see, our approach not only achieved the original iCaRL performance but 
even surpassed it by some decimals (0.15, respectively 0.10). We will continue 
trying to improve this approach while also trying new ones.

**Author**: Erik Zsolt Varga
