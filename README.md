# Combining-Cords-and-Composer

## Overview

In this repository, I am documenting the results of my experiments to effectively combine decile cords with mosaicML composer.


## Observations

- 

## Model Results


## Overview

Resources:

https://github.com/decile-team/cords
Subset selection strategies for efficient training of machine learning models (2x -3x)

https://github.com/mosaicml/composer
Algorithmic improvements that improve the efficiency of training deep neural networks (2x - 3x)

https://github.com/libffcv/ffcv
Implemented a faster version of data loaders by introducing a new data format that significantly improved the training speed. (5x)

Goal:

Approaches targeted at efficiency in all the above repositories complement each other. While adopting any individual approach, we can attain speed-ups in the range of 2x - 5x, which is significant, but we are still missing out on even better speed-ups that could be achieved by combining all the above approaches. The fundamental goal of this project is to efficiently combine CORDS, COMPOSER, and FFCV and do a detailed benchmarking on the possible speed-ups on standard datasets like CIFAR10, CIFAR100, and ImageNet.
