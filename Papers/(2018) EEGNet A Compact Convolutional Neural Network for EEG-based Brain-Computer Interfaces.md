#paper that first proposed [[EEGNet]] network design, a deep [[Convolusional Neural Network]] for BCI applications
Great paper, explains both in detail and in an understandable way for the less NN savvy.

Tested on multiple ERPs:
1. Visual [[P300]] response
2. Error-related negativity responses (ERN)
3. Movement related cortical potentials (MRCP)
4. Sensory motor rhythms (SMR)

Also covers how to interpret the model to figure out learned features

https://github.com/vlawhern/arl-eegmodels
Link to models (CC0)

## Introduction
Outlines 5 stages of BCI processing (L. F. Nicolas-Alonso and J. Gomez-Gil, “Brain computer interfaces, a review)
1. Data collection
2. Signal processing
3. Feature extraction
4. Classification - "where a decision is interpreted from the data"
5. Feedback - "where the result of that decision is provided to the user"

Supposedly mimics EEG feature extraction methods such as "optimal spatial filtering" and "filter-bank construction" using "Depthwise and Separable convolutions"

## 2.1 Materials and Methods

| Paradigm | Type        | Filter   | Subjects | Trials/Sunj | Classes | Imbalance |
|----------|-------------|----------|----------|-------------|---------|-----------|
| [[P300]]     | ERPs        | 1-40Hz   |       15 | ~2000       |       2 | 5.6:1     |
| ERN      | ERPs        | 1-40Hz   |       26 | 340         |       2 | 3.4:1     |
| MRCP     | ERP/Osc     | 0.1-40Hz |       13 | ~1100       |       2 | No        |
| SMR      | Oscillatory | 4-40Hz   |        9 | 288         |       4 | No        |

## 2.2 [[EEGNet]] Compact CNN Architecture

"Compact" refering to comparatively fewer parameters than other designs
Dropout: Uses 0.5 for "within-subject" classification to avoid overfitting
         Uses 0.25 for cross-subject classification "as the training set sizes are much larger"
Etc

**BLOCK 1**
      F_{1} - Number of 2D convolutional filters of size (1, kernLength). Filter length is half of the sample rate
	    All convolutions are 1 dimensional
	    kernLength default = half Fs, 64
            - Number of feature maps output at different band-pass frequencies

D - Depth, controlls number of spatial features to learn for each feature map

DropoutRate - Self explanatory; authors suggest 0.5 for single participants, 0.25 for cross participant.

**BLOCK 2**
F_{2} - Number of pointwise (1,1) Convolutions applied after first performing Separable Convolution
        Authors use F_2 = F_1 * _D_

Compares against DeepConvNet and ShallowConvNet
ShallowConvNet designed for Oscillatory datasets, not always a fair comparison
DeepConvNet designed as general-purpose

