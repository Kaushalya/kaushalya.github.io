---
layout: post
title: ":books: Reading list - Compression of Deep Neural Networks"
excerpt: Deep neural network compression literature research organized chronologically.
categories:
  - Deep Neural Networks
comments: true
author: Kaushalya
pinned: true
published: true
category: blog
---
# Reading list - Compression of Deep Neural Networks

Here is a list some of the papers I had read as literature review for the ["CREST Deep"](https://www.jst.go.jp/kisoken/crest/en/project/1111094/1111094_07.html) project. This project is funded by Japan Science and Technology Agency (JST). Our goal is to make the DNN models smaller, so they take less disk space, but without having a significant impact on the accuracy.

[**Compression-aware Training of Deep Networks**](https://papers.nips.cc/paper/6687-compression-aware-training-of-deep-networks). Alvarez and Salzmann. NIPS 2017
{: .notice}
> This paper introduces a regularization term which encourages the parameter matrix of each layer to have low rank while training, thus improving low rank decomposition based compression techniques. Since explicitly minimizing the rank of a matrix is NP-hard, regularization term uses nuclear norm instead. Where, the nuclear norm is defined as summation of singular values of parameter matrix of a layer. In addition, group Lasso regularization term is introduced to reduce the number pf parameters further. Experiments of this paper are limited to _DecomposeMe_ network architecture, in which each convolutional layer is decomposed into two 1D kernels. Even though it is claimed that a decomposed ResNet-50 network is also used, the results are not reported in the paper.

**Do Deep Convolutional Nets Really Need to be Deep and Convolutional?** Gregor Urban et al. ICLR 2017
{: .notice}
> This can be considered as a response to the NIPS 2014 paper "Do deep nets really need to be deep?" (Ba and Caruana, 2014). They train shallow Colnvolutional Neural Networks using network distillation on an ensemble of state-of-the-art CNNs on CIFAR-10 dataset. Their results suggest that to achieve similar accuracy with a shallow student model, it should possess much more parameters than the deep teacher model (can be 30 times larger than the deep teacher model). Still the accuracy may not reach the level of the teacher model.

**MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications**. Howard et al. (Google Inc.) Arxiv preprint [27th April 2017]
{: .notice}
> This paper introduces a smaller and faster convolutional neural network achitecture by replacing convolutions by depthwise separable convolutions and a 1x1 pointwise convolution to combine the outputs of depthwise convolutions. Additionally this paper introduces two more parameters, width multiplier and resolution multiplier to reduce the number of hyperparameters further.

**Dynamic Network Surgery for Efficient DNNs**. Guo et al., NIPS. 2016
{: .notice}
> This paper was [presented](https://papers.nips.cc/paper/6165-dynamic-network-surgery-for-efficient-dnns) as a poster at NIPS 2016. Two operations: pruning and splicing (recovery of pruned connections) are performed in a continuous manner. Connections are pruned based on the magnitude of their weights. Authors claim a 17.7X compression rate for AlexNet.

**Learning Structured Sparsity in Deep Neural Networks**. Wen et al., NIPS. 2016
{: .notice}
> This paper was [presented](http://papers.nips.cc/paper/6504-learning-structured-sparsity-in-deep-neural-networks) a poster at NIPS 2016. This paper introduces group lasso based sparsity regularization to zero out all weights in some structures (filters, channels, and layers) without a significant drop of classification accuracy.
