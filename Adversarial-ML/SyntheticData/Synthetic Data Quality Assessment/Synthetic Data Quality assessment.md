

# Measuring the statistical similarity between two samples using Jensen-Shannon and Kullback-Leibler divergences

_Can we quantify the quality of the information we receive every day? How can we measure the distance between two statistical samples?

# Introduction

In recent years, the amount of information generated and processed daily easily surpasses that of decades ago. The current stage of collection and storage of very large amounts of data is unprecedented. In this scenario, new challenges arise and require more intelligent solutions to be solved. One of the biggest challenges is to correctly identify the changes in the underlying processes and structures that generate data that are updated every day. Whether the changes in the data are due to _“bugs”_, glitches, genuinely abrupt or gradual make it difficult to design a single efficient detection mechanism. A possible solution consists of measuring the divergence between two distributions. It is based on the main concepts derived from information theory. Here we introduce two divergence measures, but only one actual _distance_ metric.

# Similarity measures for probability distributions

The _entropy_ of a discrete random variable _X_ is a measurement of the amount of information required on the average to describe that variable. It is the most important metric in information theory as it measures the uncertainty of a given variable. Shannon defined the entropy _H_ of a discrete random variable _X_ with probability mass function _P(x)_ as:

![](https://miro.medium.com/v2/resize:fit:1400/1*NSIn8OVTKufpSlvOOoXWQg.png)

Entropy H of a discrete random variable X

In the previous equation, if we set _b = 2_ in the log expression, we can estimate the minimum value in bits necessary to encode all the information contained in _X._ The _relative entropy_ measures how distant two distributions are from each other. It is also referred to as the _Kullback-Leibler_ _divergence (KL divergence)_ between two samples. For discrete probability distributions _P(x)_ and _Q(x),_ defined on the same probability space _𝛘,_ it is given by:

![](https://miro.medium.com/v2/resize:fit:1400/1*QinqQP6WmyHpy_bqCRaJ1g.png)

KL divergence of distribution Q from P for two discrete random variables

For two _probability density functions p(x) and q(x),_ the previous equation becomes:

![](https://miro.medium.com/v2/resize:fit:1400/1*PJ2I2HoIe-BBs_EA6hlX0Q.png)

KL divergence for two continuous random variables

Let P_(x)_ and _Q(x)_, _x_ ∈ _𝛘,_ be two _probability mass functions_ (i.e. discrete distributions). Then _D(P||Q) ≥ 0_ with equality if and only if _P(x) = Q(x)_ for all _x._ For the most part, _D(P||Q)_ ≠ _D(Q||P)_. Therefore, KL divergence is **not** a real distance metric because it is not symmetric and does not satisfy the triangle inequality. It is important to notice that the KL divergence is defined only if for all _x, Q(x) = 0 → P(x) = 0._

An alternate approach is the Jensen-Shannon divergence (JS divergence), another method of measuring the similarity between two probability distributions. It is a symmetric and smoothed version of the KL divergence and can be used as a _distance_ metric. Defining the quantity M = (P + Q)*(0.5), we can write the JS divergence as:

![](https://miro.medium.com/v2/resize:fit:1400/1*viATYZeg9SiT-ZdzYGjKYA.png)

JS divergence between distributions P and Q

From the above equations, we see that the JS divergence is equivalent to the entropy of the mixture minus the mixture of the entropy. It is common to compute the square root of JSD as a true metric for distance. All of these metrics are already implemented in Python as the imports below suggest.

from scipy.stats import entropy  
from scipy.spatial.distance import jensenshannon  
from scipy.special import kl_div

# Computing divergence for discrete variables

The Python script below illustrates its use for discrete data, by computing the probability mass function using NumPy’s histogram and then calculating the KL and JS divergences for any discrete data.

JS divergence and KL divergence Python code for discrete variables

To understand its real use, let’s consider the following distribution of some real data with added normal random noise.

mu, sigma = reference_data.mean(), reference_data.std()  
noise = np.random.normal(0, sigma, size=reference_data.shape)  
pure = reference_data.copy()  
signal = pure + noisefig, ax = plt.subplots(1,1,figsize=(12,4))sns.distplot(noise, ax=ax,  
             hist=False,  
             kde_kws={'lw': 3,'label':'Noise'})sns.distplot(pure, ax=ax,  
             hist=False, rug=True,  
             kde_kws={"lw": 3,'label': 'Original data'})sns.distplot(signal, ax=ax,  
             hist=False,  
             kde_kws={"lw": 3, 'label': 'Transformed data'})ax.set_xlabel('Reference data',fontsize=12,weight='bold')

![](https://miro.medium.com/v2/resize:fit:1400/1*WdGwh4qFm3tXQn2DRftdnA.png)

Adding a normally distributed noise to original reference data

We have transformed the original data by adding some additional noise (e.g. transforming the same column name in another dataset). Let’s observe how both the KL divergence and JS divergence behave when compared.

![](https://miro.medium.com/v2/resize:fit:1400/1*QGIcN6FjQlfbBh2uL0zh9A.png)

Divergences (KL and JS) for normal random noise with zero mean

![](https://miro.medium.com/v2/resize:fit:1400/1*Bh51x6h4VJb5UFeuFNAPoQ.png)

Divergences (KL and JS) for normal random noise with different means

The KL divergence seems to be more sensitive to small changes in the original data. Similarly, we can generate some discrete random data and compare its divergence using both metrics.

![](https://miro.medium.com/v2/resize:fit:1400/1*MN_MEruEijTSnqZT69hRAg.png)

JS and KL divergence for discrete random data

Here, we can observe the symmetric behavior of the JS divergence. Its value is the same whether we use x_0 or x_1 as our reference data.

# Computing divergence for continuous variables

What if we need to compute the divergence for continuous variables as well? Instead of probability _mass_ functions and discrete data (i.e. bins), now we have to deal with probability _density_ functions and continuous data (as we have seen before).

A commonly used method is to approximate the observed statistical distribution with some probability density function (pdf). Well known distributions include normal, _Poisson_, _beta_, _gamma_, etc. Suppose we have two continuous distributions _p(x)_ and _q(x)_ with normal probability density functions, such as:

![](https://miro.medium.com/v2/resize:fit:1400/1*z_1968753THSQxbhF44Uvw.png)

We can rewrite the KL divergence for continuous data such as

![](https://miro.medium.com/v2/resize:fit:1400/1*HfQx_NgtYOr70CRR9MgF0Q.png)

The probability density function of the normal distribution is given by

![](https://miro.medium.com/v2/resize:fit:1400/1*cpnKvhewoaroQ9BQYPx2RQ.png)

Which leads to

![](https://miro.medium.com/v2/resize:fit:1400/1*gnrl8iJzNOG0vYOkALifAQ.png)

(Analytical) KL divergence between two normal pdfs

Therefore, we have an _analytical_ expression for the KL divergence instead of the empirical ones. One of the advantages of expressing it analytically is that we get rid of the necessity to _“break”_ the variable into discrete parts (_bins_) and avoid the problem of support intersection (i.e. whether _Q(x)=0_ or _P(x)=0_).

![](https://miro.medium.com/v2/resize:fit:1400/1*qr_IGiPmm9z17_o9e-ni_g.png)

This approach is particularly useful when there is a shift in the transformed data. If instead of multiplying the original reference data we had shifted it (e.g. sum _100_ to all of its values), the divergence would still grow monotonically as shown below.

![](https://miro.medium.com/v2/resize:fit:1400/1*o8ZH6ENVJtZywKJmRPR99g.png)

So far, most of the demonstrations shown here can be easily implemented also using the following GitHub package as provided by Michael Nowotny:

[https://github.com/michaelnowotny/divergence](https://github.com/michaelnowotny/divergence)

Approximating the data with a normal distribution can be heavily biased because nothing guarantees that the vast majority of information present in most data follows a normal density curve. A more general approach can be established by using the [generalized gamma distribution](https://en.wikipedia.org/wiki/Generalized_gamma_distribution) function to approximate the data distribution and to compute the KL divergence. Depending on the distribution, it adjusts better to the data points reducing the generalization error. The probability density function of a generalized gamma distribution is given by:

![](https://miro.medium.com/v2/resize:fit:1400/1*9I25Kfal8hOdanvtwNBl5w.png)

The probability density function of a generalized gamma distribution

Where Γ is the [_gamma_](https://en.wikipedia.org/wiki/Gamma_function) function. It follows from the definition of the Kullback-Leibler divergence that the analytical expression for the KL divergence between two generalized gamma density functions is given by:

![](https://miro.medium.com/v2/resize:fit:1400/1*LTtN93vZ0vNMP_hqQ_Yr6g.png)

KL divergence between two generalized gamma functions

Where _Ψ(x)_ is the [_digamma_](https://en.wikipedia.org/wiki/Digamma_function) function.

![](https://miro.medium.com/v2/resize:fit:1400/1*nUbjC2l5oGQIMAM70lSgVA.png)

Below we show a Python implementation that compares variations in the original data by adding different scalars. Notice that we set _p=1_ in the original expression to reduce the generalized gamma to a standard gamma distribution.

Python code for the generalized gamma pdf and KL divergence

![](https://miro.medium.com/v2/resize:fit:1400/1*lAzt5Chzi6KtxayD0mo9dA.png)

Approximating the previous distribution using a generalized gamma approach

As we shift the data, the divergence increases monotonically as well, as expected. Python’s _scipy_ package has several implementations for the different distribution functions as shown below.

from scipy.stats import gengamma, gamma, beta #distributions  
from scipy.special import gamma, digamma #functions

# Computing divergence using a cumulative density function

More recent publications have shown approaches to estimate the KL divergence _without solving for the densities_ first (as it is typically done)_._ That is, this intermediate step is unnecessary as long as the empirical cumulative density function (cdf) is estimated. The empirical cdf is defined as:

![](https://miro.medium.com/v2/resize:fit:1400/1*t84qU2mdYAHqX0XBmhiCSQ.png)

Here, _U(x)_ is the [Heaviside step function](https://en.wikipedia.org/wiki/Heaviside_step_function) — or unit step function — where _U(0) = 0.5_. This function can be interpolated linearly, leading to a continuous distribution 𝑃𝑐 (see reference [3]). The final proposed divergence is then:

![](https://miro.medium.com/v2/resize:fit:1400/1*tlS4_Fe_kghF6DM41exkxQ.png)

where

![](https://miro.medium.com/v2/resize:fit:1400/1*drNr3YvnrtZDPSWFpmGSHA.png)

The number 𝜖 (epsilon) is defined such that it is smaller than the smallest distance between the samples. We have implemented a Python code to compute the empirical cumulative density function and its linear interpolation as well as the final divergence estimator. The results can be seen below.

Python code for the cumulative distribution function and its corresponding divergence

![](https://miro.medium.com/v2/resize:fit:1400/1*9Leuq7VaPlbnJE0jVXh-0Q.png)

As we apply the same transformation shown for discrete data (adding normal noise and changing the standard deviation), we observe that the divergence increases as expected. This is a relatively new approach and more investigations should be performed to better understand its behavior.

# Conclusions

We presented three different methods to estimate the similarity between two samples. The first one involves data discretization and the divergence is computed empirically. The second one involves approximating the data with a continuous probability density function. The results seem more stable. It is possible to detect divergence by shifting the data, but its implementation might be more complicated as it depends on the tools and resources available. The third method is the newest one and involves computing the cumulative density function.

Each of these methods has its advantages and disadvantages. Choosing the right one depends on the data and available resources. In Python, many libraries are already implemented. This makes it easier to use more advanced functions (e.g. digamma function). There is a lot of room for improvement and exploration in data quality. Designing the right tools can facilitate your daily job!

# References

[1] T. Dasu, S. Krishnan, S. Venkatasubramanian, K. Yi — **An information-theoretic approach to detecting changes in multi-dimensional data streams** — Interface (2006).

[2]Nielsen, Frank — **On the Jensen-Shannon Symmetrization of Distances Relying on Abstract Means** — Entropy (2019), vol. 21, issue 5, p. 485.

[3]Fernando Pérez-Cruz — **Kullback-Leibler Divergence Estimation of Continuous Distributions** — 2007 — Department of Electrical Engineering. Princeton University.

[4]Christian Bauckhage — **Computing the Kullback-Leibler Divergence between two Generalized Gamma Distributions** — 2014 — University of Bonn.

[5]Thomas Cover, Joy Thomas — **Elements of Information Theory —** 2nd edition —2006 — Wiley-Interscience



[[The Jensen-Shannon Divergence]][[Outlier mining in high-dimensional data using the Jensen–Shannon divergence and graph structure analysis]]
[[Measuring the disclosure risk using TCAP]] 
![[Final Report on the Disclosure Risk Associated with the Synthetic Data Produced by the SYLLS Team - Mark Elliot.pdf]]

[[Disclosures in Synthetic Data]]