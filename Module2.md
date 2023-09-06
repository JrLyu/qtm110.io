# Module 2: Correlation Intuitive Introduction

## Basic Description
> ***Descriptive Questions***: Questions that describe the world as it is. 
- How much or many of something exists among certain people/in certain places/at certain times.
- Variation by person, place, and time.
- Often interesting on their own: frequently undervalued and may serve as start of future investigations.
- Often challenging - but difficulty frequently underestimated. 

> ***Algorithms***: Rules that allow us to input data and get outcomes (usually a number).

### Three Definitions of Average
- Arithmetic Mean: sum and divide by number.
- Median: observation that divides ordered data in half.
  - For a data set $$x$$ of $$n$$ elements, ordered from smallest to greatest, 
    - if $$n$$ is odd, $$\text{median}(x)=x_{(n+1)/2}$$
    - if $$n$$ is even, $$\text{median}(x)=\dfrac{x_{(n/2)}+x_{(n/2)+1}}{2}$$
- Mode: the most common observation.

## Correlation Intuitive Introduction
> ***Correlation***: the extent to which two features of the world tend to occur to together.
- Could be two binary features
- Could be two discrete features
- Could be two continuous features
- Or any mix of the above. 

### Sign of Correlation
- Positive correlation: 
  - Two features move together/tend to occur together
  - Two features move in opposite directions/tend not to occur together

*Note: we can often transform a positive to negative and vice versa by redefining.*

- Correlation of no relationship: 
  - Uncorrelated (zero correlation): there is no discernable relationship. 

*Sometimes two variables will be "spuriously correlated," meaning two random variables are correlated by chance.*

| As $$X$$ rises, $$Y$$... | Type of Correlation/Covariance | Value of Correlation |
|:---:|:---:|:---:|
| Rises | Positive | $$\text{corr}(X,Y)>0$$ |
| Does Not Change | None (variables are uncorrelated or **independent**) | $$\text{corr}(X,Y)=0$$ |
| Falls | Negative | $$\text{corr}(X,Y)<0$$ |

## Formalizing Correlation
- **Covariance** is one statistic to measure correlation: 
$$
\text{cov}(X,Y)=E\Big[\big(X-\mu_X\big)\big(Y-\mu_Y\big)\Big],
$$ 
where $$E$$ stands for the expectation, or average, $$\mu_X$$ stands for the mean of $$X$$, and $$\mu_Y$$ is the mean of $$Y$$.
  - A positive covariance means the two variables are moving in the same direction.
  - Covariance is unit sensitive, meaning change of unit will affect the magnitude of covariance. 

- **Correlation Coefficient** is another common statistic to measure correlation: 
$$
\text{corr}(X,Y)=\dfrac{\text{cov}(X,Y)}{\sigma_X\sigma_Y},
$$ 
where $$\sigma_X$$ and $$\sigma_Y$$ are the **standard deviations** of $$X$$ and $$Y$$, respectively.
  - The formula for standard deviation is 
$$
\sigma_X=\sqrt{E\big[(X-\mu_X)^2\big]}.
$$
  - By deviding the product of standard deviations, we are essentially normalizing covariance so that it lies between $$-1$$ and $$1$$. Therefore, we can evaluate and compare the "strength" of correlation. 
  - A positive correlation will result in a correlation coefficient $$>0$$.
  - If $$\text{corr}(X,Y)=1$$, then there is a perfect linear positive relationship between them, which can be modeled using $$Y=\beta\times X+\alpha,$$ with $$\beta>0$$.
  - If $$\text{corr}(X,Y)$$ is positive but less than $$1$$, there is not a perfect linear relationship between them.
  - If $$\text{corr}(X,Y)=-1$$, then there is a perfect linear negative relationship between them, which can be modeled using $$Y=-\beta\times X+\alpha$$, with $$\beta>0$$. 
  - If $$\text{corr}(X,Y)$$ is negative but greater than $$-1$$, then there is not a perfect linear relationship between them. 
  - Change of unit does not change the value of correlation coefficient.

### Comparison between Covariance and Correlation
- Range: 
  -  Covariance: $$(-\infty,\infty)$$
  -  Correlation: $$[1,1]$$

| As $$X$$ rises, $$Y$$... | Type of Correlation/Covariance | Value of Covariance | Value of Correlation |
|:---:|:---:|:---:|:---:|
| Rises | Positive | $$\text{cov}(X,Y)>0$$ | $$0<\text{corr}(X,Y)\leq1$$ |
| Does Not Change | None (variables are uncorrelated or **independent**) | $$\text{cov}(X,Y)=0$$ | $$\text{corr}(X,Y)=0$$|
| Falls | Negative | $$\text{cov}(X,Y)<0$$ | $$-1\leq\text{corr}(X,Y)<0$$|


### More on Correlation
- Magnitude of the relationship
  - We can normalize by variance in $$X$$ to get "slope"/regression coefficient: 

$$
\beta=\dfrac{\text{cov}(X,Y)}{\sigma_X^2}
$$

  - This number tells us, descriptively, how much $$Y$$ changes, on average, as $$X$$ increases by one unit. 
  - So if relationship is near linear but very weak, we would get a small number.

- Limits of Correlation Coefficients: 
  - Do not indicate strength of association very well: 
    - $$r$$ gives us an overall measure of how close the dots (observed data) are to the line (best-fit-line)
    - $$r$$ does not tell us how much $$Y$$ changes with a unit change in $$X$$.
  - Cannot generalize or make predictions
    - Must know equation (slope) of best fit line to make predictions.
  - Assumes **linear** relationships -- can't capture other associations
    - $$r\approx0$$ does not always mean no association. 
    - Always plot the data to see its shape. 

## Uses of Correlation
- Why we measure correlation? 
  - Description (Easy)
  - Prediction (Harder)
  - Causal Inference (Hardest)

- Step 0: Data and Measurement: 
  - Before we can even describe relationships between variables, we need to make sure we have good variables. 
  - Two parts: concept validity & Accuracy

- Description: 
  - No additional assumptions needed (Good)
    - Just need to assume our data is accurate and reflects concept
  - Might be of interesting in and of its own
  - More likely a starting point of a deeper question

- Predictive Questions: 
  - Prediction Assumptions 1: 
    - From data we predict from (training data) to what we predict to (prediction)
  - Prediction Assumptions 2:
    - Appropriate Model: Linearity 

- Unbiased Prediction: 
  - **Unbiased**: would my prediction be right (on average) if I was able to make 1000s of predictions
  - Needs:
    - Linear relationship
    - Representative Sample
    - Forecast in our range of data

- Causal Inference:
  - How does changing a feature of the world change some other feature? 
  - There are situations where even knowing the causal story might not be enough for these predictions due to adaption

- Review: Description, Prediction and Explanation
  - Correlations can be used to:
    - Describe an observable phenomenon
    - Predict some outcome given observations
    - Understand the phenomenon, to the point where we can manipulate it purposefully.
  - As we move through these uses, we need to make more assumptions and/or have better research design.

## Linearity
- Lots of relationships between data are non-linear
- One easy solution for much of what we do: transform variables.
- Another easy solution is to split the problem up: 
  - Everything is linear if you look close enough
- For a really important class of problems linearity always applies: binary variable
  - Treatment versus control
- Other more sophisticated ways
  - Lot of the success of Machine Learning (ML) etc. is dealing with interactions and non-linearity in higher dimensions
  - Also a lot of classical statistical solutions to non-linearity

## Candidates for Causation
- A causal effect is a change in one feature of the world that results from a change in another feature of the world.
- Causation Definition 1 -- Correlation: Can we predict one quantity by knowing another, using a known correlation between the two? 
  - Reasoning: if we understand the cause, we should be able to forecast the outcome.
  - However, **associations need not to be causal**
    - Problem 1: Correlation w/o Causation
      - Reverse Causality
      - Common Cause
    - Problem 2: Direction
      - Correlation of $$X$$ with $$Y$$ is the same as $$Y$$ with $$X$$. 
- Causation Definition 2 -- Regularity: Every time $$X$$ happens, $$Y$$ happens
  - This definition addresses the issue of direction. 
  - Problem 1: Deterministic
  - Problem 2: Trivial relationships
- Causation Definition 3 -- Temporal Order: The Arrow of Time. i.e., Event $$A$$ can cause event $$B$$ only if event $$A$$ precedes event $$B$$ in time. 
  - Problems Prediction $$\neq$$ Causation
- Causation Definition 4 -- Physical Connection
  - We can experience with our sense. Maybe we should require that causes physically produce effects through some observable mechanism
  - Problem: 
    - Hard to verify in many cases
    - Requires ever more convoluted stories
- Causation Definition 5: Counterfactual Dependence
> **Causation (Conterfactual Dependence)**: $$X$$ *causes* $$Y$$ if and only if 
> - $$Y$$ occurs when $$X$$ occurs, and
> - $$Y$$ would not have occurred in the counterfactual world where $$X$$ did not occur. 

## Counterfactual Dependence
- The counterfactual dependence model is also known as Rubin Causal Model (RCM) or Neyman-Rubin Causal Model. 
- Definition Revisit: 
  - Let $$T$$ be binary evenet ($$T$$ for Treatment)
    - $$T=1$$: Treated
    - $$T=0$$: Untreated
  - Let $$Y$$ be some outcome of interest
    - $$Y_1\equiv Y$$ in the counterfactual world where $$T=1$$.
    - $$Y_0\equiv Y$$ in the counterfactual world where $$T=0$$.
  - $$T$$ causes $$Y$$ if and only if $$Y$$ occurs when $$T$$ occurs, and $$Y$$ would not have occurred in the counterfactual world where $$T$$ did not occur. 
- Individual Treatment Effect:
  - Causal Effect on $$T$$ on $$Y$$ is $$Y_1-Y_0$$
    - $$T$$ has a causal effect on $$Y$$ if and only if $$Y_1-Y_0\neq0$$
    - Problem: $$Y_1-Y_0$$ is not observable.
    - Many events can be causes of the same effect in this sense
- Potential Outcomes Cheatsheet
  
| Quantity | $$E[Y_1\mid T=1]$$ | $$E[Y_0\mid T=0]$$ | $$E[Y_1\mid T=0]$$ | $$E[Y_0\mid T=1]$$ |
|:---:|:---:|:---:|:---:|:---:|
| Description | Average outcome in treated group | Average outcome in untreated group | Average outcome in the untreated group if they'd been treated | Average outcome in the treated group if they'd been untreated |
|Factual (Observed) or Counterfactual? | Factual | Factual | Counterfactual | Counterfactual |

## Limits to Counterfactual Dependence
- The fundamental Problem of Causal Inference
  - A most one of $$Y_1$$ or $$Y_0$$ is observable.
  - If $$T=1$$, then we only see $$Y_1$$
  - If $$T_0$$, we only observe $$Y_0$$
  - Never get to observe $$Y_1-Y_0$$: the fundamental problem of causal inference
- How will get purchase on the problem? 
  - The goal is to get groups that are comparable to each other, but differ in whether they get the treatment or not
    - Comparable in what sense? In the sense that they have the same potential outcomes - *Apples to Apples*
    - Differ in treatment due to experimental manipulation or natural experiments
    - All of this will be ON AVERAGE, so we will be restricted to talking about Average Causal Effect (or Average Treatment Effects)
- Coherent and Incoherent Causal Questions: 
  - Infinite number of factors that, had they been different, would have changed the real world.
  - Solution: Narrow Question
- Answerable and Unanswerable Causal Questions
  - Questions are unanswerable due to the fundamental problem of causal inference
  - As for unanswerable questions, we will instead talk about the Average Treatment Effect or the Average effects for a particular population of interest
    - Does not mean one grand effect for all.