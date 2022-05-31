# Scikit-learn MOOC take-aways

## The big messages of the MOOC

### 1. The machine learning pipeline

- Learned on a **train set**; applied to a **test set**
- Built from a data matrix, a given number of features for each observation
- **Transformations** of the data
  - Encoding of the categorical variables
  - Only using information available at train time
  - The scikit-learn pipeline object

### 2. Adapting model complexity to the data

- Minimize the **test error**
  - **Train error** can detect **underfit**: models too simple for the data
- Multiple **hyperparameters**
  - Control model complexity
  - Selecting hyperparameters is important
  - GridSearchCV, RandomSearchCV

### 3. Specific models

- Understanding the models
  - know when they are suited to the data
  - intuitions on how to debug them
- **Linear models**: combining the values of features
  - For many features or few observations
- **Tree-based**: a series of binary choices (thresholds)
  - For tabular data, columns of different nature
  - HistGradientBoostingRegressor and Classifier are goto methods

### Topics that were not covered in the MOOC

- **Unsupervised learning**
  - Finding order and structure in the data, for instance to group samples, or to transform features
  - Particularly useful because it does not need labels
  - But given labels, supervised learning not unsupervised learning, is more likely to recover the link between data and labels
- **Model inspection**
  - Understanding what drives a prediction
  - Useful for debugging, for reasoning on the system at hand
  - Requires a lot of nuance
- **Deep learning**
  - Often not better than gradient boosting trees for classification or regression on tabular data
  - But more flexible: can work natively with tasks that involve variable length structures in the input and output of the model (e.g. speech to text)
  - For images, text, voice: use pretrained models
  - Comes with great computational and human costs, as well as large maintenance costs
  - Not in scikit-learn: have a look at resources on pytorch and tensorflow to get started!

## Bringing value: the bigger picture beyond machine-learning

### Valudation and evaluation matter

- Validation and evaluation are often the **weak point** of an analysis.
- Even with cross-validation, a measure of prediction accuracy is an **imperfect estimate** of how the model will actually generalize to new data
- As you narrow down on a solution, spend **increasingly more effort** on validating it
- Have many splits in your cross-validation

## Machine learning is a small of the problem most of the times

- How to approach the full problem (the full **value chain**)
- Acquiring **more/better data** is often more important than using fancy models
- Putting in **production**: when the model is used routinely
  - Technical debt (simpler models are easier to maintain, require less compute power)
  - Drifts of the data distribution (require monitoring)

## Technical craft is not all

- Methodological elements are not enough to always have solid conclusion from a statistical standpoint
- Once you know how to run the software, the biggest challenges are **understanding the data**, its shortcomings, and what can and cannot be conlcuded from an analysis
  - Automating machine learning does not solve data science
  - Domain knowledge and critical thinking about the data are crucial

## How the predictions are used

- Errors mean different things depending on the **situation**
  - **Operational risk**: how to errors impact real world?
    - Add placement: errors are harmless
    - Medicine: errors can kill
  - **Operational logic**: better a false detection or a miss?
    - E.g. detecting brain tumors:
      - Send to surgery: false detections are very dangerous
      - Give an MRI scan: missed should be avoided, as an MR scan is harmless
- The predictions may modify how the system functions:
  - Predicting who will benefit from an hospital stay may overcrowd some units of the hospital, and thus change the positive impact of hospitals on patients.

## Choice of the output/the labeled data

- What we chose to predict is a very **loaded choice**
- Interesting labels are often hard to get, focusing on the "easy" ways of accumulating labels comes with biases
- Out target may be a proxy of the quantity of interest

## Biases in the data

- The data may not reflect the **ground truth**
  - Disease monitoring is function of testing policy
  - It may change with time, it may be unevern across the population (e.g. higher quality data for rich people)
- The state of affaires may not be the desired one
  - For equal qualifications and responsibilities, women are typically payed less than men. A learner will pick this up and amplify inequalities

## Prediction models versus causal models

- Predictive models do not always capture **causality**
  - People that go to the hospital die more than people who do not
    - **Fallacy**: comparing different populations
  - Having heart pressure greater than a threshold triggers specific care which has a positive impact. A learner will pick up above-threshold heart pressure as good for you.
  - In pure predictive settings, these informations are beneficial for their predictions. However, they should not be trusted when designing interventions and interpretation is subject to caution

## Societal impact

- See also https://fairlearn.org/
- ML induces changes in our society
- Challenges at the intersection of technology and society, no solution will be purely technical
