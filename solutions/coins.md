[Problem Statement](../problems/coins.md)

Part 1:

WLOG let the fair coin be the $$ n $$th one, and let the random variable $$ h_{i} $$ count the number of heads flipped counting the coins from $$1$$ to $$i$$. Recall $$p_i$$ is the probably the $$i$$th coin flips heads.

Then, we have $$ P(h_{n} \text{ is even}) = P(h_{n-1} \text{ is even})(1-p_i) + P(h_{n-1} \text{ is odd})(p_i)$$.

But we know $$P(h_{n-1} \text{ is even or odd}) = 1$$ and $$p_i=1-p_i=0.5$$, so we have $$ P(h_{n} \text{ is even})=0.5 $$

Part 2:

Given the coins $$p$$, let's try to write the distribution of likelihoods to flip any particular number of heads as a polynomial. The coefficient of each degree term will be the probability that we get that number of heads.

We will construct the polynomial inductively: we'll let $$q_i$$ denote the above polynomial for the first $$i$$ coins.

For a single coin, our polynomial is $$q_1(x) = (1-p_1) + p_1x$$.

For the $$k$$th coin, our polynomial is $$q_k(x)=\underbrace{(1-p_k)q_{k-1}(x)}_{k\text{th coin is tails}} + \underbrace{(p_kx)q_{k-1}(x)}_{k\text{th coin is heads}} = (1-p_k+p_kx)q_{k-1}(x)$$

Then it's clear the full polynomial can be factored as $$q_n=(1-p_1+p_1x)(1-p_2+p_2x)\dots(1-p_n+p_nx) = k_0 + k_1x + \dots + k_nx^n$$.

Observe then that having the same probability of flipping an even or odd number of heads is equivalent to having $$\sum_{i\text{ even}}k_i=\sum_{j\text{ odd}}k_j\implies \sum_{i\text{ even}}k_i-\sum_{j\text{ odd}}k_j=0$$

But how does the polynomial help us?

We can use the [roots of unity](https://en.wikipedia.org/wiki/Root_of_unity)! 

Consider $$q_n(-1)=k_0-k_1+k_2-k_3+\dots$$. This is precisely the expression above! Thus, we can observe $$q_n$$ has a root at $$x=-1$$ iff the odds of flipping an even or odd number of heads is the same!

But we also know $$q_n(-1)$$ has a [unique factorization](https://en.wikipedia.org/wiki/Fundamental_theorem_of_algebra#Corollaries) as $$(1-p_1+p_1(-1))(1-p_2+p_2(-1))\dots(1-p_n-p_n(-1)) = (1-2p_1)(1-2p_2)\dots(1-2p_n)$$. Then for this product to equal zero we [must have](https://en.wikipedia.org/wiki/Zero-product_property) at least one of $$p_i=0.5$$.

This also proves sufficiency.

Thanks to [Thomas](https://thomasqm.com) for the beautiful solution.
