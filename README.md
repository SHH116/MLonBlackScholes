# Pricing Vanilla Options via Machine Learning 

Traditionally, vanilla European Options would be priccd via analytical Black-Scholes, a mathematically closed form formula.
In this project, I apply various machine learning regression kernels to learn the Black-Scholes behaviour.
The result is a highly accurate (r-squared) model, that can price options independent of Black-Scholes.

In addition, I stress-test the new model under various scenarios to measure its aggregate behaviour under various volatility and underlying spot price regimes; To ensure that forward tests are as reliable as the backtests.

--------
## Libraries

* !pip install pandas
* !pip install numpy
* !pip install pandas_profiling
* !pip install seaborn 
* !pip install qgrid

-----------
## Black-Scholes assumptions
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
## Project steps
1-SPX index as an underlying proxy for global markets.
  
2-VIX index as a proxy for ATM put and call implied volatility.
  
3-Compute Analytical BS (at the money call/put prices) deterministically by using SPX and VIX prices as function arguments.
  
4-Fit various relevant kernels of choice on SPX and VIX as independent variables, and BS output as response varaible. 
  
5-On the original time-series compare the performance of the kernel vs the analytical BS.
  
6-Identify the kernel that produces the highest r-squared (the best learner).
  
7-Stress-test the kernel of choice on a) monte-carlo simulated data b)randomized historical data, to measure the r-squared again.
  
8-If test predictions do not degrade vs the train predictions, the model is reliable.
  
9-If test predictions degrade vs the train predictions, choose another relevant kernel.
  
  
  
------
 ## Theory Vs Reality
 
 * In reality we do not have the options Implied Volatilites represented by VIX in this project, so the practitioners must reverse engineer the options market price in conjunction with the underlying SPX value in order to extract the VIX. 
  
 * The model is trained for varying spot and volatiltiy regimes, but not for varying interest rates
  
 * The model prices the at the money put and call options only.
  
 * The VIX is used as volatility proxy for a specific strike (the ATM), whereas in reality it is an aggregate compution of the upper/lower strikes of 30-day t0 expiry and the neighbouring tenors. 
  
-----
  

  
 






