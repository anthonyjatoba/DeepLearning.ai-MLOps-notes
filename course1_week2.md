# Week 2: Model overview

## Selecting and Training a Model

### Modeling overview

**Model-centric AI development vs Data-centric AI development**: there has been a lot of emphasis on choosing the right model, such as the right neural network architecture. For practical projects, it may be more useful to take a data-centric approach, making sure you are feeding your algorithm with high-quality data.

### Key challenges

AI system = Code (algorithm/model) + Data

Model development is an iterative process, going through iteration fast is key to improve performance. By the end, carry out a richer error analysis (audit performance)

Challenges in model development:
- Doing well on the training set
- Doing well on the dev/test set
- Doing well on business metric or project goal

### Why low average error isn't good enough

Challenges:
- Performance on disproportionately important examples
    - Give a higher weight
- Performance on key slices of the dataset
    - **Loan approval:** make sure not to discriminate by etnicity, gender, location...
    - **Product recommendations from retailers:** be careful to treat fairly all major user, retailer, and product categories.
- Rare classes
    - **Skewed data distributon:** accuracy in rare classes, e.g. medical diagnosis

### Establish a baseline

#### HLP: Human level performance

**Speech recognition:** 
- Clear speech: 94% (95% HLP)
- Car noise: 89% (93% HLP)
- People noise: 87% (87% HLP)
- Low bandwitch: 70% (70% HLP)

Focus on car noise background.

#### Unstructured and structured data

Humans are better at unstructured data

- **Unstructured data:** use HLP as baseline
- **Structured data** (giant databases): HLP is less usefull

#### Ways to stablish a baseline

- HLP
- Literature
- Quick-dirty-implementation
- Performance of older system

Baseline helps to indicate what might be possible. In some cases it also gives a sense of what is irreducible error.

### Tips for getting started

#### Model + Hyperparameters + Data


- Literature search to ee what's possible (courses, blogs, projects)
- Find open-source implementations
- Reasonable algorithm + good data > great algorithm with + not so good data

#### Deployment constraints

Should you take into account deployment constraints when picking a model? 
- **Yes**,, if baseline is already established and goal is to build and deploy.
- **No** (or not necessarily), if purpose is to *establish a baseline* and determine what is possible and might be worth pursuing.

#### Sanity-check for code and algorithm

- Try to overfit a small training dataset before training on a large one to find bugs quickly.
    - Example 1: speech recognition - train on only one example
    - Example 2: image segmentation - feed just one image