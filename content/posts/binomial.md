+++
title = "Binomial distribution, Mean and variance derivations"
date = 2019-04-02T14:48:13-04:00
draft = true
tags = []
categories = []
+++

Binomial distribution is defined as,
$$Binomial(r,n,p) = {}^{n}C_{r}\,\, p^r {(1-p)}^{n-r}\quad (1)$$

### Finding expected value of the Binomial distribution

We need to find $E[r]$ using the definition

$$E[x] = \int x P(x)dx\quad (2)$$

So, plugging in $r$ from $(1)$ in $(2)$, we get

$$E[r] = \int r\, ^{n}C_r\,\, p^r {(1-p)}^{n-r} dr$$

which is equivalent to,

$$E[r] = \int r\, \frac{n!}{r!(n-r)}\, p^r {(1-p)}^{n-r} dr$$

we cancel $r$ and get

$$E[r] = \int \frac{n!}{(r-1)!(n-r)}\, p^r {(1-p)}^{n-r} dr \quad (3)$$

We substitute $r-1=k$,

$$E[r] = \int \frac{n!}{(k)!(n-k-1)}\, p^(k+1) {(1-p)}^{n-k-1} dk$$

then we expand the factorial of $n$ which is equivalent to,

$$E[r] = n\int \frac{(n-1)!}{k!(n-k-1)}\, p^{(k+1)} {(1-p)}^{n-k-1} dk$$

and then we break the $p^{k+1} = p\, p^k$ and since $^{n-1}C_k = \frac{(n-1)!}{(k)!(n-k-1)}$

$$E[r] = np\,\int \,^{n-1}C_k\, p^{k}{(1-p)}^{n-k-1}dr \quad (4)$$

from $(1)$, we substitute the definition of $Binomial(k,n-1,p)$ in $(4)$,

$$E[r] = np \int Binomial(k,n-1,p) dk $$

Since the quantity inside the integral is a distribution, it summs up to 1,

$$E[r] = np$$

### Finding the variance of the binomial distribution

We use the formula, since we know $E[x] = np$
$$Var(x) = E[(x - E[x])^2] = E[x^2] - (E[x])^2 \quad (5)$$
We write down $E[r^2]$ with $Binomial(r,n,p)$

$$
E[r^2] = \int r^2\, ^{n}C_r\,\, p^r {(1-p)}^{n-r} dr
$$

We follow a similar procedure to reach $(3)$

$$
E[r^2] = \int r\,\, ^{n}C_{r-1}\,\, p^r {(1-p)}^{n-r} dr
$$

Now we split the equation using $r = (r-1) + 1$,

$$
E[r^2] = \int (r-1)\,\, ^{n}C_{r-1}\,\, p^r {(1-p)}^{n-r} dr + \int \,^{n}C_{r-1}\,\, p^r {(1-p)}^{n-r} dr
$$

The second term is same as $(4)$, then we cancel out $r-1$ in the first part to get

$$
E[r^2] = \int ^{n}C_{r-2}\,\, p^r {(1-p)}^{n-r} dr + np
$$

now we break up the equation with $n! = n(n-1)\, (n-2)!$ and split $p^r = p^2\, p^(r-2)$

$$
E[r^2] = p^2 n(n-1)\int ^{n}C_{r-2}\,\, p^r {(1-p)}^{n-r} dr + np
$$

The product inside the integral is the Binomial distribution

$$
E[r^2] = p^2 n(n-1)\int Binomial(r-2,n-2,p) dr + np
$$

so we get,

$$
E[r^2] = p^2 n^2 - p^2 n  + np
$$

Plugging back $E[r^2]$, $E[r]$ into the definition of $Var(r)$ in $(5)$

$$
Var(r) = p^2 n^2 - p^2 n  + np - (np)^2
$$

Cancelling out and grouping terms we get

$$
Var(r) = np(1-p)
$$
