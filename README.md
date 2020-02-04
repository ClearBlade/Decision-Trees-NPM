# Decision-Trees-NPM

## Contents

### [Overview](#overview-1)
### [System Installation](#system-installation)
### [Steps for Transpilation to ES5](#steps-for-transpilation-to-es5-1)
### [Usage](#usage-1)
### [Assets](#assets-1)

## Overview

Decision Trees can be implemented to run on the ClearBlade Platform for classification and regression purposes.

This is an ipm package, which contains one or more reusable assets within the ipm Community. The 'package.json' in this repo is a ipm spec's package.json, [here](https://docs.clearblade.com/v/3/6-ipm/spec), which is a superset of npm's package.json spec, [here](https://docs.npmjs.com/files/package.json).

[Browse ipm Packages](https://ipm.clearblade.com)

## System Installation

1. Open the ClearBlade Platform and enter your login credentials
```
https://platform.clearblade.com/
```
2. Click on **Add System** -> **Advanced** and copy the link of this repository in the box.
```
https://github.com/ClearBlade/decision-trees
```
3. Click **Create**
4. You can now access this system in the platform.

## Steps for Transpilation to ES5

Follow these steps for transpilation - 

```
https://github.com/ClearBlade/Machine-Learning-Node-Libraries/blob/master/README.md#steps-for-transpilation-to-es5-1
```

## Usage

- This IPM package consists of a Decision Tree Library that can be imported on the ClearBlade Platform in order to train and test machine learning models on the platform. This library can be used to perform classification and regression.

- As a classifier it can be used as follows:

```
var model = getTree();
var classifier = new model.DecisionTreeClassifier({ gainFunction: "gini", maxDepth: 10, minNumSamples: 3});
classifier.train(dataset, predictions);
  
var output = classifier.predict(test);
```

- The implementation of these libraries is done in the [smoke test](https://github.com/ClearBlade/decision-trees/blob/master/code/services/DecisionTreeSmokeTest/DecisionTreeSmokeTest.js) and you can refer to the **Official Documentation** of that library to explore more options that you can use.  

## Assests

### Libraries 

| Library  | Description  | Official Documentation |   
|---|---|---|
| ``` CARTDecisionTreeLibrary ```  | A Library Implementing Classification and Regression Trees  | https://github.com/mljs/decision-tree-cart |

### Code Services

``` DecisionTreeSmokeTest ``` : A code service to show working of Decision Tree Library.
