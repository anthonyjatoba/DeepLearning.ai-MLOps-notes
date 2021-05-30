# Week 1: Overview of the ML Lifecycle and DeploymentThe 

## Machine Learning Project Lifecycle

### Steps of an ML Project

### Case study: speech recognition

## Deployment

### Key challenges

### Deployment patterns

### Monitoring

### Pipeline monitoring

Many AI systems are not just a single machine learning model running a prediction service, but instead involves a  pipeline of multiple steps. Changes on one step may affect the next steps.

Metrics to monitor:
* Software metrics
* Input metrics
* Output metrics

**How quickly data change?** some applications have data that changes quickly. User data generally has a slower drift. Enterprise data (B2B) can shift fast.

### Optional references

[Concept and Data Drift](https://towardsdatascience.com/machine-learning-in-production-why-you-should-care-about-data-and-concept-drift-d96d0bc907fb)

[Monitoring ML Models](https://christophergs.com/machine%20learning/2020/03/14/how-to-monitor-machine-learning-models/)

[A Chat with Andrew on MLOps: From Model-centric to Data-centric](https://www.youtube.com/watch?v=06-AZXmwHjo)

#### Papers

Konstantinos, Katsiapis, Karmarkar, A., Altay, A., Zaks, A., Polyzotis, N., … Li, Z. (2020). Towards ML Engineering: A brief history of TensorFlow Extended (TFX). http://arxiv.org/abs/2010.02013 

Paleyes, A., Urma, R.-G., & Lawrence, N. D. (2020). Challenges in deploying machine learning: A survey of case studies. http://arxiv.org/abs/2011.09926

Sculley, D., Holt, G., Golovin, D., Davydov, E., & Phillips, T. (n.d.). Hidden technical debt in machine learning systems. Retrieved April 28, 2021, from Nips.c https://papers.nips.cc/paper/2015/file/86df7dcfd896fcaf2674f757a2463eba-Paper.pdf