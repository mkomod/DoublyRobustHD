# DoublyRobustHD
This is an R package to implement methods seen in "A Bayesian semiparametric framework for causal inference in
high-dimensional data" by Joseph Antonelli and Francesca Dominici, which can be found at the following link:

https://arxiv.org/pdf/1805.04899.pdf

To download the R package use the following in R:


```
library(devtools)
install_github(repo = "jantonelli111/DoublyRobustHD")
library(DoublyRobustHD)
```

and a simple example on how to use it is below:

```{r, eval=TRUE}
n = 200
p = 20
x = matrix(rnorm(n*p), n, p)
t = rbinom(n, 1, p=pnorm(0.7*x[,1] + 0.3*x[,2]))
y = rnorm(n, mean=t + 0.3*x[,1] + 0.6*x[,2] + 0.5*x[,3], sd=1)

est = DRbayes(y=y, t=t, x=x, nScans=2000, nBurn=1000, thin=2)
```

A more detailed vignette is currently being written and will be available by the end of May.
