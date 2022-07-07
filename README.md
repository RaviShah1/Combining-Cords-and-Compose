# Combining-Cords-and-Composer

## Observations

- 

## Model Results


## Overview

In this repository, I am documenting the results of my experiments to effectively combine decile cords with mosaicML composer.

**Resources:**

https://github.com/decile-team/cords - Subset selection strategies for efficient training of machine learning models (2x -3x)

https://github.com/mosaicml/composer - Algorithmic improvements that improve the efficiency of training deep neural networks (2x - 3x)

https://github.com/libffcv/ffcv - Implemented a faster version of data loaders by introducing a new data format that significantly improved the training speed. (5x)

**Goal:**

Approaches targeted at efficiency in all the above repositories complement each other. While adopting any individual approach, we can attain speed-ups in the range of 2x - 5x, which is significant, but we are still missing out on even better speed-ups that could be achieved by combining all the above approaches. The fundamental goal of this project is to efficiently combine CORDS, COMPOSER, and FFCV and do a detailed benchmarking on the possible speed-ups on standard datasets like CIFAR10, CIFAR100, and ImageNet.

**Tasks:**

1. Combine methods from the composer with CORDS and get some tutorial notebooks showing how to combine them.

2. Run some detailed benchmarks on what methods from COMPOSER and subset selection strategy from CORDS can be used to achieve the best speed up on the CIFAR10 dataset. (Finding the best methods composition and subset selection strategy)

