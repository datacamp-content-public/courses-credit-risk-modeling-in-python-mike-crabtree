---
title: Insert title here
key: c7d0c9d78ab7fa4b6bdeaf7a8fbb25d0

---
## Logistic Regression

```yaml
type: "TitleSlide"
key: "2b154f14f7"
```

`@lower_third`

name: Michael Crabtree
title: Data Scientist, Ford Motor Company


`@script`



---
## Logistic Regression in Python

```yaml
type: "FullSlide"
key: "dd992832d2"
code_zoom: 85
```

`@part1`
- Classification algorithm used to predict probability of a class
```python
from sklearn.linear_model import LogisticRegression
clf = LogisticRegression(random_state = 0
                         ,solver = 'lbfgs'
                         ,multi_class = 'auto'
                         ,max_iter = 150)
```{{2}}

- Produces decimal values for the probability of a predicted class.  In this case, `loan_status` for **probability of default** {{3}}

```python
array([[9.812e-01, 3.021e-02]])
```{{4}}


`@script`



---
## Probability of Default

```yaml
type: "FullSlide"
key: "9682da0499"
disable_transition: true
```

`@part1`
- The estimated probability that the recipient of the loan will fail to repay the agreed amount.
- One of three primary credit risk components:{{2}}
  1. **Probability of Default (PD)**{{3}}
  2. Loss Given Default (LGD){{4}}
  3. Exposure at Default (EAD){{5}}


`@script`



---
## Probability of Default

```yaml
type: "FullSlide"
key: "17a50ee2a2"
disable_transition: true
```

`@part1`
- Probability of default at a point in time is used to help a lending agency develop a strategy and set aside provisions for **expected loss**

![](https://assets.datacamp.com/production/repositories/4760/datasets/50355cebe2f6d9b3b147a93fd51c6bbf5fae7dd9/Expected_Loss_Curve.jpg){{2}}


`@script`



---
## Logistic Regression for Credit Risk

```yaml
type: "FullSlide"
key: "5fac3bfd84"
```

`@part1`
- The most common algorithm used for predicting **probability of default** (PD)

- Predicted probabilities are easy to interpret and track over time:{{2}}
  - Scorecard development
  - Roll rate analysis (ex: calculating % of accounts whose deliquency got better/worse)
  - Vintage analysis (ex: probability of 90 Days Past Due in next 12 months) 
  
 - This course focuses on **logit** (or log-odds) probabilities{{3}}


`@script`



---
## Prepare Data for Logistic Regression

```yaml
type: "FullSlide"
key: "c1d32f831d"
code_zoom: 85
```

`@part1`
- Discretize Features with `cut()`

```python
bins = [0,35000,60000,100000]
credit_loan_data['inc_bucket'] = pd.cut(
  credit_loan_data['person_income']
  ,bins)
```{{2}}

- Creates a new feature vector that has discretized the income values into buckets{{3}}


`@script`



---
## Prepare Data for Logistic Regression

```yaml
type: "FullSlide"
key: "76cc3b610a"
code_zoom: 85
```

`@part1`
- One-hot encoding with `get_dummies()`

```python
pd.get_dummies(credit_loan_data['loan_intent'])
```{{2}}

- Splits a categorical feature into numeric vectors where the value is 1 if the row contained that value{{3}}

![](https://assets.datacamp.com/production/repositories/4760/datasets/0fcb85bd997558a17e28ae3283a7d7f01b73fc99/one_hot_example.PNG){{3}}


`@script`



---
## Prepare Data for Logistic Regression

```yaml
type: "FullSlide"
key: "2a2be2a979"
code_zoom: 85
```

`@part1`
- Split data into train/test sets with `train_test_split()`

```python
X = credit_loan_data[['person_income'
                      ,'person_home_ownership'
                      ,'loan_intent'
                      ,'loan_amnt']]
y = credit_loan_data[['loan_status']]
```{{2}}

```python
X_train, X_test, y_train, y_test = \
	train_test_split(X, y, test_size=.4,random_state=123)
```{{3}}


`@script`



---
## Implementing Logistic Regression

```yaml
type: "FullSlide"
key: "6365c4f112"
code_zoom: 85
```

`@part1`
- Instantiate a logistic regression classifier
- Train the model on our new training data sets{{2}}

```python
clf = LogisticRegression(random_state=0, solver='lbfgs'
                         ,multi_class='auto')
fit = clf.fit(X_train, y_train)
```{{3}}


`@script`



---
## Let's practice!

```yaml
type: "FinalSlide"
key: "c3ea249b6d"
```

`@script`
So what we covered in this lesson is: the definition of a logistic regression, the definition for probability of default or PD for short, why PD is important to the overall analysis of credit risk, and finally how to set up and implement a logistic regression model whose target is probability of default.
Let's hop over to some programming exercises and use our new set of skills!

