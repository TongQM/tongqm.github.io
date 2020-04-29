---
layout:   post
title:    "Interest Rates"
date:     2020-04-29
author:   "miao"
mathjax:  true
---


# Interest Rates

* Yields to maturity is the most accurate measure of interest rates.
* Present value is used to measure interest rates.


## Four Types of Credit Market Instruments
* A simple loan: both principal and interest are repaid at the maturity date.
* A fixed-payment loan: principal and interest are divided into equal payments every period before maturity.
* Coupon bond: interest is divided into equal payment every year and the principal (face value) is repaid at the maturity date.
* Discount bond (zero-coupon bond): bought at a price below the face value and the face value is repaid at the maturity date.

### Yield to Maturity
Yield to maturity is the interest rate that equates the present value of cash flow payments received from a debt instrument with its value today.

#### Simple Loan
$$PV=\frac{CF}{(1+i)^n}$$

#### Fixed-Payment Loan
$$LV=\sum_{k=1}^n\frac{FP}{(1+i)^k}$$

#### Coupon Bond
$$P=\sum_{k=1}^n\frac{C}{(1+i)^k}+\frac{FV}{(1+i)^n}$$
There are three points needing to be mentioned about coupon bond,

+ When the coupon bond is priced at its face value, the yield to maturity equals the coupon rate. (Proof is shown below.)
+ THe price of a coupon bond and the yield to maturity are **negatively related**: as the yield to maturity rises, the price of the bond falls; as the yield to maturity falls, the price of the bond rises.
+ The yield to maturity is greater than the coupon rate when the bond price is below its face value.

#### Discount Bond
$$P=\frac{FV}{(1+i)}$$
when the maturity is one year. More generally,
$$P=\frac{FV}{(1+i)^n}$$

Annex Proof for Coupon Bond,

When the face value equals the price,
$$FV=P=\sum_{k=1}^n\frac{FV\cdot i_c}{(1+i)^k}+\frac{FV}{(1+i)^n}$$
$$1-\frac{1}{(1+i)^n}=i_c\sum_{k=1}^n\frac{1}{(1+i)^k}$$
$$\frac{(1+i)^n-1}{(1+i)^n}=i_c[\frac{1-\frac{1}{(1+i)^{n+1}}}{1-\frac{1}{1+i}}-1]$$
$$(1+i)^n-1=i_c\frac{(1+i)^{n+1}-1-i\cdot (1+i)^n}{i}$$
$$(1+i)^n-1=\frac{i_c}{i}\cdot [(1+i)^n-1]$$
$$i_c=i$$





