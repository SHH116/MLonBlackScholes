![image](https://user-images.githubusercontent.com/56700326/132067100-90a80137-ff9d-41de-8a55-cabc2d2c94b9.png)



# Pricing European Vanilla via various Gaussian Machine Learning Kernels 

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
* !pip install scikit-learn


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
  

## Regarding Gaussian Process Regression (GCP) Kernels
The model inputs include VIX as a mean-reverting feature and the underlying SPX price as an unbounded random-walk feature. However, most of the GCP kernels co-enforce a sinosidal property in conjunctions with a drift. Therefore, the GCP kernels cannot replicate the market regimes with very dominant trends, unless they have had exposure to similar-magnitude drifts in training. Therefore, the quality of the model's forward predictions would highly depend on the similarity of the current regime's drift to that of the training data. Basically, drift dominant regimes would degrade the model's R-squared. Therefore, I have used additive and multiplicative proeprties of the independent variables to come up with stronger and simpler alternatives. 
  
  
  
  

 ## Assumptions and Constraints
 

 * The model is trained for varying spot and volatiltiy regimes, but not for varying interest rates.
  
 * The model prices the at the money put and call options only expiring at the constant term of 30 days.
  
 * The model uses VIX as a proxy to price the ATM strike whereas VIX is an aggregate compution of the upper/lower strikes of 30-day to expiry and its neighbouring terms. 
  
 * The VIX has an embedded skew, therefore, the model slightly overestiamtes the ATM call and put price. This is fine however, since the core business idea is to insure the bank portfolio and reduce VaR exposure, and over protection is better than under protection.
  

 ## Data
  
2-year SPY (as SPX proxy) and VIX hostorical data can be downloaded from the following sources. The first year to be used for model training and the second year to be used for model forward testing.
  
  
  <dt>Data Sources:</dt>
  <dd>[1] https://ca.finance.yahoo.com/quote/SPY/history?p=SPY</dd>
  <dd>[2] https://ca.finance.yahoo.com/quote/%5EVIX/history?p=%5EVIX</dd>
  <dd>[3] https://stooq.com/db/h/</dd>
  <dd>[4] https://www.barchart.com/ondemand/api/getHistory?gclid=Cj0KCQjw7MGJBhD-ARIsAMZ0eeuwPQiDLvub5yVYGvvfyW4AyeWpHGH9lBK1XylfM3DSyAygHiji6ccaAtpOEALw_wcB</dd>
  <dd>[5] https://www.quandl.com/search?query=stocks</dd>
  
  
 ## Future Version
  
* Feed the entire volatility surface values instead of a single VIX value, in order to extract prices per each strike.
  
* Perform 5-day forward, 1-month forward forecasts as well.
  
* Apply the model on underlyings other than SPX.
  
  
## Acknowledgments
  
Thanking Dmitry Vyushin of RBC for his supervision and guidance
  
Sasha Hajy Hassani as the developer
  
## Further Readings
  
  Gaussian Process:
  <dd>[1]https://fhr.nuc.berkeley.edu/fhr-research-areas/pyrk/uncertainty-quantification/</dd>
  <dd>[2]https://analyticsindiamag.com/guide-to-gpytorch-a-python-library-for-gaussian-process-models/</dd>
  <dd>[3]https://scikit-learn.org/stable/modules/gaussian_process.html</dd>
  
  
  
  
  
  
  
  
  
  
  
 
  

  
 






