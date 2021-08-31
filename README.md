# Pricing Vanilla Options via Machine Learning 

Traditionally, vanilla European Options would be priccd via analytical Black-Scholes, a mathematically closed form formula.
In this project, I apply various machine learning regression kernels to learn the Black-Scholes behaviour.
The result is a highly accurate (r-squared) model, that can price options independent of Black-Scholes.

In addition, I stress-test the new model under various scenarios to measure its aggregate behaviour under various volatility and underlying spot price regimes; To ensure that forward tests are as reliable as the backtests.

--------
## Libraries







-----------
## Black-Scholes primary assumptions include:
<dl>
  <dt>Put-Call parity holds:</dt>
  <dd>https://corporatefinanceinstitute.com/resources/knowledge/finance/put-call-parity/</dd>
  <dt>No Arbitrage:</dt>
  <dd>https://quant.stackexchange.com/questions/41414/does-black-scholes-need-to-assume-no-arbitrage</dd>
  <dt>Underlying follows a Random Walk and its returns are lognormally distributed:</dt>
  <dd>https://en.wikipedia.org/wiki/Random_walk</dd>
  <dt>The Random walk has constant drift and volatility:</dt>
  <dd>https://www.investopedia.com/terms/b/blackscholes.asp</dd>
  <dt>The Options are Vannilla European style:</dt>
  <dd>https://en.wikipedia.org/wiki/Option_style:</dd>
  <dt>No Dividends are paid
</dl>
  
--------
## Project steps:
1-SPX 500 as an underlying proxy for global markets
2-VIX index as a proxy for ATM put and call implied volatility
3-Compute Analytical BS prices
4-Use price,implied volatility 

  
 






