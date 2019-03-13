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
That's where gridsearch comes into play! (15s)


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
Here is an example of a logistic regression in Python using ScikitLearn like we used in previous exercises.
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
The first of those simple parameters is going to be C.  C is the parameter which is used for inverse regularization.
This is a value that is used to help us prevent our model from overfitting to the training set as is the case with most machine learning models.  Remember, the smaller the C value, the stronger the regularization.


---
## Logistic Regression Hyperparameters

```yaml
type: "FullSlide"
key: "7b815b8525"
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4760/datasets/dcd6fc37e3115ce7d962e56cb87900de5e3d49a9/logi_reg_maxiter.PNG)

| Parameter     | Usage           |
| ------------- |:-------------:|
| C             | Inverse regularization parameter|
| max_iter    | Max iterations for solvers to converge      |


`@script`
Next is the max iter parameter which is used to control the maximum number of iterations taken for the solvers to converge.  The solver in this case is the lbfgs you see in the code, which represents one of several quasi-Newton methods available to algorithms in Scikit Learn.


---
## Logistic Regression Hyperparameters

```yaml
type: "FullSlide"
key: "2166e7d1ab"
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4760/datasets/1dfc5741e700d7e2ba3204377426644f1f0be31b/logi_reg_randstate.PNG)

| Parameter     | Usage           |
| ------------- |:-------------:|
| C             | Inverse regularization parameter|
| max_iter    | Max iterations for solvers to converge      |
| rand_state | Seed for random shuffling      |


`@script`
Last, but not least, is the random state parameter.  This is an integer used as a seed for the pseudo random shuffling of the data prior to fitting.  This is not generally used for the lbfgs solver, but it gives us an opportunity to play with searching through more values using gridsearch.


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
I've mentioned grid search several times now, but what exactly is it?
Grid search is a method within Scikit learn which allows us to pass in a machine learning model as well as a dictionary of parameters to figure out which combination works best.
It is able to do so, because grid search will implement both a fit and score method.
The grid search method is generally brought in my importing model selection from scikit learn.


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
Now, the first thing I like to do is create some simple arrays of the different values I want grid search to choose from.
Here, I have created some simple ones for each of the parameters we are going to use: c, max iter, and random state.  One fun thing to note is when establishing a range of c values, it's easy to use the logspace function from numpy to generate evenly spaced values in the log space.
Once all of those are created, we can then create our dictionary of hyperparameters to use in our grid search.


---
## Using GridSearch()

```yaml
type: "FullSlide"
key: "95bf2beddc"
code_zoom: 85
```

`@part1`
An Example of the use
```python
clf_logistic = GridSearchCV(m_logistic
                            ,hyperparameters
                            ,cv=5
                            ,verbose=0)
```


`@script`



---
## Let's practice!

```yaml
type: "FinalSlide"
key: "3824076083"
```

`@script`


