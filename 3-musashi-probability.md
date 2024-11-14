The probability of at least *k* successes (a "success" for this computation is getting a Musashi) in n attempts (an "attempt" is a build) is given by:

$$ P_{atleast}(n, k) = 1 - \sum_{i=0}^{k-1} P_{exact}(n, i) $$

where $P_{exact}(n, i)$ is the probability of *exactly* *i* successes in *n* attempts.

To understand why, start by thinking about how to account for all the possible outcomes. In any series of *n* attempts, we must get some specific number of successes. It can be anywhere from 0 (none) all the way up to *n* (all). So if we sum up the probability for all the possible number of successes, we will get 1 (which is another way of writing 100%). But we can work backwards from this, too. The probability of getting at least 3 successes would just be adding up the probability of getting 3, the probability of getting 4, and so on up to *n* (the maximum). But because we know they all sum up to 1, we can also look at the "leftovers": this total is the same as taking the total 100% and subtracting off the probability of getting 0, the probability of getting 1, and the probability of 2. For our problem, it's much more convenient to work with the "leftovers" because the number of terms we have to compute is much smaller (3 vs. 13).

So what's $P_{exact}(n, k)$? Well, lucky for us, this is a well known problem is statistics. The formula is:

$$ P_{exact}(n, i) = \binom{n}{i} P_1^i (1 - P_1)^{n - i} $$

$\binom{n}{k}$ is the [binomial coefficient](https://mathworld.wolfram.com/BinomialCoefficient.html). Intuitively, it's the number of combinations you can get by choosing *k* distinct items from a group of *n* distinct possibilities. You may have heard it read as "*n* choose *k*". $P_1$ is just the probability of success in a single attempt.

Substituting in the formula, we get:

$$ P(n, k) = 1 - \sum_{i=0}^{k-1} \binom{n}{i} P_1^i (1 - P_1)^{n - i} $$

For our problem, we have these specific values:

* $P_1 = 1.2\% = 0.012$ is the probability of getting Musashi in a single build.
* $n = 16$ is the number of "attempts" we're making. An "attempt" in this case is a build.
* $k = 3$ is the minimum number successes we're looking for, which is 3 because that's how many you got.

Substituting in specific values:

$$ P(16, 3) = 1 - \sum_{i=0}^{3-1} \binom{16}{i} (0.012)^i (1 - 0.012)^{16 - i} $$
$$ P(16, 3) = 1 - \sum_{i=0}^{2} \binom{16}{i} (0.012)^i (0.988)^{16 - i} $$
$$ P(16, 3) = 1 - \binom{16}{0} (0.012)^0 (0.988)^{16 - 0} - \binom{16}{1} (0.012)^1 (0.988)^{16 - 1} - \binom{16}{2} (0.012)^2 (0.988)^{16 - 2} $$
$$ P(16, 3) = 1 - (1) (1) (0.988)^{16} - (16) (0.012) (0.988)^{15} - (120) (0.012)^2 (0.988)^{14} $$

And that's enough to plug into a calculator.

$$ P(16, 3) = 0.00086074974562 = 0.086074974562 \% \approx 0.086 \% $$
