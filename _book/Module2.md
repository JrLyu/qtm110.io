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
