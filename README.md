# VB Diarization with Eigenvoice and HMM Priors

[![Build Status](https://travis-ci.org/wq2012/VB_diarization.svg?branch=master)](https://travis-ci.org/wq2012/VB_diarization) [![PyPI Version](https://img.shields.io/pypi/v/vbdiar.svg)](https://pypi.python.org/pypi/vbdiar) [![Python Versions](https://img.shields.io/pypi/pyversions/vbdiar.svg)](https://pypi.org/project/vbdiar) [![Downloads](https://pepy.tech/badge/vbdiar)](https://pepy.tech/project/vbdiar)

## Overview

This is a **refactored** version of the VB diarization software available at
[BUT Speech@FIT](https://speech.fit.vutbr.cz/software/vb-diarization-eigenvoice-and-hmm-priors).

I am **NOT** the original author of the library.

To learn more about speaker diarization, check out
[awesome-diarization](https://github.com/wq2012/awesome-diarization).

## Tutorial

Install the package by:

```bash
pip3 install vbdiar
```

Then run the demo by:

```bash
python3 VB_diarization_demo.py
```

Example output will look like:

```
Sparsity:  361046 0.01620852224405829
0 [-1576615.8355463971, 0.49998034201233305, 0.6934600067618628]
1 [-1573630.3277233944, 0.49488450922230304, 0.6836972634466193]
2 [-1573617.1947171816, 0.36649139165757927, 0.5409513837409551]
3 [-1572912.9800757084, 0.11168936153343934, 0.3251044601426033]
4 [-1571979.6082527784, 0.0511120253656933, 0.24549579256407847]
5 [-1571852.5969909965, 0.04362939516423323, 0.25859357242423703]
6 [-1571843.076166819, 0.041302487267731204, 0.2567046359254187]
7 [-1571839.496966404, 0.040141590272420244, 0.25445602191467415]
8 [-1571838.1495057037, 0.03968370343565774, 0.25386126590129093]
9 [-1571837.9234294428, 0.039410488991860955, 0.2532333123298111]
Sparsity:  361046 0.01620852224405829
0 [-1576615.8355463971, 0.4999273922036727, 0.6955313429761281]
1 [-1573630.237593537, 0.49160926691380996, 0.6830149532990263]
2 [-1573594.5598103066, 0.40390147708810875, 1.02908233512813]
3 [-1573262.4806976253, 0.23319489472978927, 0.9278382508877128]
4 [-1572494.6378055941, 0.07173885575254442, 0.2388312218175654]
5 [-1571891.0068257698, 0.036514173883825, 0.1331738561456543]
6 [-1571828.6978994848, 0.03385540733953837, 0.12283041224134558]
7 [-1571827.8500376013, 0.0331494832874937, 0.11751781046290008]
8 [-1571827.6890726706, 0.03264925241684536, 0.11368757107899666]
9 [-1571827.4188203989, 0.0318864571203821, 0.10959011779700172]
```

## Notes from original author

This python code implements speaker diarization algorithm described in:
* http://www.fit.vutbr.cz/~burget/VB_diarization_slides.pdf

This algorithm is based on a generalized version of the model described in:
* [Kenny, P. Bayesian Analysis of Speaker Diarization with Eigenvoice Priors, Montreal, CRIM, May 2008](http://www.crim.ca/perso/patrick.kenny/BayesCluster.pdf)
* [Kenny, P., Reynolds, D., and Castaldo, F. Diarization of Telephone Conversations using Factor Analysis IEEE Journal of Selected Topics in Signal Processing, December 2010](http://www.crim.ca/perso/patrick.kenny/Kenny_sdfa.pdf)

The generalization introduced in this implementation lies in using an HMM instead of the simple mixture model when modeling generation of segments (or even frames) from speakers. HMM limits the probability of switching between speakers when changing frames, which makes it possible to use the model on frame-by-frame bases without any need to iterate between
1) clustering speech segments and
2) re-segmentation (i.e. as it was done in the paper above).