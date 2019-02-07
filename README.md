# VB Diarization with Eigenvoice and HMM Priors

[![PyPI Version](https://img.shields.io/pypi/v/vbdiar.svg)](https://pypi.python.org/pypi/vbdiar) [![Python Versions](https://img.shields.io/pypi/pyversions/vbdiar.svg)](https://pypi.org/project/vbdiar)

## Overview

This is a **refactored** version of the VB diarization software available at
[BUT Speech@FIT](https://speech.fit.vutbr.cz/software/vb-diarization-eigenvoice-and-hmm-priors).

I am **NOT** the original author of the library.

## Notes from original author

This python code implements speaker diarization algorithm described in:
http://www.fit.vutbr.cz/~burget/VB_diarization_slides.pdf

This algorithm is based on a generalized version of the model described in:

```
Kenny, P. Bayesian Analysis of Speaker Diarization with Eigenvoice Priors, Montreal, CRIM, May 2008, http://www.crim.ca/perso/patrick.kenny/BayesCluster.pdf

Kenny, P., Reynolds, D., and Castaldo, F. Diarization of Telephone Conversations using Factor Analysis IEEE Journal of Selected Topics in Signal Processing, December 2010, http://www.crim.ca/perso/patrick.kenny/Kenny_sdfa.pdf
```

The generalization introduced in this implementation lies in using an HMM instead of the simple mixture model when modeling generation of segments (or even frames) from speakers. HMM limits the probability of switching between speakers when changing frames, which makes it possible to use the model on frame-by-frame bases without any need to iterate between
1) clustering speech segments and
2) re-segmentation (i.e. as it was done in the paper above).