# Notes

## Introduction machine-learning concepts

### General concepts

- Goal of machine-learning is to generalize, i.e. conclude on new instances
- Challenges involved in generalizing are the great variety of data, noise and unexplainable variance (due to data not captured in data set).
- Memorizing, also known as nearest-neighbour predictor, predicting the target based on the closest match in the database. Works well on already known data, not well on new instances.

### Terminology

- Data matrix: all the data to consider in table format
- Samples: rows in data matrix are different observations
- Features: columns in data matrix are different descriptiors

### Supervised learning

- A data matrix _X_ with _n_ observations
- A __target__ _y_: a property of each observation
- The goal is to __predict__ _y_
  - __Classification__: _y_ is discrete, made of different classes.
  - __Regression__: _y_ is continuous, a numerical quantity

### Unsupervised learning

- A data matrix _X_ with _n_ observations
- The goal is to extract from _X_ structure that generalizes.
- Very wide variety of different problems