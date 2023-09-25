# Experiments

## Randomization and Noise
- Random Assignment
  - If units are assigned randomly
  - Then no reason to expect differences: T/C groups should have same characteristics, including potential outcomes (in particular, $$Y_0$$ and $$Y_1$$).
  - Formally, Treatment and Control groups should have the same characteristics in **expectation**.
    - But expectation is a population concept
    - And all we can see is a (finite-size) sample
- Why do we do an experiment?
  - Fundamental problem of causal inference:
    - Never observe both $$Y_1$$ and $$Y_0$$ for a unit
  - Instead, the best we can do is compare $$Y_0$$ among one group to $$Y_1$$ in another group: 
  $$
  E[Y_0\mid T=1]\neq E[Y_0\mid Y=0]\rightarrow\text{Bias}
  $$
  - How do experiments help?
  $$
  E[Y_0\mid T=1]=E[Y_0\mid Y=0]\rightarrow\text{No Bias}
  $$
  - How do experiments achieve this?
    - **Random Assignment**
- Standard Errors: 
  - Standard error depends on $$\text{Cov}(Y_1,Y_0)$$
    - Not observable (just like $$p$$ - the real porportion -was not)
    - Some subtleties to the calculating $$SE$$
  - One common approach: 
  $$
  \widehat{SE}=\sqrt{\dfrac{\widehat{\text{Var}(Y_0)}}{N-m}+\dfrac{\widehat{\text{Var}(Y_1)}}{m}},
  $$
  where $$N$$ is the size of sample, $$m$$ is the number of observations assigned to treatment, and $$\widehat{\text{Var}(V_0)}$$ and $$\widehat{\text{Var}(V_1)}$$  are estimated in sample.
    - Larger sample (increase $$N$$) leads to lower standard error, meaning more precision
    - If variance of $$Y_1$$ and $$Y_0$$ (treatment and control group outcomes) are similar, then splitting sample evenly between treatment and control minimizes $$SE$$.
    - Lower variance in outcomes means more precision.
      - If we are looking at samples or outcomes with less natural variable (noise), then we will have more precise inferences. 

## Confidence Intervals
> **Point Estimates**: The single **statistic** we get from a study or analysis is called a *point estimate*.
- Using our calculated SE, we can construct an interval of possible true values that would be *consistent with* our estimate. 
> **Confidence Interval (CI)**: a range representing our uncertainty about our point estimate due to **random error/noise**.
- We can consider CI as providing a range of possible **true values** that would be *consistent with* our estimate. 
  - "How consistent" is defined by the **width** of a CI - most commonly choose to be 95%.
- **95% Confidence Interval**: assuming no bias, 95% of the intervals constructed in this way around an estimate will contain the true value.
  - Common misinterpretation: there is a 95% chance the true value lies within our CI.
    - Philosophical explanation: the truth is fixed: it's either in the interval (100%) or not (0%)
    - Mathematical explanation: if we assume that our estimand could be literally anything, and all possibilities are equally likely, the two are numerically equivalent.
  - CI relies on estimated SE from the sample, which may differ
  - "95%" is a statement about the long-run "coverage" of Ci, not the likely range of the truth itself. 
- Constructing Confidence Intervals:
  - **Central Limit Theorem**: If we repeat a study/analysis/experiment a zillion times, the value of many of the statistics we get will follow a **normal distribution**. 
  - **Normal distribution**: values of some random variables (like heights of people/means of samples) follow a normal distribution
    - The truth will be the mean of the normal distribution
  - In a normal distribution, 95% of the probability lies within $$\approx$$ 2SEs of the mean
    - meaning 95% of our samples should lie within 2SEs of the truth
    - so if we add $$\pm$$ 2SEs to each side of our estimate, 95% of the time that interval should contain the truth
  - Common use in short: 
  $$
  95\%\text{ CI}=\text{Point Estimate}\pm2\times\text{SE}
  $$
  - Researchers often report a 95% confidence interval for various quantities (means, regression coefficients, proportions) the same way: 
  $$
  [\text{Estimate}-2\times\text{SE},\text{Estimate}+2\times\text{SE}]
  $$
  - What contributes to high SE? 
    - Small sample size
    - High variance in outcomes $$(Y_0,Y_1)$$.

## Hypothesis Testing Introduction
- Justification: why we need hypothesis testing?
  - Sometimes, we want to make a decision about whether we observed data that are different from some important values. 
- Hypothesis Testing:
  - Suppose that there is not effect of the treatment watsoever. I.e., $$E[Y_1-Y_0]=0.$$
  - What is the probability that we would have gotten an estimate as big as ours just by chance alone?
    - We will call this number the ***p-value***.
    - If that number (p-value) is really small, then we can be fairly confident that the treatment really does have an effect (because it is very unlikely that we would have gotten this result just be chance).
    - If the number is big, we are much less confident (because there is a good change that we could have gotten this result by change, even if there is really no effect).
  - Test our data to see if it is *consistent with* the **null hypothesis** or not.
    - consistnet: are our results "too weird" for the null hypothesis to make senze?
    - consistent: what is the chance (porbability) we would get a result at least as "extreme" as what we observed due to random error/chance/noise, assuming the null hypothesis is true and there is no biase? -- p-value
- P-Values and Magical Thresholds
  - Special cutoffs:
    - "reject the null hypothesis" of no effect if $$p<.05$$
    - "fail to reject the null hypothesis" of effect if $$p>.05$$
  - When results are represented in a table, stars (\*, \*\*, \*\*\*) next to the estimates are used to indicate that there are some "statistical significance."
  - p-value is a very useful statistic, but it's dangerous to stress about particular significance thresholds. 
  - Remember that p-value means the odds of getting the same result if the true effect is zero
    - **does not** mean that the finding is true with probability $$1-p$$.
  - The naive rule of thumb that $$p<.05$$ means that the finding is true and $$p>.05$$ means that it is false has done a lot of damage over the years, and we make lots of errors on both sides of that threshold.
- Calculating p-values:
  -  Analytical Approach: CLT and SEs
     -  CLT tells us that with sufficiently large sample, the distribution of our estimates (from theoretical replications of an anlysis) approaches a normal distribution
        -  Thus, we can assume our single result was drawn from a normal distribution with a mean defined by the null hypothesis ($$Y_1-Y_0=0$$) and standard deviation equal to our sample SE.
        -  Ask: how many SEs away from the null hypothesis is our estimate?
     - Take away: Large effects (differences between null and observed data) and/or low SEs/high precision for bigger $$N$$, and thus lower p-values.
  - Computational Approach: Permutation Tests