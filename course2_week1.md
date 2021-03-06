# Course 2 Week 1: Overview of the ML Lifecycle and Deployment 

## Introduction to Machine Learning Engineering in Production

### Overview

#### The importance of data

*"Data is the hardest part of ML and the most important piece to get right... Broken data is the most common cause of problems in production ML Systems"*

Scaling Machine Learning at Uber with Michelangelo - Uber

*"No other activity in the machine learning lifecycle has a higher return on investment than improving the data a model has access to."*

Feast: Bridging ML Models and Data - Gojek

#### Traditional ML modeling

![Traditional ML modeling](figures/course2/week1/traditional_ml.png)

#### Production ML systems require so much more

![Production ML](figures/course2/week1/production_ml.png)

ML code accounts for approximately 5% of the total code.

#### ML modeling vs production ML

![ML modeling vs production ML](figures/course2/week1/academic_vs_production.png)

- Production ML = ML development + Modern software development

#### Managing the entire lifecycle of data

- Labeling
- Feature space coverage
- Minimal dimensionality
- Maximum predictive data
- Fairness
- Rare conditions

#### Modern software development

Accounts for:
- Scalability
- Extensibility
- Configuration
- Consistency and reproducibility
- Safety and security
- Modularity
- Testability
- Monitoring
- Best practices

#### Production machine learning system

![ML cycle](figures/course2/week1/production_ml_cycle.png)

#### Challenges in production grade ML

- Build integrate systems
- Continuously operate it in production (24/7)
- Handle continuously changing data
- Optimize compute resource costs

### ML Pipelines

#### ML pipelines

Infrastructure for automating, monitoring, and maintaining model training and deployment.

![Pipeline example](figures/course2/week1/pipeline_example.png)

- ML pipeline workflows are usually directed acyclic graphs (DAG).
- A DAG is a directed graph that has no cycles.
- DAGs define the sequencing of the tasks to be performed, based on their relationships and dependencies.

#### Pipeline orcherstration frameworks

- Responsible for scheduling the various components in an ML pipeline DAG dependencies.
- Help with pipeline automation.
- Examples: Airflow, Argo, Celery, Luigi, Kubeflow

#### TensorFlow Extended (TFX)

An end-to-end platform for deploying production ML pipelines.

![TFX components](figures/course2/week1/tfx_components.png)

## Collecting Data

### Importance of Data

In production ML, you usually have to find ways to collect data.

#### Example: predicting time spent on the airport security checkpoint

![Airport line example](figures/course2/week1/airport_line.png)

One person at the start of the line and another one recorded the time each passenger entered or left the line. **Painful!**

#### ML: Data is a First-Class Citizen

-  Software 1.0
    - Explicit instructions to the compute
- Software 2.0
    - Specify some goal on the behavior of a program
    - Find a solution using optimization techniques
    - Good data is key to success
    - Code in Software = Data in ML

#### Everything starts with data

![XKCD ML Comic](figures/course2/week1/xkcd_ml.png)

- Models aren't magic
- Meaningful data:
    - Maximize predictive content
    - Remove non-informative data
    - Feature space coverage

#### Garbage In, Garbage Out

![Garbage In, Garbage Out](figures/course2/week1/garbage_in_out.png)

#### Key Points

- Understand users, translate user needs into data problems
- Ensure data coverage and high predictive signal
- Source, store and monitor quality data responsibly

### Example Application: Suggesting Runs

![Garbage In, Garbage Out](figures/course2/week1/suggesting_runs.png

#### key considerations

- Data availability and collection
    - What kind of/how much data is available
    - How often does the new data come in:
    - Is it annotated?
        - If not, how hard/expensive is it to get it labeled?

- Translate user needs into data needs
    - Data needed
    - Features needed
    - Labels needed

#### Example dataset

![Garbage In, Garbage Out](figures/course2/week1/run_example.png)

#### Get to know your data

- Identify data sources
- Check if they are refreshed
- Consistency for values, units, and data types
- Monitor outliers and errors

#### Dataset issues

- Inconsistent formatting
    - Is zero "0", "0.0", or an indicator of a missing measurement
- Compounding errors from other ML Models
- Monitor data sources for system issues and outages

#### Measure Data Effectiveness

- Intuition about data value can be misleading
    - Which features have predictive value and which ones do not?
- Feature engineering helps to maximize the predictive signals
- Feature selection helps to measure the predictive signals

#### Translate User Needs Into Data Needs

![Run example needs](figures/course2/week1/run_needs.png)

Translate that into features

![Run example features](figures/course2/week1/run_features.png)

![Run example labels](figures/course2/week1/run_labels.png)

#### Key points

- Understand your user, translate their needs into data problems
    - What kind of/how much data is available
    - What are the details and issues of your data
    - what are your predictive features
    - What are the labels you are tracking
    - What are your metrics

### Responsible Data: Security, Privacy and Fairness

#### Example

A classifier trained on Open Images dataset may not be able to label wedding traditions from different parts of the world.

![Wedding example](figures/course2/week1/wedding_example.png)

#### Source Data Responsibly

![Wedding example](figures/course2/week1/data_sources.png)

#### Data Security and Privacy

- Data collection and management isn't just about your model
    - Give user control o what data can be collected
    - Is there a risk of inadvertently revealing user data?
- Compliance with regulations and policies

#### Users privacy

- Protect personally identifiable information
    - Aggregation: replace unique values with summary value
    - Redaction: remove some data to create a less complete picture

#### How ML Systems Can Fail Users

- Representational har
- Opportunity denial
- Disproportionate product failure
- Harm by disadvantage

#### Commit to Fairness

- Make sure your models are fair
    - Group fairness, equal accuracy
- Bias in human-labeled and/or collected data
- ML Models can amplify biases

#### Reducing bias: Design fair labeling systems

- Accurate labels are necessary for supervised learning
- Labeling can be done by:
    - Automation (logging or weak supervision)
- Humans (aka "Raters", often semi-supervised)

#### Types of human raters

![Human raters](figures/course2/week1/human_raters.png)

#### Key points

- Ensure rater pool diversity
- Investigate rater context and incentives
- Evaluate rater tools
- Manage cost
- Determine freshness requirements

## Labeling Data

Data is always changing. If you trained a model a few years ago to recognize what a book looks like, it would only consider paper books. If you trained the same model nowadays, you would also want to include ebooks.

### Case Study: Degraded Model Performance

#### You're on an Online Retailer Selling Shoes

Your model predicts click-through rates (CTR), helping you decide how much inventory to order.

**When suddenly** your AUC and prediction accuracy has dropped on men's dress shoes!

- Why?
- How do we even know that we have a problem?

If you don't put good practices in place in the production setting, you're gonna find out when you order too many shoes or not enough shoes.

#### Case study: taking action

- How to detect problems early on?
- What are the possible causes?
- What can be done to solve these?

#### What causes problems?

Kinds of problems:
- Slow problems: e.g., drift
- Fast problems: e.g., bad sensors, bad software update

#### Gradual problems

![Gradual problems](figures/course2/week1/gradual_problems.png)

#### Sudden problems

![Sudden problems](figures/course2/week1/sudden_problems.png)

#### Why "understand" the model?

- Mispredictions do not have uniform **cost** to your business
- The **data you have** is rarely the data you wish you had
- Model objective is nearly always a **proxy** for your business objectives
- Some percentage of your customers may have a **bad experience**

**The real world does not stand still**

### Data and Concept Change in Production ML

#### Detecting problems with deployed models

- Data and scope change
- Monitor models and validate data to find problems early
- Changing ground truth: **label** new training data

#### Easy problems

Example: classifying cats and dogs in pictures.

- Ground truth changes slowly (month, years)
- Model retraining driven by:
    - Model improvements, better data
    - Changes in software and/or systems
- Labeling
    - Curated datasets
    - Crowd-based

#### Harder problems

Example: fashion/style applications.

- Ground truth changes fast (weeks)
- Model retraining driven by:
    - **Declining model performance**
    - Model improvements, better data
    - Changes in software and/or systems
- Labeling
    - Direct feedback
    - Crowd-based

#### Really hard problems

Example: stock market applications.

- Ground truth changes very fast (days, hours, min)
- Model retraining driven by:
    - **Declining model performance**
    - Model improvements, better data
    - Changes in software and/or systems
- Labeling
    - Direct feedback
    - Weak supervision

#### Key points

- Model performance decay over time
    - Data and Concept Drift
- Model retraining helps to improve performance
    - Data labeling for changing ground truth and scarce labels

### Process Feedback and Human Labeling

#### Data labeling

Variety of Methods:
- Process Feedback (direct labeling): e.g., actual vs predicted click-through
- Human Labeling: e.g., cardiologists labeling MRI images
- ~~Semi-Supervised Labeling~~
- ~~Active Learning~~
- ~~Weak Supervision~~

We are not going to cover the last ones.

#### Why is labeling important in production ML

In many cases you need to perform supervised learning, therefore requiring labeled data.

- Using business/organization available data
- Frequent model retraining
- Labeling ongoing and critical process
- Creating a training dataset requires labels

#### Direct labeling: continuous creation of training dataset

Features are taken from the inference requests that your model is getting.

![Direct labeling](figures/course2/week1/direct_labeling.png)

Advantages
- Training dataset continuous creation
- Labels evolve quickly
- Captures strong label signals

Disadvantages
- Hindered by the inherent nature of the problem
- Failure to capture ground truth
- Largely bespoke design

#### Process feedback - Open-Source log analysis tools

**Logstash:** free and open-source data processing pipeline
- Ingests data from a multitude of sources
- Transforms it
- Sends it to your favorite "stash"

**Fluentd**
- Open-source data collector
- Unify the data collection and consumption

#### Process feedback - Cloud log analytics

**Google Cloud Logging**
- Data and events from Google Cloud and AWS
- BindPlane. Logging: application components, on-premise, and hybrid cloud systems
- Sends it to your favorite "stash"

**AWS ElasticSearch**

**Azure Monitor**

#### Human labeling

People ("raters") to examine data and assign labels manually.

![Direct labeling](figures/course2/week1/human_labeling.png)

Methodology
1. Unlabeled data is collected
2. Human "raters" are recruited
3. Instructions to guide raters are created
4. Data is divided and assigned to raters
5. Labels are collected and conflicts resolved

Advantages
- More labels
- Pure supervised learning

Disadvantages
- Quality consistency: datasets difficult for human labeling
- It can be slow
- It can be expensive (specialists)
- Small dataset curation

![Direct labeling](figures/course2/week1/human_labeling_disadvantages.png)

#### Key points

- Various methods of data labeling
    - Process feedback
    - Human labeling
- Advantages and disadvantages of both

## Validating Data

Garbage In, garbage out. You can have a lot of data, but if your data is not good, it is not good for ML either. How do you know data is good or isn't good?

### Detecting Data Issues

#### Drift and skew

- **Drift:** changes in data over time, such as data collected once a day.
- **Skew:* difference between two static versions, or different sources, such as training set and serving set

#### Typical ML pipeline

In a typical ML pipeline, you have different sources of data, but over time they will change, so your model performance can drop quickly.

![Direct labeling](figures/course2/week1/typical_ml_pipeline.png)

#### Model Decay: Data Drift

Over time a ML model starts to perform poorly in many cases, and we call that model decay. Usually, is called drift, which is changes in the statistical properties of features, often caused by seasonality, trends, or in general changes in the world. 

![Model Decay - Data drift](figures/course2/week1/data_drift.png)

In the example above, the app classifies a user as a spammer if he sends 20 or more messages a day. After a system update, both spammer and non-spammer started to send more messages, classifying every user as a spammer.

#### Performance Decay: Concept Drift

Concept drift is a change in the statistical properties of your label. 

![Performance Decay - Concept drift](figures/course2/week1/concept_drift.png)

#### Detecting Data Issues

- Detecting schema skew
  - Training and serving data do not conform to the same schema
  
- Detecting distribution skew
  - Dataset shift -> covariate or concept shift
  
- Requires continuous evaluation

#### Detecting Distribuction skew

- **Dataset shift:** when the joint probability of x and y is not the same during training and serving 
- **Covariate shift:** the change of distribution of the input (x) variables present in train and serving data, but the conditional distribution remains unchanged.
- **Concept shift:** a change in the relationship between the input (x) and output (y) variables.

![Detecting Distribuction skew](figures/course2/week1/shift_definition.png)

#### Skew detection workflow

![Skew detection workflow](figures/course2/week1/skew_detection_workflow.png)

### TensorFlow Data Validation

- Understand, validate, and monitor ML data at scale
- Used to analyze and validate petabytes of data at Google every day
- Proven track record in helping TFX users maintain the health of their ML pipelines

#### TFDV capabilities

- Generates data statistics and browser visualizations
- Infers the data schema
- Performs validity checks against the schema
- Detects training/serving skew

#### Skew detection TFDV

![Skew detection TFDV](figures/course2/week1/skew_detection_tfdv.png)

#### Skew - TFDV

- Supported for categorical features
- Expressed in terms of L-infinity distance (Chebyshev distance)
- Set a threshold to receive warnings

![Skew detection TFDV](figures/course2/week1/skew_tfdv.png)

#### Schema skew

Serving and training data don't conform to the same schema:
- For example, int != float

#### Feature skew

Training **feature values** are different than the serving **feature values**:
- Feature values are modified between training and serving time
- Transformation applied only in one of the two instances

#### Distribution skew

**Distribution** of serving and training dataset is significantly different:
- Faulty sampling method during training
- Different data sources for training and serving data
- Trend, seasonality, changes in data over time

#### Key points

- TFDV: Descriptive statistics at scale with the embedded facets visualizations
- It provides insight into:
  - What are the underlying statistics of your data
  - How does your training, evaluation, and serving dataset statistics compare
  - How can you detect and fix data anomalies

### Optional references

[MLops](https://cd.foundation/blog/2020/02/11/announcing-the-cd-foundation-mlops-sig/)

[Data 1st class citizen](https://medium.com/@karpathy/software-2-0-a64152b37c35)

[Runners app](https://pair.withgoogle.com/chapter/data-collection/)

[Rules of ML](https://developers.google.com/machine-learning/guides/rules-of-ml)

[Bias in datasets](https://ai.googleblog.com/2018/09/introducing-inclusive-images-competition.html)

[Logstash](https://www.elastic.co/logstash)

[Fluentd](https://www.fluentd.org/)

[Google Cloud Logging](https://cloud.google.com/logging/)

[AWS ElasticSearch](https://aws.amazon.com/elasticsearch-service/)

[Azure Monitor](https://azure.microsoft.com/en-us/services/monitor/)

[TFDV](https://blog.tensorflow.org/2018/09/introducing-tensorflow-data-validation.html)

[Chebyshev distance](https://en.wikipedia.org/wiki/Chebyshev_distance)

#### Papers

Konstantinos, Katsiapis, Karmarkar, A., Altay, A., Zaks, A., Polyzotis, N., ??? Li, Z. (2020). Towards ML Engineering: A brief history of TensorFlow Extended (TFX). http://arxiv.org/abs/2010.02013 

Paleyes, A., Urma, R.-G., & Lawrence, N. D. (2020). Challenges in deploying machine learning: A survey of case studies. http://arxiv.org/abs/2011.09926

Sculley, D., Holt, G., Golovin, D., Davydov, E., & Phillips, T. (n.d.). Hidden technical debt in machine learning systems. Retrieved April 28, 2021, from Nips.cc https://papers.nips.cc/paper/2015/file/86df7dcfd896fcaf2674f757a2463eba-Paper.pdf