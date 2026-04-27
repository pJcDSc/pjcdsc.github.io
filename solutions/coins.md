Part 1:

WLOG let the fair coin be the $$ n $$th one, and let the random variable $$ h_{i} $$ count the number of heads flipped counting the coins from $$1$$ to $$i$$.

Then, we have $$ P(h_{n} \text{ is even}) = P(h_{n-1} \text{ is even})(1-p_i) + P(h_{n-1} \text{ is odd})(p_i)$$.

But we know $$P(h_{n-1} \text{ is even or odd}) = 1$$ and $$p_i=1-p_i=0.5$$, so we have $$ P(h_{n} \text{ is even})=0.5 $$


