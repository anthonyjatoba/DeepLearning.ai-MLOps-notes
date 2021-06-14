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

Infrastructure for automating, monitoring and maintaining model training and deployment.

![Pipeline example](figures/course2/week1/pipeline_example.png)

- ML pipeline workflows are usually directed acyclic graphs (DAG).
- A DAG is a directed graph that has no cycles.
- DAGs define the sequencing of the tasks to be performed, based on their relationships and dependencies.

#### Pipeline orcherstration frameworks

- Responsible for scheduling the various components in an ML pipeline DAG dependencies.
- Help with pipeline automation.
- Examples: Airflow, Argo, Celery, Luigi, Kubeflow

#### TensorFlow Extended (TFX)

End-to-end platform for deploying production ML pipelines.

![TFX components](figures/course2/week1/tfx_components.png)

## Collecting Data

### Importance of Data

In production ML, you usually have to find ways to collect data.

#### Example: predicting time spent on airport security checkpoint

![Airport line example](figures/course2/week1/airport_line.png)

One person at the start of the line and another one recorded the time each passenger entered or left the line. **Painful!**

#### ML: Data is a First Class Citizen

-  Software 1.0
    - Explicit instructions to the compute
- Software 2.0
    - Specify some goal on the behavior of a program
    - Find solution using optimization techniques
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
- Ensue data coverage and high predictive signal
- Source, store and monotor quality data responsibly

### Example Application: Suggesting Runs

### Responsible Data: Security, Privacy & Fairness