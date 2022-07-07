# Combining-Cords-and-Composer

## Observations

- when training in colab/colab pro, it is important to note that each session assigns a different GPU. Thus, for every session, I run tests against a cords only baseline and compare the results relative to the baseline to avoid gpu influencing the results
- for some reason, the torchvision resnet18 tends to be faster than the resnet18 in cords utils
- the composer channels first function consistently slows down training on resnet18 (almost 9 second slow down per epoch) - should not use
- the default composer function parameters may not be optimal on smaller models as they benchmarked results on models such as resnet101
- it is important that some composer functions are applied in the train loops (as applying them in the evaluation loop as seen in the example nb provided to me will not improve performance)
 
 note on measuring speed up:
- cords speeds up the per epoch training time because it uses data selection strategies
- some composer functions(e.g. blurpool and squeeze_excite) slow down the per epoch training time slightly but improves accuracy faster thus speeding up overall training time
- as a result, to measure the success of an experiment, we must not only look at the time it takes to train one epoch, but also the number of epochs to reach an accuracy (e.g. when combining cords and composer, the training time / epoch may be slighly slow than a cords only baseline; however, it should take fewer epochs before the model accuracy converges)

to be completed:
- use the completed baseline experiments on glister + indivuals composer functions to figure out the optimal configuration of cords and composer functions
- test on larger models and test different composer parameters for smaller models
- create clear example/tutorial notebooks with the optimal results

## Experiment Results

- you can find several notebooks with code in experiments folder
- I have run other experiments, I will add code and documentation to this repo later - all important info is listed in observations

ResNet18 on Cifar10 dataset (30 epochs) - Session 1

<table>
  <tr>
    <td>Method</td>
    <td>sec/epoch</td>
    <td>total time (hrs)</td>
    <td>epoch val acc > 0.7</td>
  </tr>
  <tr>
    <td>GLISTER only</td>
    <td>8.3552</td>
    <td>0.0696</td>
    <td>25</td>
  </tr>
  <tr>
    <td>GLISTER+Blurpool</td>
    <td>8.6463</td>
    <td>0.0721</td>
    <td>24</td>
  </tr>
  <tr>
    <td>GLISTER+Squeeze_Excite</td>
    <td>9.6993</td>
    <td>0.0808</td>
    <td>24</td>
  </tr>
  <tr>
    <td>GLISTER+Channels_Last</td>
    <td>17.2986</td>
    <td>0.1442</td>
    <td>22</td>
  </tr>
</table>

## Overview

In this repository, I am documenting the results of my experiments to effectively combine decile cords with mosaicML composer.

**Resources:**

- https://github.com/decile-team/cords - Subset selection strategies for efficient training of machine learning models (2x -3x)
- https://github.com/mosaicml/composer - Algorithmic improvements that improve the efficiency of training deep neural networks (2x - 3x)
- https://github.com/libffcv/ffcv - Implemented a faster version of data loaders by introducing a new data format that significantly improved the training speed. (5x)

**Goal:**

- Approaches targeted at efficiency in all the above repositories complement each other. While adopting any individual approach, we can attain speed-ups in the range of 2x - 5x, which is significant, but we are still missing out on even better speed-ups that could be achieved by combining all the above approaches. The fundamental goal of this project is to efficiently combine CORDS, COMPOSER, and FFCV and do a detailed benchmarking on the possible speed-ups on standard datasets like CIFAR10, CIFAR100, and ImageNet.

**Tasks:**

1. Combine methods from the composer with CORDS and get some tutorial notebooks showing how to combine them.

2. Run some detailed benchmarks on what methods from COMPOSER and subset selection strategy from CORDS can be used to achieve the best speed up on the CIFAR10 dataset. (Finding the best methods composition and subset selection strategy)

