# Module 5: Bias and Noise

## Confounder
> **Confounder**: a confounder is something directly affects both treatment status and outcome. 
- Other terms: 
  - Common Cause: Common cause of outcome and treatment
  - Apples-to-oranges: Groups are not comparable in potential
  - Omitted Variable Bias (OVB): There is a missing variable
- Three conditions make a variable a confounder:
  - Associated with the **treatment**
  - Cause of the **outcome** separate from any effects it has one the **treatment**
  - Not along a causal path between **treatment** and **outcome** (i.e., not a **mediator/mechanism**).
  - That is, it's not part of a casual chain like Exposure -> "Confounder" -> Outcome. It is something outside the casual chain.
- Confounding is strictly a problem for **causal questions**.
  - It makes things look associated when there is no causal effect.
  - Irrelevant for description or prediction

## Average Treatment Effects and Bias
- The Ideal
  - Potential Outcomes
    - $$Y$$: the outcome we observe
    - $$T$$: a binary variable indicating if treatement is taken
  - $$Y_{1_i}=$$ outcome observed for unit $$i$$ if $$T=1$$.
  - $$Y_{0_i}=$$ outcome observed for unit $$i$$ if $$T=0$$.
  - $$Y_{1_i}-Y_{0_i}$$ is the casual effect of $$T$$ for unit $$i$$ - cannot be observed
  - The **Average Treatement Effect (ATE)** is $$E[Y_{1_i}-Y_{0_i}]$$.
  - We can also think about ATE's for sub-populations $$E[Y_{1_i}-Y_{0_i}\mid Z]$$
  - The casual effect among those who got the treatement: $$\text{ATT}=E[Y_{1_i}-Y_{0_i}\mid T=1]$$
    - Expectations are linear, so we can re-write the formula as $$E[Y_{1_i}-Y_{0_i}\mid T=1]=E[Y_{1_i}\mid T=1]-E[Y_{0_i}\mid T=1]$$
    - However, $$E[Y_{0_i}\mid T=1]$$ is not an observable quantity. It is counterfactual. 
  - How does this quantity of interest relate to the quantity that we can estimate? 
    - What we can estimate: $$E[Y_1\mid T=1]-E[Y_0\mid T=0]$$.
      - This is our estimate -> a correlation
    - What we are interested in: $$E[Y_1\mid T=1]-E[Y_0\mid T=1]$$
      - This is our estimand -> a causal effect.
    - Since $$\text{Correlation}=\text{True Effect}+\text{Bias}$$ (ignore noise for now), we get 
  $$
  E[Y_1\mid T=1]-E[Y_0\mid T=0]=E[Y_1\mid T=1]-E[Y_0\mid T=1]+\text{Bias}
  $$
    - So, we have
  $$
  \text{Bias}=\text{What we estimate}-\text{What we are interested in}
  $$
  $$
  \begin{aligned}
  \text{Bias}&=E[Y_1\mid T=1]-E[Y_0\mid T=0]-E[Y_1\mid T=1]+E[Y_0\mid T=1]\\&=E[Y_0\mid T=1]-E[Y_0\mid T=0]
  \end{aligned}
  $$
    - In other words, if these two groups have different $$Y_0$$'s, then we have **bias**. 
    - The difference between average outcomes among the control group and the average outcome that we would have obtained among the treatment group had they not gotten the treatment. The bias is non-zero whenever $$E[Y_0\mid T=1]\neq E[Y_0\mid T=0].$$
  
## Randomness and Omniscient Powers
- What does "apples-to-apples" mean?
  - For purpose of estimating the ATT, we need no difference of the following properties between treatment and control groups 
    - on average
    - in $$Y_0$$
  - Note that in general, $$\text{ATT}\neq\text{ATE}$$. For comparison of the treatment and control to give an unbiased estimate of the ATE, we need a similar conditon on $$Y_1$$.
- What we would like to do: Randomize
  - If we could randomize, then the only difference between units would be if they received treatment
  - In particular, units would have the same potential units if we randomly assigned to two groups: 
    - $$E[Y_0\mid A]$$ - expected outcome if not treated for population A
    - $$E[Y_0\mid B]$$ - expected outcome if not treated for population B.
    - $$E[Y_0\mid A]-E[Y_0\mid B]=0$$
  - Just let $$A=$$ Treated and $$B=$$ Untreated, we have 
  $$
  \text{Bias}=E[Y_0\mid T=1]-E[Y_0\mid T=0]=0.
  $$
  - Confounding: DAGs: 
    - **Directed Acyclic Graph (DAG)** are very useful for casual questions and help to identify confounding and other biases.
    - Graph = some points connected by lines
    - Directed = those lines are arrows that indicate causation
    - Acyclic: cannot follow arrows to get back where it is started. 