---
layout:   post
title:    "Inventory Control Subject to Uncertain Demand——With Setup Cost"
date:     2020-01-14
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

### Single Period Model with Setup Cost

The situation here is more complex: we still have some inventory while the demand is uncertain such that both shortage and surplus are possible at the end of the period. If we reorder, surplus (not only including holding but also including wasting inventory) cost and setup cost occur; if we don't order, penalty cost caused by shortage may occur, in which case tradeoff needs measuring properly.

The optimal policy here is not only an order up to point $S$ but also a decisive point $s$ due to the appearance of setup cost. When the existing inventory is lower than $s$, we reorder up to $S$; otherwise we don't reorder.

#### Notations
- $K$, setup cost,    
- $h$, surplus cost for each unit leftover,    
- $p$, loss of revenue plus loss of good will per unit,    
- $c$, unit cost,    
- $G(y)$, expected holding and shortage cost if on-hand inventory at the beginning of the period is $y$,    
- $f(x)$, probability density function of demand.

#### Model
For convenience we don't include setup cost at first in our cost function, similar to previous models we have,

$$G(y)=h\int_0^y(y-x)f(x)dx+p\int_y^{+infty}(x-y)f(x)dx$$

But no hurry to minimize this function, which doesn't contain