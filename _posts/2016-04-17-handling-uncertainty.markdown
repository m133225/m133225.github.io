---
layout: post
title:  "Dealing with uncertainty"
date:   2016-04-17 12:00:00 +0800
categories: probability uncertainty
---
So far, we have discussed the basic idea behind motion planning.
But the environment is constantly changing, and always has its uncertainty. How do we account these uncertainties into our planning?

In general, we can model the movement of a robot in the following cycle:

1. The robot moves. This increases the uncertainty of the environment.
2. Using the movement (control input) in step 1, predict the new environment.
3. Use sensors to gather information about the new environment
4. Using the new information, update the model of the new environment, which reduces the uncertainty (then go back to (1))

Without covering on the different types of probability (that were covered in the slides), let's move on directly to the solution: Bayes' Filter, also known as [Recursive Bayesian estimation](https://en.wikipedia.org/wiki/Recursive_Bayesian_estimation).

Bayes' Filter simply adds on to the above model. It uses the known previous state, the latest control input and sensor information, to predict the new environment.
i.e. p(x<sub>t</sub>| z<sub>1:t</sub>, u<sub>1:t</sub>) where x<sub>t</sub> is the new environment.

If you would like a more detailed explanation with concrete examples, click [here](http://people.ufpr.br/~danielsantos/ProbabilisticRobotics.pdf) and start from page 23!


Another important assumption that we can make is that the Markov Property holds. In short, states are 'atomic' rather than 'sequential'. Each state is conditionally independent on its previous states.

Upon closer inspection, one should realise that this assumption is heavily flawed. There are many ways in which this assumption can be violated. For example, factors such as dynamics in the environment are not in the state representation. In this case, the probability model (and state) does not account for these uncertainties, and they will make the new state dependent on the old ones.

However the case, making this assumption actually works well in practice! Which is similar to how [Naive Bayes classifier](https://en.wikipedia.org/wiki/Naive_Bayes_classifier) works. These assumptions simplifies the problem and reduces the amount of computation required.

<hr/>

We can then consolidate the above into a Transition Model.  
Prediction = integral of p(x<sub>t</sub>|x<sub>t-1</sub>, u<sub>t</sub>) p(x<sub>t-1</sub>|z<sub>1:t-1</sub>, u<sub>1:t-1</sub>) wrt d<sub>x-1</sub>

We can then update the probability required for the next iteration:  
p(x<sub>t</sub>|z<sub>1:t</sub>, u<sub>1:t</sub>) = g(z<sub>t</sub>|x<sub>t</sub>)p(x<sub>t</sub>|z<sub>1:t-1</sub>,u<sub>1:t</sub>)/integral(g(z<sub>t</sub>|x<sup>'</sup><sub>t</sub>)p(x<sup>'</sup><sub>t</sub>|z<sub>1:t-1</sub>,u<sub>1:t</sub>))d(x<sup>'</sup><sub>t</sub>)
