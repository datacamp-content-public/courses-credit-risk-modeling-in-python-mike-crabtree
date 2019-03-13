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
```

`@part1`
Previously used hyperparameters:
- C : Inverse of the regularization strength
- max_iter : Maximum number of iterations taken
- random_state : Seed of the RNG for shuffling


`@script`
While not all hyperparameters are good candidates for grid search, we can use a set of simple ones to help us optimize the performance of our model.
For the next set of exercises we will be using the following hyperparameters.


---
## What is GridSearchCV?

```yaml
type: "FullSlide"
key: "2b56850ca0"
code_zoom: 85
```

`@part1`
Here is some text

```python
import numpy as np
from sklearn.model_selection import GridSearchCV
```
Here is some more text


`@script`



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


