#Inventory Control Subject to Known Demand 2

飞机上把固定需求的库存管理模型写完吧。

## All-units Discounted
All-units discounted means a relatively cheaper price would be charged for **each unit** when ordering more. Basically prices are determined by different quantities of orders. Without loss of generality, we can assume there are three price intervals corresponding with three order quantity intervals.

#### Notations
* $c_1$, cost per unit when order quanity below $q_1$,    
* $c_2$, cost per unit when order quantity above  $q_1$ but below $q_2$,    
* $c_3$, cost per unit when order quantity above $q_2$,   
* $C(Q)$, total unit cost for a certain order.

Without loss of generality, I just stipulate three intervals of unit costs here.   
Then we have cost function for a single order,
$$\begin{aligned}
C(Q)&=c_1Q\quad if\quad0\le Q<q_1\\
&=c_2Q\quad if\quad q_1\le Q<q_2\\
&=c_3Q\quad if\quad Q\ge q_3
\end{aligned}$$
![total cost per order versus quantity](https://i.loli.net/2019/12/14/ztwYdS8eWFEUop3.jpg)   
As we can see from the picture, there are two cutoffs when the unit prices shift down and slopes descend as the quantity increases.   
We still have the cost function,   
$$G(Q)=K\frac{\lambda}{Q}+ic_i\frac{Q}{2}+c_i\lambda, i=1,2,3$$    
So we can get,   
![annual cost versus quantity](https://i.loli.net/2019/12/14/WKacmRz2vljyCiY.jpg)    
where the crossings indicate the extreme points (they could be at other points depending on the specific shape of the curve). Note that (a) lines do not intersect here because $c_i$ changes suddenly as $Q$ increases; (b) each line just makes sense in a certain interval, when $Q\le q_1$, line $c_1$ reflects $G(Q)$, when $q_1\le Q\le q_2$, line $c_2$ does, when $Q\ge q_2$, line $c_3$ does.    
So how to find the total rather than local extreme point in a appropriate interval? Here’s the algorithm,


1. Start with smallest $c_i$ and compute EOQ. If feasible (i.e. EOQ falls in the corresponding interval of Q), stop. Otherwise start considering next larger  $c_i$ and repeat until computed EOQ is feasible.
2. Calculate the $G(Q)$ with all smaller $c_i$s where $Q$ is exactly at the threshold of the corresponding $c_i$.
3. Calculate the total cost of feasible EOQ and oher Qs at the thresholds, adopt the one with least cost.  

## Incremental Discounted 
Another rule of discounted quantity order is incremental discounted quantity where only those units above thresholds are discounted, in which case the unit cost is a continuous function on quantity.

#### Notation
* $c_1$, cost per unit for order quanity below $q_1$,    
* $c_2$, cost per unit for order quantity above  $q_1$ but below $q_2$,    
* $c_3$, cost per unit for order quantity above $q_2$,   
* $C(Q)$, total unit cost for a certain order.

WLOG, only three intervals are stipulated here. Then we have the cost function for a sigle order,   
$$
\begin{aligned}
C(Q)&=c_1Q\quad if\quad 0\le Q<q_1\\
&=c_1q_1+c_2(Q-q_1)=(c_1-c_2)q_1+c_2Q \quad if\quad q_1\le Q<q_2\\
&=c_1q_1+c_2(q_2-q_1)+c_3(Q-q_2)=(c_1-c_2)q_1+(c_2-c_3)q_2+c_3Q\quad if\quad Q\ge q_3
\end{aligned}
$$

![total cost per order versus quantity](https://i.loli.net/2019/12/27/2IQaB1sE9Fd3kLJ.jpg)

Thus we have unit cost,   
$$
\begin{aligned}
C(Q)/Q&=c_1\quad if\quad 0\le Q\le q_1\\
&=(c_1-c_2)q_1/Q+c_2\quad if\quad q_1\le Q\le q_2\\
&=(c_1-c_2)q_1/Q+(c_2-c_3)q_2/Q+c_3\quad if\quad Q\ge q_3
\end{aligned}
$$

Because the total cost per order is continuous, unit cost is also continuous on quantity, in which case we cannot simply plug the unit into EOQ formula and get EOQ because now unit cost $C(Q)/Q$ itselt has become endogenous and to get the stationay point we also need to take derivative of $C(Q)/Q$ on $Q$, which is much more complicated and unnecessary.   

Recall we had annual cost,
$$G(Q)=K\frac{\lambda}{Q}+ic_i\frac{Q}{2}+c_i\lambda$$    
But there’s a difference here—we need to substitute $c_i$ with $C(Q)/Q$,    
$$
\begin{aligned}
G(Q)&=K\frac{\lambda}{Q}+i\frac{C(Q)}{Q}\frac{Q}{2}+\frac{C(Q)}{Q}\lambda\\
&=[K+C(Q)]\frac{\lambda}{Q}+\frac{1}{2}iC(Q)
\end{aligned}$$     
From this we obliterate the unit cost $C(Q)/Q$. We notice that the derivative of $C(Q)$ on $Q$ are exactly $c_1$, $c_2$ or $c_3$ because there’s only one term in $C(Q)$ consisting $Q$ while the other terms are all constants. So a brilliant idea comes into our mind —can we constitute an equivalent $K’$ to replace $K$ and follow the original EOQ formula to get optimal  $Q^*$s? The answer is yes but note that the $K’$ term should never include a term including $Q$, that is, $K’$ should be a constant rather than a variable on $Q$!     

Then we can extract constants in $C(Q)$ to constitute $K’$s on different quantity intervals,    
$$
\begin{aligned}
K’_1&=K\\
K’_2&=(c_1-c_2)q_1+K\\
K’_3&=(c_1-c_2)q_1+(c_2-c_3)q_2+K\quad or\\
&=(c_1-c_3)q_1+(c_2-c_3)(q_2-q_1)+K
\end{aligned}
$$    
where $K$ is the original setup cost.   
The process left is much simpler, just plug different $K’_i$ and corresponding $c_i$ into,   
$$EOQ_i=\sqrt{\frac{2K’_i\lambda}{ic_i}}$$    
to get different $Q^*_i$s, then plug $Q^*_i$s into the cost function,   
$$G(Q)=K’_i\frac{\lambda}{Q^*_i}+ic_i\frac{Q^*_i}{2}+c_i\lambda$$     
and compare the annual cost to determine which one is optimal.


 