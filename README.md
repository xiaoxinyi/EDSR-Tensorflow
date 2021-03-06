# EDSR Tensorflow Implementation
An implementation of [Enhanced Deep Residual Networks for Single Image Super-Resolution](https://arxiv.org/pdf/1707.02921.pdf) written in tensorflow.

## Requirements
 - Tensorflow
 - scipy
 - tqdm
 - argparse

## Installation
 `pip install -r requirements.txt`

## Training
In order to train, you'll have to do a few things...
 - Download a dataset of images (due to my computational limitations, I've used General-100)
 - Place all the images from that dataset into a directory under this one
 - run `python train.py --dataset data_dir` where data_dir is the directory containing your images

## Training details
As I've mentioned before, I'm currently faced with some computational limitations, so this
caused me to do a few things differently than what is mentioned in the paper. One of the
more important changes I've made was using the General-100 dataset, because it's much smaller.
I've also trained a network with less layers than the original baseline model as was described 
in the paper. This, however, can still be done using my code by adjusting some training parameters.
I've trained by taking the center 100x100 pixels of each image in General-100, and shrinking them down to 50x50.
I then trained an EDSR to resize the 50x50 pixel images back to 100x100. Currently, I use 80% of the
dataset as a training set and 20% as a testing set. I trained the EDSR over 1000 iterations using Adam optimizer

## Results
| Original image | Shrunk image | EDSR Output |
| -------------- | ------------ | ----------- |
| ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/correct0.png "Original")          | ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/input0.png "input")         | ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/output0.png "shrunk")        |
| ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/correct1.png "Original")          | ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/input1.png "input")         | ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/output1.png "shrunk")        |
| ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/correct2.png "Original")          | ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/input2.png "input")         | ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/output2.png "shrunk")        |
| ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/correct3.png "Original")          | ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/input3.png "input")         | ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/output3.png "shrunk")        |
| ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/correct4.png "Original")          | ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/input4.png "input")         | ![alt-text](https://github.com/jmiller656/EDSR-Tensorflow/blob/master/results/output4.png "shrunk")        |

## Remarks
It seems my output images have some deconvoltion artifacts (especially around the border). I plan on finding the reason for this. It likely could be a mistake I've made.

## Future work
- Add MDSR implementation
- Train and post results on a larger model and dataset
