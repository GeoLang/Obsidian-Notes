The first #paper to propose [[xDAWN]] for BCI
Applys [[xDAWN]] to [[BCI Speller]]  paradigm and uses Bayesian Linear Discriminant Analysis (BLDA)

### Page 2

Authors mention BCI paradigms where the user actively control the modulation of brain waves [6] and [7]. Look into this?
Possible future TODO will be check out papers [6] and [7]

### Page 6
Authors break down [[xDAWN]] algorithm steps at the end of section 2, but it still has *alot* of Maths
   
Experiment is based on the BCI Competition 2003 - Speller data set and uses BCI2000 software
   
Pre-processing steps explained

Authors explain the preprocessing steps they used for their experiments.

Data filtered with 4th order forward-backward Butterwords Bandpass filter at 1-20Hz
Each sensor was normalised to mean zero and standard deviation of 1
"The temporal length of the synchronous response was chosen to be 1 second"

- (Is that a wordy way of saying 1 second epochs?)

### Page 7
Authors explain why they used Bayesian Linear Discriminant Analysis

Authors justify BLDA because it is *fully automatic*.
No hyper-parameters need to be adjusted with BLDA.

### Page 8
Figure 5 6 and 7 compare PCA, [[xDAWN]], and ICA as well as the default (reference)

Figure 8 shows [[xDAWN]] performing better than ICA and PCA, even with minimum number of repetitions

### Page 9
[[xDAWN]] improves performance, so long as at least 2 components are selected and as few as 4 could suffice

In fact, 4 is recommended.
