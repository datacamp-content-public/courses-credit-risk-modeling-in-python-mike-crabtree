---
title: Insert title here
key: 50d2db29b3db8d93542da0d39fcc8cb0

---
## Easy Hyperparameters with GridSearch

```yaml
type: "TitleSlide"
key: "fc62b4f5d9"
```

`@lower_third`

name: Michael Crabtree
title: Data Scientist, Ford Motor Company


`@script`
In the previous exercises, we used a logistic regression to compute probability of default and analyzed the performance.
We set some of the hyperparameters to specific values, but what if we want to try a range of different values?
That's where gridsearch comes into play!


---
## Logistic Regression Hyperparameters

```yaml
type: "FullSlide"
key: "8dc2d60288"
code_zoom: 85
disable_transition: true
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4760/datasets/9e1b32b308b688ee903b5ff0aee5455be1c5276e/logi_reg_blank.PNG)


`@script`
Here is an example of a logistic regression in Python using ScikitLearn complete with some set hyperparameters.
While not all hyperparameters are good candidates for grid search, we can use a set of simple ones to help us optimize the performance of our model.


---
## Logistic Regression Hyperparameters

```yaml
type: "FullSlide"
key: "55ab6f4abe"
disable_transition: true
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4760/datasets/cb137dc0a088452d41dc3f41a92199dbfb1a3be9/logi_reg_c.PNG)

| Parameter     | Usage           |
| ------------- |:-------------:|
| C             | Inverse regularization parameter|


`@script`
The first of those hyperparameters is going to be C.  C is the parameter which is used for inverse regularization.
This is a value that is used to help us prevent our model from overfitting to the training set as is the case with most machine learning models.  Remember, the smaller the C value, the stronger the regularization.


---
## Logistic Regression Hyperparameters

```yaml
type: "FullSlide"
key: "7b815b8525"
disable_transition: true
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4760/datasets/dcd6fc37e3115ce7d962e56cb87900de5e3d49a9/logi_reg_maxiter.PNG)

| Parameter     | Usage           |
| ------------- |:-------------:|
| C             | Inverse regularization parameter|
| max_iter    | Max iterations for solvers to converge      |


`@script`
Next is the max iter parameter, which is used to control the maximum number of iterations taken for the solvers to converge.  The solver in this case is the lbfgs you see in the code.


---
## Logistic Regression Hyperparameters

```yaml
type: "FullSlide"
key: "2166e7d1ab"
disable_transition: true
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4760/datasets/1dfc5741e700d7e2ba3204377426644f1f0be31b/logi_reg_randstate.PNG)

| Parameter     | Usage           |
| ------------- |:-------------:|
| C             | Inverse regularization parameter|
| max_iter    | Max iterations for solvers to converge      |
| rand_state | Seed for random shuffling      |


`@script`
Last, but not least, is the random state parameter.  This is an integer used as a seed for the pseudo random shuffling of the data prior to fitting.  While this is not generally used for the lbfgs solver, it gives us an opportunity to play with searching through more values using gridsearch.


---
## What is GridSearchCV?

```yaml
type: "FullSlide"
key: "2b56850ca0"
code_zoom: 85
```

`@part1`
- Exhaustive search over a dictionary of parameters
- Implements `fit` and `score` from Scikit Learn
- Imported from `model_selection`
```python
from sklearn.model_selection import GridSearchCV
```


`@script`
So I've mentioned grid search several times now, but what exactly is it?
Grid search is a method within Scikit learn which allows us to pass in a machine learning model as well as a dictionary of hyperparameters to figure out which combination of those hyperparameters works best.
Grid search is able to find the best combination because it will implement both a fit and score method.
The grid search method is imported from model selection from scikit learn.


---
## Setting the Hyperparameters to Use

```yaml
type: "TwoRows"
key: "9ffb5572cc"
hide_title: false
code_zoom: 85
```

`@part1`
Create arrays of parameters
```python
#Regularization Parameter
C = np.logspace(0, 4, 60)
#Max Iterations Parameter
max_iter = [100,200,300]
#Random State Parameter
random_state = [0,1,2,3,4]
```


`@part2`
Create a dictionary of the arrays
```python
hyperparameters = dict(C = C
                       ,max_iter = max_iter
                       ,random_state = random_state)
```


`@script`
The first thing I like to do is create some arrays of the different values I want grid search to choose from.
Here, I have created some for each of the parameters we are going to use: c, max iter, and random state.  One fun thing to note is when establishing a range of c values, it's easy to use the logspace function from numpy to generate a set number of evenly spaced values in the log space.
Once all of those are created, we then use the dict() function to create our dictionary of hyperparameters to use in our grid search.


---
## Using Grid Search

```yaml
type: "FullSlide"
key: "95bf2beddc"
code_zoom: 85
```

`@part1`
Implement grid search with our logistic regression using `GridSearchCV()`
```python
clf_logistic = GridSearchCV(m_logistic
                            ,hyperparameters
                            ,cv=5
                            ,verbose=0)
```
| Attributes    |
| ------------- |
| `cv_results_`   |
| `best_estimator_`|


`@script`
Now that our dictionary of hyperparameters has been created, we can simply pass them into the GridSearch() function along with: the model, the parameter for cross validation folds, and the verbose option parameter.
This returns a gridsearch object which has many useful attributes such as: cv results to see things like parameters and metrics for the object, and best estimator to see more details about the model chosen by grid search.  These output a dictionary which can easily be made into a Pandas dataframe for further analysis.


---
## Let's practice!

```yaml
type: "FinalSlide"
key: "3824076083"
```

`@script`
So, we've learned: what hyperparameters from the logistic regression we are going to use gridsearch on, how to create the dictionary of those hyperparameters, and implement them using the GridSearch function.
Now let's go through some programming exercises to use this new skill.  Good luck!

