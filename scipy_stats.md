# Just enough scipy.stats to poke yourself in the Eye

## Standard scipy.stats import
```Python
import scipy.stats as scs # Follow the norm! It makes code more re-usable. 
```

## Distributions and their methods

#### Distributions
```Python
norm = scs.norm(mu, sd) # Variable norm now holds a normal/gaussian distriution with 
						# mean mu and standard deviation sd. 
gamma = scs.gamma(alpha, beta) # Variable gamma now holds a gamma distribution with 
							   # shape parameter alpha and scale/rate parameter beta. 
expon = scs.expon(lambda) # Variable expon now holds an exponential dist. 
						  # with mean 1/lambda and variance 1 / lambda ** 2 (squared).
binom = scs.binomial(n, p) # Variable binom now holds a binomial distribution with 
						   # mean np and variance np(1 - p)
poisson = scs.poisson(lambda) # Variable poisson now holds a poisson distribution with 
							  # mean lambda and variance lambda. 
geometric = scs.geom(p) # Variable geometric now holds a geometric distribution with 
						# mean 1/p and variance 1 - p / (p ^ 2). 
uniform = scs.uniform(scale = a, loc = b) # Variable that holds the uniform distribution
 									  	  # ranging from a-b. 

Note that there are A TON of distributions available to grab just like this - these
are just the most common ones that I've used thus far.
```

#### Useful Distribution Methods
```Python
To Come!
```

### Standard Error
```Python
se = scs.sem(data) # SE now holds the standard-error of the mean for input data. 
``` 

