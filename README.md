# capped_variance_swap

A Capped Variance Swap is a financial derivative that allows an investor to trade the future realized variance of an underlying asset, with a cap on the maximum possible variance. This instrument is similar to a regular variance swap, but the cap limits the amount of variance that can be considered in the payoff calculation, thereby limiting the potential gain or loss for the investor.


Underlying Asset (S): The asset whose variance is being traded (e.g., a stock, index).
Strike Variance (K_var): The fixed level of variance agreed upon at the inception of the swap. This is typically the expected variance.
Realized Variance (sigma_realized^2): The actual variance of the underlying asset observed over the life of the swap.
Variance Cap (C_var): The maximum level of variance that can be realized in the calculation. If the actual realized variance exceeds this cap, the cap is used instead.
Notional Amount (N): The dollar amount per variance point. This scales the payoff of the swap.
Maturity (T): The time until the swap expires.


Log Returns: Variance is calculated using the log returns of the underlying asset's price. The log return from time t to t+1 is given by:
R_t = ln(S_{t+1} / S_t)
Where:
R_t is the log return at time t.
S_t is the price of the underlying asset at time t.

Realized Variance (sigma_realized^2): Realized variance is calculated as the average of the squared log returns over the life of the swap. It can be annualized by multiplying by the number of trading days in a year (commonly 252 days):
sigma_realized^2 = (1/n) * sum_{t=1}^{n} (R_t - R_avg)^2 * 252
Where:
n is the number of time intervals (e.g., daily returns).
R_avg is the average log return over the period.

Capped Variance: The realized variance is capped at a predetermined level, C_var. If the realized variance exceeds this cap, the cap is used in the payoff calculation:
sigma_cap^2 = min(sigma_realized^2, C_var)

Capped Variance Swap Payoff: The payoff of the capped variance swap at maturity is the notional amount multiplied by the difference between the capped variance and the strike variance:
Payoff = N * (sigma_cap^2 - K_var)
Where:
N is the notional amount.
sigma_cap^2 is the capped realized variance.
K_var is the strike variance.

If sigma_cap^2 > K_var, the payoff is positive, benefiting the holder of the swap. Conversely, if sigma_cap^2 < K_var, the payoff is negative, and the holder would incur a loss.
