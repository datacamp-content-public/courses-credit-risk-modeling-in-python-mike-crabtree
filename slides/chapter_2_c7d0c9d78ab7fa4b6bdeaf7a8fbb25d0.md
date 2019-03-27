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

- This course focuses on **logit** (or log-odds) probabilities{{2}}

- Predicted probabilities are easy to interpret and track over time:{{3}}
  - Scorecard development
  - Roll rate analysis (ex: calculating % of accounts whose deliquency got better/worse)
  - Vintage analysis (ex: probability of 90 Days Past Due in next 12 months)


`@script`



---
## Prepare Data for Logistic Regression

```yaml
type: "FullSlide"
key: "c1d32f831d"
code_zoom: 85
```

`@part1`
1. Discretize Features with `pd.cut()`
```python
bins = [0,35000,60000,100000]
credit_loan_data['inc_bucket'] = pd.cut(
  credit_loan_data['person_income']
  ,bins)
```


2. One-hot encoding
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


