---
layout: post
title:  "Inventory Control Subject to Uncertain Demand——(Q,R) Model"
date:   2020-01-04
author: "miao"
mathjax:  true
---



# Inventory Control Subject to Uncertain Demand 1
## Continuous Review Models
Continuous review means that inventory is monitored continuously or the periods bewteen two consecutive reviews are short enough.
### (Q, R) Model
Policy: reorder $Q$ every time when inventory hits $R$.

![(Q,R) model](https://i.loli.net/2020/01/03/mqj2cYdEXw1ybRF.png)

#### Notations
$Q$, order quantity,    
$R$, reorder point,    
$\tau$, lead time,     
$h=ic$, holding cost per unit per time unit,    
$p$, penalty cost per unit per time,    
$x$, demand during lead time,     
$f(x)$, probability density of the demand during lead time.

Hence the cost function,

$$G(Q,R)=h(\frac{Q}{2}+R-\lambda\tau)+K\frac{\lambda}{Q}+\frac{pn(R)\lambda}{Q}$$

where,

$$n(R)=\int_R^{+\infty}(x-R)f(x)dx$$

serves as the expected shortage every order cycle.

Though the demand is uncertain, it is still stable and thus the average demand rate is still $\lambda$ during a long time period, in which case the average holding cost doesn't contain any uncertainty as the first term shows; the second term is the setup cost;
the third term shows the expected shortage penalty cost for a year because there are $\lambda/Q$ times expected shortages in a year.       
Our objective is still minimize yearly cost,

$$min\quad G(Q,R)$$

Take derivatives respectively on $Q$ and $R$,

$$\frac{\partial G(Q,R)}{\partial Q}=-\frac{K\lambda}{Q^2}+\frac{h}{2}-\frac{pn(R)\lambda}{Q^2}=0$$

$$Q^*=\sqrt{\frac{2\lambda[p n(R)+K]}{h}}$$

$$\frac{\partial G(Q,R)}{\partial R}=h+\frac{p\lambda}{Q}\cdot \frac{dn(R)}{dR}=0$$

$$h+\frac{p\lambda}{Q}[-Rf(R)+\int_{+\infty}^Rf(x)dx+Rf(R)]=0$$

$$F(R^*)=1-\frac{hQ}{p\lambda}$$    

where $F(R)$ is the cumulative distribution function of $f(\cdot)$.

Though we find the first order conditions, it seems impossible to calculate. Here we assume $x\sim N(\mu,\sigma)$ and use iteration to approach the optimal solution.    

- Just start from EOQ (assume there's no expected shortage) and use

$$F(R)=1-\frac{hQ}{p\lambda}$$

to determine $R_1$. Here's one practical approach,   

>For handy calculation, we can normalize $R$ with $r=\frac{R-\mu}{\sigma}$ and $x$ with $z=\frac{x-\mu}{\sigma}$ to use the standard normal distribution.

>$$n(R)=\int_{R}^{+\infty}[(\sigma z+\mu)-(\sigma r+\mu)]f(x)d(\sigma z+\mu)$$

>Recall that $\phi(z)=f(\sigma z+\mu)\cdot \sigma$ (probability formula under stict monotone transformations), we can get $f(x)=\phi(z)/{\sigma}$. Hence,

>$$n(R)=\sigma \int_{r}^{+\infty}(z-r)\phi(z)dz=\sigma L(z)$$

>Just let the intergal part be $L(z)$, which we can use in any case.             
>Because $F(R_1)=\Phi(r_1)$, we can determine $R_1=\sigma r_1+\mu$ by looking up cdf table of standard normal distribution before determining $r_1$ with $\Phi(r_1)$.

- Then use $R_1$ and

$$Q_1=\sqrt{\frac{2\lambda[p n(R)+K]}{h}}$$

to determine $Q_1$.

- After that, use $Q_1$ to determine $R_2$ again...

- Generally we stop iteration when $Q_i$, $Q_{i+1}$ and $R_i$, $R_{i+1}$ are close enough (less than 1). But remember there's no guarantee of convergence!