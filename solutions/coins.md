Part 1:

WLOG let the fair coin be the $$ n $$th one, and let the random variable $$ h_{i} $$ count the number of heads flipped counting the coins from $$1$$ to $$i$$. Recall $$p_i$$ is the probably the $$i$$th coin flips heads.

Then, we have $$ P(h_{n} \text{ is even}) = P(h_{n-1} \text{ is even})(1-p_i) + P(h_{n-1} \text{ is odd})(p_i)$$.

But we know $$P(h_{n-1} \text{ is even or odd}) = 1$$ and $$p_i=1-p_i=0.5$$, so we have $$ P(h_{n} \text{ is even})=0.5 $$

Part 2:

Given the coins $$p$$, let's try to write the distribution of likelihoods to flip any particular number of heads as a polynomial. The coefficient of each degree term will be the probability that we get that number of heads.

We will construct the polynomial inductively: we'll let $$q_i$$ denote the above polynomial for the first $$i$$ coins.

For a single coin, our polynomial is $$q_1 = (1-p_1) + p_1x$$.

For the $$k$$th coin, our polynomial is $$\underbrace{q_{k-1}(1-p_k)}_{\text{Prior distribution and the $$k$$th coin is tails}} + \underbrace{q_{k-1}(p_kx)}_{\text{Same, but heads}}$$ = $$q_{k-1}(1-p_k+p_kx)$$

Let's consider the polynomial $$k_0 + k_1x^1 + k_2x^2 + \dots + k_nx^n$$, where each $$k_i$$ denotes the probability of flipping $$i$$ heads.

Then we have that the probability of an even number of heads
