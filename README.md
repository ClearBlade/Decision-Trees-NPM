# Decision-Trees

## Contents

### [Overview](#overview-1)
### [System Installation](#system-installation)
### [Steps for Transpilation to ES5](#transpilation-to-es5)
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

## Transpilation to ES5

Follow these [steps](https://github.com/ClearBlade/Machine-Learning-Node-Libraries/blob/master/README.md#steps-for-transpilation-to-es5-1) for transpilation of any NPM package to ES5 so that the NPM package can be imported as a library in the clearblade code engine.

## Usage

- This IPM package consists of a Decision Tree Library that can be imported in the ClearBlade Platform in order to train and test machine learning models on the platform. This library can be used to perform classification and regression.

- The API documentation for this library can be found [here](http://mljs.github.io/decision-tree-cart/)

- The following code snippet loads the Decision Tree library and allows your code to access functionality of the library APIs via the **model** variable.
``` javascript
  var model = getTree();
```

- Once we define the **model** varibale, the Decision Tree library can be implemented as a classifier which is shown below. This library currently supports **gini** as the gain function which determines the best split at a given point of time. The maxDepth parameter determines the maximum depth of the tree.
``` javascript
  var classifier = new model.DecisionTreeClassifier({ 
    gainFunction: "gini", 
    maxDepth: 10, 
    minNumSamples: 3});
 ```
 
 - After configuring the classifier, the training data can be set up as shown below. This data includes Readings recorded from 3 sensors (Power, Temperature and Accelerometer) inside a machine. The training labels are also defined which give information about whether a maintenance was required for a given set of sensor values. ( 0 - Maintenance Not Required; 1 - Maintenance Required )
``` javascript
  var training_data = [
      [1350, 73.4, 0.0683], 
      [1350, 73.4, 0.0685], 
      [1532, 83.1, 0.5272], 
      [1710, 77.3, 1.721], 
      [1200, 76.6, 0.0688], 
      [1820, 82.1, 0.4333], 
      [1421, 75.4, 0.0695], 
      [1800, 95.1, 1.9], 
      [1520, 82.4, 0.4272], 
      [1740, 95.0, 1.715]
  ];
      
  var training_labels = [0, 0, 0, 1, 0, 1, 0, 1, 0, 1];
```

- Using the training data and training labels, train the classifier as follows-
 ``` javascript
  classifier.train(training_dataset, training_labels);
 ```

- Once the classifer is trained, predict for a given set of sensor values, if a maintenance is required or not.
``` javascript
  var test_data = [[1780, 95.5, 1.812]];
  var output = classifier.predict(test_data);
```

- This library can also be used for performing regression tasks as well. The code snippet is shown below:
``` javascript
  var model = getTree();
  
  var reg = new model.DecisionTreeRegression({
    gainFunction: "regression",
    minNumSamples: 3,
    maxDepth: 10
  });
  
  var feature_1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20];
  var feature_2 = [73.4, 76.2, 62.3, 80.2, 100, 94, 88.3, 70, 78, 83, 83, 91, 74, 68, 84, 81, 90, 94, 103, 99];
  
  reg.train(feature_1, feature_2);
  
  var test_data = [[24]]
  var output = classifier.predict(test_data);  
```

- The implementation of this library is done in the [smoke test](https://github.com/ClearBlade/decision-trees/blob/master/code/services/DecisionTreeSmokeTest/DecisionTreeSmokeTest.js) and you can refer to the [**Official Documentation**](https://github.com/mljs/decision-tree-cart) of that library to explore more options that you can use.  

## Assets

### Libraries 

| Library  | Description  | Official Documentation |   
|---|---|---|
| ``` CARTDecisionTreeLibrary ```  | A Library Implementing Classification and Regression Trees  | https://github.com/mljs/decision-tree-cart |

### Code Services

``` DecisionTreeSmokeTest ``` : A code service to show working of Decision Tree Library.
