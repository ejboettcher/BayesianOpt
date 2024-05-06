## Why Design an Experiment

It cost money to run an experiment! 
It also cost money to train algorithms and implement algorithms.
<br>
GPU time is expensive, if you can train and run on a CPU you can save a lot of money.  
How do you know if you can reduce sample size and runtime?

<br>
There are mathematical models you can use to identify what is the number of sample you need to get good results. (see AB testing)

<br>
In addition, not knowing how to adjust your experiment to meet the risk, can **cost you your job** and or the company a lot of money.

<br>
When, Google debuted their Bard, it failed. It cost the company $100B in valuation. This was a high risk demo. 

<br>
You need to know how to adjust your experiments for the risk!

This is where design experimentation comes in. How does one adjust for risk while reducing the cost of running the experiment.  

<br>

One way to reduce cost and risk is to set-up an A/B Test, but that is only good for two (A and B) variables.  
How do you design an experiment when you have lots of variables.  

This is were **Bayesian Optimization** comes in.

---

## Bayesian Optimization

Bayesian optimization is a sequential design strategy for global optimization of black-box functions that does not assume any functional forms.  
  
### How is this Machine Learning?  

Machine Learning Models have multiple hyper-parameters that need to be optimized. The model is a _black-box_ function. Training a ML model can take hours to weeks per configuration. You want to quickly find the hyper-parameters that work well and before  this decade ends!

---

### How is this useful for Software Engineering?

:::: {.columns}  
::: {.column width=60%}  

Say you need to speed up the a web application.  You can control seven parameters.
However, each experiment will take an hour to run. (@sweet)

* BO: would take 2 days to run!
* Grid: at .1 spacing would take 10**7/24 = 417,000 days

#### So it is worth the time to set up, Bayesian Optimization algorithm!

:::   
::: {.column width=38%}  

![](./img/hercules_server.jpg)

:::  
::::

---

## Software Engineering Example

The following example is from "Experimentation for Engineers", by Dr. Sweet (@sweet).

* Optimize a single parameter
* Model the Response Surface
* Optimize over Acquisition Function
  * Expected result - uncertainty (aka Lower Confidence Bound)
* Do a Bayesian Optimization

---

## Bayesian Optimization Flow



![](./img/BO-flow.png)

---

:::: {.columns}  
::: {.column width=49%}  

### Single Parameter

What do we know about the system?


* Single parameter: bounded between 0 - 1
* Uncertainity is constant.

So we have a response surface!  
Let's take a measurement.

:::  
::: {.column width=50%}  

![](./img/init_system.png)

:::  
::::

---

## What measurement should we take?

Let's take a value in the middles.

* Value = 0.5

Result: CPU Time is ~1.5  

So, what happens to our uncertainty.  

* near value = 0.5
* near 0 
* near 1?


---

## Take a measurement


![](./img/baseline.png)


---

## Now what, 

How do we decide on which point to take next?

* Point with the highest uncertainty!

Let's make another measurement.

* Value = 0
* Result = ~1.2

---

![](./img/two_points.png)

---

![](./img/design_next_experiment.png)

## Random Search

## Wait,  

### How is this different than Monte Carlo Method

Monte Carlo method is simular in a since that we randomly select values to run our experiment.  

However, in Bayesian Optimization we feed in past results to know if we are moving in the right direction.

We can see how the systems is converging to an optimized solution.

