---
layout:   post
title:    "Inventory Control Subject to Uncertain Demand——Zero Setup Cost"
date:     2020-01-13
author:   "miao"
mathjax:  true
---



# Inventory Control Subject to Uncertain Demand 3
## Periodic Review Model
Periodic review means that inventory is examined at constant intervals, when decision about both whether to order and how much to order need to be determined.

If we assume no lead time exists, there would be four different models showed as following table,

|                  | Zero Setup Cost |                With Setup Cost               |
|:----------------:|:---------------:|:--------------------------------------------:|
|   Single Period  |    Newsvendor   | I don't know the official name of this model |
| Infinite Horizon |  Order up to S  |                     (S,s)                    |
|:----------------:|:---------------:|:--------------------------------------------:|

where single period means that the inventory from last period is not applicable for the use in the following periods,     
while infinite horizon means that the inheritance of inventory is allowed.

### Newsvendor Model
The policy is order $S$ at the beginning of every interval.

![Newsvendor Model](https://i.loli.net/2020/01/13/fexyL2TjoAHDMPV.jpg)

#### Notations
$c_o$, overage cost (penalty per unit left over)     
$c_u$, underage cost (penalty per unit short)     
$F(x)$, cumulative distribution of demand during a single interval,     
$f(x)$, probability density of demand during a single interval,     
$S$, order up to point.

#### Model
Cost function,

$$G(S)=c_o\int_0^S(S-x)f(x)dx+c_u\int_S^{+\infty}(x-S)f(x)dx$$

It's easy to understand that the integral part in the first term denotes the expected units left over at the end of an interval while the integral in the second term means the expected units in shortage. The only difference compared with normal model is that holding cost is replaced by overage cost.

Hence our model is,

$$min_S\quad G(S)$$

#### Solution
Take derivative of $G(S)$ on $S$,

$$\frac{\partial G(S)}{\partial S}=c_o\int_0^Sf(x)dx-c_u\int_S^{+\infty}f(x)dx=0$$

$$c_oF(S)-c_u[1-F(S)]=0$$

$$F(S^*)=\frac{c_u}{c_o+c_u}$$

this is applicable to all distributions.

### Order up to S
The policy is order up to $S$ at the beginning of every interval.

![Order up to S](https://i.loli.net/2020/01/13/fexyL2TjoAHDMPV.jpg)

The figure is the same as the previous Newsvendor model except that inventory left from previous periods can be used in the following periods.     

#### Notations
Two differences from Newsvendor model,      
$c_o$, overage cost becomes $h$, inventory holding cost per unit per period,      
$c_u$, underage cost becomes $p$, penalty per unit short per period. (Actually in most cases they are the same.)

#### Model

$$G(S)=h\int_0^S(S-x)f(x)dx+p\int_S^{+\infty}(x-S)f(x)dx$$

#### Solution

$$F(S^*)=\frac{p}{p+h}$$


These two models are simplest models of periodic review——they don't have either setup or lead time. Note that the length of an interval is not adjustable, namely $T$ is exogenous. We will discuss an endogenous $T$ in (S,T) model.