# Coins solution

[Problem Statement](../problems/coins.md)

Part 1:

WLOG let the fair coin be the $n$th one, and let the random variable $h_{i}$ count the number of heads flipped counting the coins from $1$ to $i$. Recall $p_i$ is the probability the $i$th coin flips heads.

Then, we have $P(h_{n} \text{ is even}) = P(h_{n-1} \text{ is even})(1-p_n) + P(h_{n-1} \text{ is odd})(p_n)$.

But we know $P(h_{n-1} \text{ is even or odd}) = 1$ and $p_n=1-p_n=0.5$, so we have $P(h_{n} \text{ is even})=0.5$

Part 2:

We show the contrapositive of the problem statement - that is, if an even or odd number of heads is equally likely, then at least one coin must be fair.

Given the coins $p$, let's try to write the distribution of likelihoods to flip any particular number of heads as a polynomial. The coefficient of each degree term will be the probability that we get that number of heads.

Suppose our described polynomial is $q(x)=k_0+k_1x+k_2x^2+\dots+k_nx^n$ (for $k_i$'s matching the probability distribution). Then, observe that having the same probability of flipping an even or odd number of heads is equivalent to having $\sum_{i\text{ even}}k_i=\sum_{i\text{ odd}}k_i\implies \sum_{i\text{ even}}k_i-\sum_{i\text{ odd}}k_i=0$. Thus if we can find an expression for this quantity in terms of $p_i$ we are done.

To do this, let's find the [unique factorization](https://en.wikipedia.org/wiki/Fundamental_theorem_of_algebra#Corollaries) of this polynomial via induction: let's denote $q_i(x)$ as the above polynomial for the first $i$ coins.

For a single coin, our polynomial is $q_1(x) = (1-p_1) + p_1x$.

For the $i$th coin, our polynomial is $$q_i(x)=\underbrace{(1-p_i)q_{i-1}(x)}_{i\text{th coin is tails}} + \underbrace{(p_ix)q_{i-1}(x)}_{i\text{th coin is heads}} = (1-p_i+p_ix)q_{i-1}(x)$$

Then it's clear the full polynomial can be factored as $q_n(x)=(1-p_1+p_1x)(1-p_2+p_2x)\dots(1-p_n+p_nx) = k_0 + k_1x + \dots + k_nx^n$.

But how does the polynomial help us?

We can use the [roots of unity](https://en.wikipedia.org/wiki/Root_of_unity)! 

Consider $q_n(-1)=k_0-k_1+k_2-k_3+\dots$. This is precisely the sum expression we had above! Thus, we can observe $q_n$ has a root at $x=-1$ iff the odds of flipping an even or odd number of heads is the same.

But we also know $q_n(-1) = (1-p_1+p_1(-1))(1-p_2+p_2(-1))\dots(1-p_n+p_n(-1)) = (1-2p_1)(1-2p_2)\dots(1-2p_n)$. Then for this product to equal zero we [must have](https://en.wikipedia.org/wiki/Zero-product_property) at least one of $p_i=0.5$.

This also proves sufficiency.

Thanks to [Thomas](https://thomasqm.com) for the beautiful solution.

# Addendum

[Egor](https://github.com/eggag32) later showed me the following (much simpler) solution to Part 2:

Observe the actual distribution doesn't matter, just the aggregate probabilities of even or odd. 

Inductively, suppose none of the first $i-1$ coins are fair. Let them have aggregate probability $q_{i-1}$ of having an even number of heads, with $q_{i-1}\neq0.5$. Then the probability the first $i$ coins flip an even number of heads is $q_{i-1}(1-p_i)+(1-q_{i-1})p_i$. It suffices to show that the only way this quantity equals 0.5 (i.e., we are equally likely to flip an even or odd number of heads) is if the $i$th coin is fair.

Here we can complete the square, but we'll present an alternate deduction: 

Suppose for contradiction $p_i\neq 0.5$. Then we can write $p_i=0.5+\epsilon$, where $\epsilon\neq 0$. Then, $q_{i-1}(1-(0.5+\epsilon))+(1-q_{i-1})(0.5+\epsilon)=0.5\implies \epsilon(1-2q_{i-1})=0$.

Since we set $\epsilon\neq0$, we find $q_{i-1}=0.5$, arriving at a contradiction. 