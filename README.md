# quant

A stock Nifty traded at two different places: NSE and SGX.
The price time series of NSE and SGX follow a normal/gaussian distribution.
There is another stock INDA.P in New York, and correlation between NSE-SGX daily percentage returns is same as NSE-INDA.P daily percentage returns.

First the price-time series of NSE and SGX is converted to return-time series, and the Pearson's correlation coefficient of two return-time series is calculated using pandas.
Estimating the value of chi-square as a little close to 0 predicts that the returns follow a linear relationship. Hence we calculate the equation of the regression line that best fits the given data of NSE-SGX daily percentage returns, with a degree of freedom 248.

Here's the estimated output and the scatter plot of returns of NSE (x) amd returns of SGX (y):

![image](https://user-images.githubusercontent.com/63365275/126037443-8029a26d-bb12-4774-92f3-9e77e4484305.png)

![image](https://user-images.githubusercontent.com/63365275/126037402-babbabd0-1ae9-4465-b216-dc4b4fea4d86.png)

Next, we needed to predict the prices of INDA.P
We used OLS (Ordinary Least Square) regression to achieve this in 95% confidence level of the slope.
We calculate the point estimate of slope and intercept and standard error in the slope using OLS regression.
we calculate the t-value with 95% confidence level and n-2 degrees of freedom (n = 250 working days)
so the confidence interval of our slope = [point estimate of slope - t-value * standard error in slope , point estimate of slope - t-value * standard error in slope]

output is as follows:

![image](https://user-images.githubusercontent.com/63365275/126037605-050988dd-5c31-4c9a-8e57-feb180132bf0.png)
 
 next we predicted the returns of inda.p as
 y(predicted) = mx+c 
 
 ![image](https://user-images.githubusercontent.com/63365275/126037698-de9ed5fe-2135-4bfc-b6e5-64c25e2f2320.png)
 where m is predicted in 95% confidence interval.
 as we know the last working day price of INDA.P , we can backtrack to predict all 250 prices.
 
 
