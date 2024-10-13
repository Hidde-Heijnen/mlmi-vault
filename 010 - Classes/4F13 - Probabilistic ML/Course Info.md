---
link: https://mlg.eng.cam.ac.uk/teaching/4f13/2425/
---
## Course structure
14 lectures, 2 coursework revisions, [[#Coursework|3 pieces of course work]]. The evaluation is by coursework only, all three pieces of course work carry an equal weight. There is no final exam.

This year, the exposition of the material will be centred around three specific machine learning areas: 
1. Supervised non-parametric probabilistic inference using Gaussian processes, 
2. The TrueSkill ranking system and 
3. The latent Dirichlet Allocation model for unsupervised learning in text.

- David Barber [Bayesian Reasoning and Machine Learning](http://web4.cs.ucl.ac.uk/staff/D.Barber/textbook/140324.pdf), Cambridge University Press (2012), available freely on the web.
- Christopher M. Bishop [Pattern Recognition and Machine Learning](https://www.microsoft.com/en-us/research/uploads/prod/2006/01/Bishop-Pattern-Recognition-and-Machine-Learning-2006.pdf). Springer (2006)
- David J.C. MacKay [Information Theory, Inference, and Learning Algorithms](https://www.inference.org.uk/mackay/itila/), Cambridge University Press (2003), available freely on the web.

## Lecture Notes Overview
Note: the links in the table below aren't up to date. If you want to see lecture slides from a similar but not identical course taught previously, go to the [Michaelmas 2021 course website](https://mlg.eng.cam.ac.uk/teaching/4f13/2122), but be warned that the slides may change slightly.

The organisation of the handouts is changing. This year the material will be structured into small chunks, each containing a single core concept. Printed handouts won't be provided at the lectures, but will be available on this web site. I recommend that you don't bring printed slides to the lectures, but of course you can do so if you think it works better for you.
### Introduction to Probabilistic Machine Learning (2L)
**Lecture 1:**
- [Modelling data](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/modelling%20data.pdf)
- [Linear in the parameters regression](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/linear%20in%20the%20parameters%20regression.pdf)
- [Likelihood and the concept of noise](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/likelihood%20and%20noise.pdf)

**lecture 2:**
- [Probability fundamentals](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/probability%20fundamentals.pdf)
- [Bayesian inference and prediction with finite regression models](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/bayesian%20finite%20regression.pdf)
- [Marginal likelihood](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/marginal%20likelihood.pdf)

### Gaussian Processes (3L)
**Lecture 3:**
- [Parameters and functions](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/parameters%20and%20functions.pdf)
- [Gaussian Process](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/gp.pdf), with a [sequential generation demo](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/seq.m)

**Lecture 4:**
- [Correspondence between linear models and GPs](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/correspondence.pdf)
- [Should we use finite or infinite models?](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/infinite.pdf)

**Lecture 5:**
- [Covariance functions](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/covariance%20functions.pdf)
- Quick introduction to the [gpml toolbox](http://www.gaussianprocess.org/gpml/code)

### Probabilistic Ranking (3L)
**Lecture 6:**
- [Introduction to ranking](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/ranking.pdf)

**Lecture 7:**
- [Gibbs sampling](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/gibbs%20sampling.pdf)
- Gibbs sampling demo: [Matlab script](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/gibbs2.m)
- [Gibbs sampling in the TrueSkill model](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/gibbs%20in%20TrueSkill.pdf)

**Lecture 8:**
- [Factor graphs](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/factor%20graphs.pdf)
- [Message passing in TrueSkill](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/message%20in%20TrueSkill.pdf)
- [Approximation by moment matching](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/moment%20matching.pdf)

### Modelling Document Collections (3L)
**Lecture 9:**
- Models of [text](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/text.pdf)
- Discrete [binary distributions](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/binary.pdf)
- Categorical, multinomial, and [discrete distributions](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/discrete.pdf)

**Lecture 10:**
- Simple [categorical and mixture models](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/document%20models.pdf)
- Learning in models with latent variables: the [Expectation Maximization (EM)](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/expectation%20maximization.pdf) algorithm

**Lecture 11:**
- [Gibbs sampling in mixture models](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/gibbs%20for%20Bayesian%20mixture.pdf), collapsed Gibbs
- [Latent Dirichlet Allocation](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/lda.pdf) topic models


## Coursework

### Coursework 1
[Coursework 1](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/coursework1.pdf) is about regression using Gaussian processes. You will need the following files: [cw1a.mat](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/cw1a.mat) and [cw1e.mat](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/cw1e.mat).  
**Due:** Friday 8th November, 2024 at 12:00 noon (online).
### Coursework 2
[Coursework 2](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/coursework2.pdf) will be about Probabilistic Ranking. You will need the data file: [tennis_data.mat](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/tennis_data.mat)
For Matlab, use: [cw2.m](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/cw2.m), [gibbsrank.m](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/gibbsrank.m), [eprank.m](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/eprank.m).  
For Python, use: [coursework2.ipynb](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/coursework2.ipynb), [cw2.py](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/cw2.py), [gibbsrank.py](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/gibbsrank.py), [eprank.py](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/eprank.py).  
**Due:** Friday 22nd November, 2024 at 12:00 noon (online).
### Coursework 3
[Coursework 3](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/coursework3.pdf) is about the Latent Dirichlet Allocation (LDA) model. You will need [kos_doc_data.mat](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/kos_doc_data.mat).  
For Matlab, use: [bmm.m](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/bmm.m), [lda.m](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/lda.m), [sampDiscrete.m](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/sampDiscrete.m).  
For Python, use: [bmm.py](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/bmm.py), [lda.py](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/lda.py), [sampleDiscrete.py](https://mlg.eng.cam.ac.uk/teaching/4f13/2425/cw/sampleDiscrete.py).  
**Due:** Friday 6th December, 2024 at 12:00 noon (online).
## How to submit
DON'T FORGET YOUR COVER SHEET! PLEASE TICK POSTGRADUATE BOX!
- Upload ONE file only as a pdf. 
- MPHIL MLMI STUDENTS - make sure that the file name includes your candidate number but not your name or student ID as you are being marked anonymously.  Please use the MPhil coversheet.

1. Click on the link for the appropriate piece of coursework
2. Click on "add submission"
3. Drag your file (which should all be in one pdf document, with the submission cover sheet at the front) to the File Submission field
4. Wait until the file is being downloaded (you should see the blue status bar to indicate that this is happening)
5. After the blue status bar has disappeared, click the "Save Changes" button
6. Click "CONFIRM SUBMISSION" - this will mean that your coursework is properly submitted
NB: ONCE YOU CLICK "CONFIRM SUBMISSION" YOU CANNOT RESUBMIT OR CHANGE ANYTHING