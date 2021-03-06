
# Markov Chain Monte Carlo

## Monte Carlo Sampling

Monte Carlo methods are used to numerically approximate integrals, when the integral function is not tractable but the function being integrated is.

In Bayesian stats, the mean of a probability density $p(\theta)$ is 
$$
\mu = \int_{\Theta} \theta p(\theta) \, d \theta .
$$
Except for cases in which the distribution $p(\theta)$ has a known form (not the case for most applied models) for functional form of the integral isn't known, but $p(\theta)$ is 

The Monte Carlo estimate of $\mu$ is.

- Draw $N$ independent samples, $\theta^{(1)}, \dots, \theta^{(N)}$, from $p(\theta)$
- Estimate $\hat{\mu}$ with,
    $$
    \hat{\mu} = \frac{1}{N} \sum_{n = 1}^N \theta^{(N)} .
    $$

If $p(\theta)$ has finite mean and variance, the law of large numbers ensures that the Monte Carlo estimate converges to the true value 
$$
\lim_{N \to \infty} \hat\mu \to \mu
$$
and the estimation error is governed by the CLT,
$$
| \mu - \hat{\mu} | \propto \frac{\sigma}{\sqrt{N}}
$$

**Example** The mean of $Y = X^2$ where $X \sim \dnorm(0, 1)$.
Draw a sample from $Y$,

```r
x <- rnorm(1024, 0, 1) ^ 2
```
The Monte Carlo estimates of the mean is

```r
mean(x)
#> [1] 0.977
```
with standard error,

```r
sd(x) / sqrt(length(x))
#> [1] 0.042
```



## Markov Chain Monte Carlo Sampling

**Problem:** Monte Carlo sampling requires the samples to be **independent**. But what if you cannot draw independent samples? 

**Solution:** Markov Chain Monte Carlo are a class of algorithms to sample from a distribution when independent samples cannot be drawn.
However, the samples in MCMC will be **dependent**.



## References

- @Stan2016a [Ch. 28]
