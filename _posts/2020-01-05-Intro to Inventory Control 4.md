---
layout:   post
title:    "Inventory Control Subject to Uncertain Demand——(Q,R) Supplement"
date:     2020-01-05
author:   "miao"
mathjax:  true
---



# Inventory Control Subject to Uncertain Demand 2
## Continuous Review
Continuous review means that inventory is monitored continuously or the periods bewteen two consecutive reviews are short enough.

### (Q,R) Supplement
Last time we talked about (Q,R) model with penalty cost when shortage happens. But in real life, the cost caused by shortage and backorder can be difficult to quantify when taking customers' good will into account. Hence, it is common to use 'service level' rather than penalty cost to determine the optimal order quantity $Q$ and reorder point $R$.

#### Type 1 Service Level
Type 1 service means the probability of not stocking out during lead time, denoted by $\alpha$.    
Obviously, $\alpha$ is the probability that demand doesn't exceed $R$ during the lead time. We have,

$$F(R)\ge \alpha$$

Then our problem becomes,

$$min\quad K\frac{\lambda}{Q}+h(\frac{Q}{2}+R-\lambda\tau)$$

$$s.t.\quad F(R)\ge \alpha$$

Here we can only determine $R$ by letting $F(R)=\alpha$ because the derivative of $G(Q,R)$ on $R$ is a constant $h$; but we can still take derivative on $Q$ and get

$$Q^*=EOQ=\sqrt{\frac{2K\lambda}{h}}$$

#### Type 2 Service Level
Type 2 service means the proportion of demand filled from stock (fill rate), denoted by $\beta$.    
Before specifying the model, we need to clarify the fact that the average demand across order cycles is exactly $Q$, that is we order exactly what are demanded in the long run because the demand, though uncertain, is still stationary and has an expected annual rate $\lambda$. In reality we may keep the more inventory because we use safety inventory to offset the penalty caused by uncertainty, but this doesn't change the average demand $Q$ in spite that the stock is always elevated when trying to avoid penalty cost or retain a certain service level.    
Then the proportion of shortage in total demand can be specified as,

$$shortage\%=\frac{n(R)}{Q}$$

where $n(R)$ is the expected shortage and $Q$ is the expected demand during an order cycle. Hence,

$$1-\beta=shortage\%=\frac{n(R)}{Q}$$

Then we have our model,

$$min\quad K\frac{\lambda}{Q}+h(\frac{Q}{2}+R-\lambda \tau)$$

$$s.t.\quad 1-\frac{n(R)}{Q}\ge \beta$$

written in another form,

$$s.t. \quad n(R)\le (1-\beta)Q$$

The optimization of type 2 is much more complex than type 1 because $Q$ has become endogenous when determining optimal $R$.    
The intuition tells us that iteration is needed again in this case, but how can we get iteration functions?

##### Equivalent Penalty Cost
The idea is that we can constitute an equivalent penalty cost according to the constraint on service level.    
Generally we have, (recall the ordinary (Q,R) model)

$$F(R)=1-\frac{hQ}{p\lambda}$$

written in another form,

$$p=\frac{hQ}{[1-F(R)]\lambda}$$

Also recall that we have,

$$Q=\sqrt{\frac{2\lambda[pn(R)+K]}{h}}$$

in ordinary (Q,R) model. What we need to do is just plug the equivalent $p$ into $Q$ function and get the relationship between $Q$ and $R$.

$$Q=\sqrt{\frac{2\lambda\{Qhn(R)+K\lambda[1-F(R)]\}}{\lambda h[1-F(R)]}}$$

$$Q=\sqrt{\frac{2Qn(R)}{1-F(R)}+\frac{2K\lambda}{h}}$$

Hence, we get a quadratic equation with $Q$.

$$Q^2-\frac{2n(R)}{1-F(R)}Q-\frac{2K\lambda}{h}=0$$

According to quadratic formula we can finally get the positive solution of $Q$,

$$Q=\frac{n(R)}{1-F(R)}+\sqrt{[\frac{n(R)}{1-F(R)}]^2+\frac{2K\lambda}{h}}$$

Combined with,

$$n(R)=(1-\beta)Q$$

we can begin our iteration and stop when differences between $Q_i$, $Q_{i+1}$ and $R_i$, $R_{i+1}$ are small enough.
