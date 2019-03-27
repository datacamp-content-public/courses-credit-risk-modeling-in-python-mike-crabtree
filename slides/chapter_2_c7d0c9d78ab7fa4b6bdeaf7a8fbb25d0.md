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
## Outline

```yaml
type: "FullSlide"
key: "20c291a668"
```

`@part1`
- Introduce logistic regression
- Mention that it's often used for predicting PD
- Introduce why PD is used and what it impacts
- Short demo of logistic regression in python (code snippet)


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

- Produces decimal values for the probability of a predicted class.  In this case, `loan_status` of Default or Non-default (1 or 0){{3}}

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
  1. **Probability of Default**
  2. Loss Given Default
  3. Exposure at Default


`@script`



---
## Probability of Default

```yaml
type: "FullSlide"
key: "17a50ee2a2"
disable_transition: true
```

`@part1`
- Probability of default at a point in time and over time are used to help a lending agency develop a strategy and set aside provisions for expected loss (given default)


`@script`



---
## Logistic Regression for Credit Risk

```yaml
type: "FullSlide"
key: "5fac3bfd84"
```

`@part1`
- Common algorithm used for predicting **probability of default** (PD)

- Predicted probabilities are easy to interpret and track over time{{2}}
  - Scorecard development
  - Roll rate analysis (ex: days past due)
  - Vintage analysis (ex: probability of 90 DPD in next 12m, Basel II)


`@script`



---
## Probability of Default

```yaml
type: "TwoColumns"
key: "29ec076675"
```

`@part1`
- What is PD.  The estimated probability that the recipient of the loan will fail to repay the agreed amount.
- Why PD is used.  Probability of default at a point in time and over time are used to help a lending agency develop a strategy and set aside provisions for expected loss (given default)


`@part2`
- It's impact (number of loans, loss at default, etc)
- Curve showing risk and population (strategy)


`@script`



---
## Prepare Data for Logistic Regression

```yaml
type: "FullSlide"
key: "c1d32f831d"
```

`@part1`
1. Discretizing Features
2. One hot encoding
3. Test/train split
4. Code snippet


`@script`



---
## Logistic Regression PD Example

```yaml
type: "FullSlide"
key: "6365c4f112"
```

`@part1`
- Code snippet example
- Output explanation


`@script`



---
## Let's practice!

```yaml
type: "FinalSlide"
key: "c3ea249b6d"
```

`@script`


