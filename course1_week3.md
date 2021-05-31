# Data Definition and Baseline

## Define Data and Establish Baseline 

### Why is data definition hard?

#### Detecting iguana example

![iguana bounding boxes](figures/course1/week3/iguana_bounding_boxes.png)

Three people can come up with three different ways to label the iguanas.

#### Phone defect detection

![iguana bounding boxes](figures/course1/week3/phone_defect_bounding_boxes.png)

#### Data stage

![iguana bounding boxes](figures/course1/week3/data_stage.png)

In this week, we will dive into best practices for the data stage of the machine learning project.

- How to define what is the data?
- How to label and organize the data well?

### More label ambiguity examples

#### Speech recognition example

An audio clip can be transcribed in different ways:
- "Um, nearest gas station"
- "Umm, nearest gas station"
- "Nearest gas station [unintelligible]"

#### User ID merge example

A common application in many companies is user ID merge, that's when you have multiple records that you think correspond to the same person.

Say you company acquires another company:

![user id merge](figures/course1/week3/user_id_merge.png)

Two ways to merge the data:
- Use a supervised approach to say if two users are the same or not based on user attributes, in a scale of 0 to 1. Use instances labelled by users.
- Hire people to manually merge users. Give clear instructions.

#### Data definition questions

- What is the input x?
    - (Phone deffect detection) Is lightning good enough? Contrast? Resolution?
    - (Structured data) What features need to be included?
- What is the target label y?
    - How can we ensure labelers give consistent labels?

### Major types of data problems

### Small data and label consistency