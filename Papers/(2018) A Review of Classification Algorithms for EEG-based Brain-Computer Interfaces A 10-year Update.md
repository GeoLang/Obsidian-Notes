#paper
A complete review of classification algorithms for [[ERP]]s over the last 10 years
Also authored a paper 10 years prior with the review until that point.

### Notes on supervised spatial filters
Authors discuss a couple of supervised spatial filters. They specifically note:
- Common Spatial Patterns ([[CSP]])
[[xDAWN]]
Fisher Spatial filters

### Paper notes some BCI studies have improved performance by combining features
There is a number of cited papers that combine multiple features (like time series and band power) to improve performance. Also combining band power and connectivity

### Discussion of [[Pearson Correlation]]
Needs more reading...

### Discusses "Wrapper" and "Embedded" feature selection
These are classifiers in their own right that select features from EEG

The authors examples are decision trees and multilayer perceptrons

### Authors note maximum Relevance Minimum Redundancy (mRMR) and R^2 feature selection
Note - This is also as far as I read so far.

# Paper overview

This paper covers BCI applications as a whole, and as a result some of the content is not entirely relevant but still important. Specifically, the paper will discuss alot of motor imagery BCI paradigms, and like most BCI papers will also primarily cover Visual P300 speller paradigms.

The authors even note that most researchers focus on this paradigm primarily because of the high quality BCI competition dataset that is readily available, and as such is perfect for comparing novel classification paradigms as you have so much existing literature to compare to.

## 1. Introduction

Exactly as you'd expect, a brief overview of the domain before diving into the important stuff

## 2. Feature extraction and selection, and performance measures in brief
### 2.1. Feature Extraction

An overview of some methods of feature extraction, specifically for use in BCI applications.

The authors mention some methods I have yet to explore. In brief these are

- Spatial Filtering
	- Laplacian Filters
	- Inverse solution-based spatial filtering (Worth investigating further, 
==[18, M. Besserve, J. Martinerie, and L. Garnero. Improving quantification of functional networks
with EEG inverse problem: Evidence from a decoding point of view. Neuroimage, 2011.]
[101, B. Kamousi, Z. Liu, and B. He. Classification of motor imagery tasks for brain-computer interface
applications by means of two equivalent dipoles analysis. IEEE Transactions on Neural Systems
and Rehabilitation Engineering, 13(2):166–171, 2005.]
[124, J. T. Lindgren. As above, so below? Towards understanding inverse models in BCI. Journal of Neural Engineering, 2017]
[173, Q. Noirhomme, R. Kitney, and B. Macq. Single trial EEG source reconstruction for brain-computer interface. IEEE Transactions on Biomedical Engineering, 55(5):1592–1601, 2008.]==)
	- ICA/PCA
	- Common Spatial Patterns ([[CSP]])
		- Additionally, Filter Bank [[CSP]]
NB: which the authors discuss in great detail in later sections as one of the more effective state-of-the-art paradigms
- Connectivity Features
	- Spectral Coherence
	- Phase Lokcing
- Covariance Matrices / Tensors
The authors describe these as "arrays and multi-way arrays, with two or more dimensions"

Combining multiple features often leads to higher accuracy, but leads to an increase in dimensionality.

### 2.2. Feature Selection

There will almost always be redundant features that should be removed to improve results

Filter methods of feature extraction measure the relationship between a feature and the target class using "the coefficient of determination" which is "the square of the estimation of the [[Pearson Correlation]] coefficient" and can be used for feature ranking.

Paper ==[111, D. Krusienski, E. Sellers, F. Cabestaing, S. Bayoudh, D. McFarland, T. Vaughan, and J. Wolpaw. A comparison of classification techniques for the P300 speller. Journal of Neural Engineering, 3:299–305, 2006.]== shows the use of feature selection to improve accuracy in stepwise [[Linear Discriminant Analysis]].

There's also a look at using [[SVM]] for channel selection in ==[115, T. Lal, M. Schr¨oder, T. Hinterberger, J. Weston, M. Bogdan, N. Birbaumer, and B. Sch¨olkopf. Support vector channel selection in BCI. IEEE TBME, 51(6):1003?1010, 2004.].==

Finally, the authos also note a "P300-based feature selection" in ==[201, B. D. Seno, M. Matteucci, and L. Mainardi. A genetic algorithm for automatic feature extraction in P300 detection. In IEEE International Joint Conference on Neural Networks, pages 3145–
3152, June 2008.]==, but do not explain it at all so [201] will need to be read.

### 2.3. Performance Measures

**Classification accuracy is only a valid metric if classes are balanced**, otherwise the confusion matrix of Kappa metric are more useful metrics ==[66, M. Fatourechi, R. Ward, S. Mason, J. Huggins, A. Schlogl, and G. Birch. Comparison of evaluation metrics in classification applications with imbalanced datasets. In International Conference on Machine Learning and Applications (ICMLA), page 777782. IEEE, 2008.]==.

Authors mention ==[212, E. Thomas, M. Dyson, and M. Clerc. An analysis of performance evaluation for motor-imagery based bci. Journal of neural engineering, 10(3):031001, 2013]== for a review of evaluation strategies for BCI contexts. **THIS IS A MUST READ**

## 3. Past methods and current challenges
### 3.1. A brief overview of methods used 10 years ago

I mean... the title of this paper tells you you can just look at the last review these authors wrote for much *much* more detail.

Briefly, list of some of the more interesting methods noted

- [[SVM]]
- [[Linear Discriminant Analysis]]
- Neural Networks
	- Multi-Layer Perceptron (MLP)
One or 2 hidden layers
	- Learning Vector Quantization (LVQ)
- Hidden Markov Models (HMMs)
- k-Nearest Neighbour (kNN)
- Combinations (Boosting, Voting, Stacking), usually the best performing

### 3.2. Challenges faced by current EEG signal classification method

- Signal-noise bad
- Headset drift between trials
- Headset changes between subjects
- Limited training data
- Low reliability/performance of BCIs
(What the author means by this I don't know)

There's a number of citations for this section grouped together, which are
[202, 80, 109, 164, 145, 56]

## 4. New EEG classification methods since 2007
## 4.1. Adaptive classifiers
### 4.1.1. Principles

Briefly, an overview of adaptive classifiers in both supervised and unsupervised adaptations, meaning if the classifier has knowledge of the class labels or not.

Supervised BCI can be used in situations where the user is getting immediate feedback from the classifier in an online system. The user responses act as a class. This cannot be done unsupervised.

### 4.1.2. State-of-the-art

A couple are discussed

- [[Linear Discriminant Analysis]]
- Quardratic Discriminant Analysis (QDA)
- Adaptive [[Linear Discriminant Analysis]]
- Adaptive [[SVM]]
- Adaptive [[CSP]] ==[247, Q. Zhao, L. Zhang, A. Cichocki, and J. Li. Incremental common spatial pattern algorithm for BCI. In IEEE International Joint Conference on Neural Networks (IJCNN), pages 2656 –2659, june 2008.]==
==[204, X. Song, S.-C. Yoon, and V. Perera. Adaptive common spatial pattern for single-trial EEG classification in multisubject BCI. In International IEEE/EMBS Conference on Neural Engineering (NER), pages 411–414. IEEE, 2013.]==
- adaptive [[xDAWN]] ==[227, H. Woehrle, M. M. Krell, S. Straube, S. K. Kim, E. A. Kirchner, and F. Kirchner. An adaptive spatial filter for user-independent single trial detection of event-related potentials. IEEE Transactions on Biomedical Engineering, 62(7):1696–1705, 2015]== (Should read this, xDAWN isn't a classifier)

Unsupervised

- LDA and Gaussian Mixture Model (GMM)
- Fuzzy C-means
- [[SVM]] [122. 151] and validated in [81]

Adaptive classifiers could achieve better than chance accuracy on a BCI paradigm (which isn't saying much?)

Adaptive methods are computationally expensive, with the authors giving the example of having to retrain an SVM from scratch in real time. This makes using them in an online scenario prohibitively slow.

## 4.2. Classifying EEG matrices and tensors
### 4.2.1. Riemannian geometry-based classification

This is complex.

As an alternative to spatial filters and feature selection, map the raw EEG onto a geometrical space with a "suitable metric?" (none of which are specified in this review which is a shame). Once mapped the data can more easily be manipulated for "averaging, smoothing, interpolating, extrapolating, and classifying".

There's alot of maths I don't really understand here here's a summary of the pros and cons section:

Riemannian geometry optimises spatial filters and the classifier 
simultaneously, which can provide better classification performance. However, they are also computationally expensive.

### 4.2.3. Feature extraction and classification using tensors

Tensors represent EEG as multi-dimensional arrays.

Obviously EEG is already represented in a multidimensional array of $$Space \times Time \times Frequency$$ but tensors can add multiple new dimensions. For example, a tensor can be a respresentation of $$Space \times Time \times Frequency \times Trial \times Subject$$ to combine multiple subject and trials into a single 5-dimensional tensor.

Special modified classifiers are needed to work on a tensor. The authors cite the examples of

- Tensor Support Machine
- Tensor Fisher Discriminant Analysis
- Higher Order Discriminant Analysis

There are some interesting examples presented that could be worth a read. ==[183, A.-H. Phan and A. Cichocki. Tensor decompositions for feature extraction and classification of high dimensional datasets. Nonlinear Theory and its Applications (NOLTA), IEICE, 1(1):37–68, 2010.]==

The authors note that tensor methods are still not mature so their application in themselves are novel but not quite there yet.

## 4.3. Transfer Learning

This doesn't need notes.

Reusing layer from other pretrained machine learning classifiers to improve the accuracy in your own applications.

Here is where the authors note that the most likely reason there's alot of applications of transfer learning to motor imagery paradigms is that there's BCI competition datasets available.

There's some interesting papers to note here;

Blankertz et al. ==[21, B. Blankertz, M. Kawanabe, R. Tomioka, F. Hohlefeld, V. Nikulin, and K.-R. M¨uller. Invariant common spatial patterns: Alleviating nonstationarities in brain-computer interfacing. In Advances in Neural Information Processing Systems 20, In . MIT Press, Cambridge, MA, 2008.]== which examined feature extraction before feeding data to an [[Linear Discriminant Analysis]] and proposes invariant [[CSP]] which can help. They found sparse features performed best. Should check *which* sparse features they used (sparce iCSP features? need definition). The following paragraph also suggests sparse features work well with inter-trial variability (moving cap between trials/subjects/days).

A notable quote from the start of section 4.3.3. 

> As reported in the above cited studies, transfer learning is instrumental in sessionto-session and subject-to-subject decoding performance. This is essential to be able to achieve a true calibration-free BCI mode of operation in the future, which in turn would improve BCI usability and acceptance.

Transfer learning can help produce calibration free BCI [46, 15, 158, 74].

## 4.4. Deep Learning

Review discusses Convolutional Neural Networks and Restricted Boltzmann machines.

The first paper to use [[Convolusional Neural Network]] for BCI was ==[32, H. Cecotti and A. Graser. Convolutional neural networks for P300 detection with application to brain-computer interfaces. IEEE Transactions on Pattern Analysis and Machine Intelligence, 33(3):433–445, 2011.]==, and authors note that each study was only tested offline. 

[234] obtained good performance with a [[Deep Belief Network]] and feature selection that isn't mentioned here but didn not compare to state-of-the-art methods (the authors say FBCSP in this case).

==[207, I. Sturm, S. Lapuschkin, W. Samek, and K.-R. M¨uller. Interpretable deep neural networks for single-trial EEG classification. Journal of Neuroscience Methods, 274:141–145, 2016.]== is a must-read paper that proposes a [[Deep Belief Network]] and methods to inrerpret the network and it's decision making to get insight into the neurophysiological causes of classifier mistakes.

## 4.5. Other new classifiers

Nothing that interesting here tbh.

# 5. Discussion and guidelines

> • Deep learning networks do not appear to be effective to date for EEG
signals classification in BCI, given the limited training data available. Shallow
convolutional neural networks are more promising.
> • Shrinkage Linear Discriminant Analysis (sLDA) should always be used instead of classic LDA, as it is more effective and more robust for limited training data.
> • When very little training data is available, transfer learning, sLDA, Riemannian Minimum Distance to the Mean (RMDM) classifiers or Random Forest should be
used.
> • When tasks are similar between subjects, domain adaptation can be considered for enhancing classifier performance. However, care should be taken regarding the effectiveness of the transfer learning, as it may sometimes decrease performance.
> • Riemannian Geometry Classifiers (RGC) are very promising, and are considered the
current state-of-the-art for multiple BCI problems, notably Motor Imagery, P300 and SSVEP classification. They should be further applied and further explored to increase their effectiveness.
> • Tensor approaches are emerging and as such may also be promising but currently require more research to be applicable in practice, online, and to assess their
performance as compared to other state-of-the-art methods.