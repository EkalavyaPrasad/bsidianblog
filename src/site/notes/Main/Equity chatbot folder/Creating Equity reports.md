---
{"dg-publish":true,"permalink":"/main/equity-chatbot-folder/creating-equity-reports/"}
---


To get a rough idea of the inherent capabilities of our current model. Let's start by simply adding all the information to our llama3:latest model and see what it gives us. 

Starting prompt. 


```
based on the information you have on {portfolio} write me a report. Your job is to be as precise as possible and be thorough with the facts and figures. 
```


This prompt was pretty ok. It ended up giving a paragraph summary of the portfolio which I did not want. But it's expected from this bare skeleton of a model. 

#### Step 1: Giving the model a format to follow:

updated prompt:

```
based on the information you have on {portfolio} write me a report. Your job is to be as precise as possible and be thorough with the facts and figures. 
Use the following format: \

     # Portfolio report \

     ## Overall portfolio summary \

     ## Portfolio composition \

     ## Industry composition \

     ## Risk analysis \

     ## Recommendations""")
```

#### Step 2:  Provide more information. 


Here is some additional context that the model is given so that it knows more about the portfolio:

```
portfolio_info = f"""Total portfolio value: {total_value:,.2f}\

Name of invested stocks: {portfolio_df['Company Name']}\

total portfolio return: {total_returns:,.2f}\

daily gain/loss: {daily_gain_loss:,.2f}\

risk metrics:\

standard deviation: {stddev:,.2f}%\

sharpe ratio: {s_ratio:,.2f}\

expected returns: {expected_returns(initial_weights, log_returns)*100:,.2f}%\

VaR: {var:,.2f}\

CVaR: {cvar:,.2f}\

Recommended optimised portfolio:

The recommended optimised portfolio after optimising weights to maximise Sharpe ratio is: {weights_df}\

After portfolio optimisation, sharpe ratio increases to {opti_s_ratio:,.2f}\

Volatility becomes {opti_stddev:,.2f}%\

Expected returns increase to {er:,.2f}% \

"""
```

prompt: 

```
"""Your job is to take portfolio data and convert them into insightful portfolio reports. You will recieve user's portfolio and your task is to create reports out of them. Give comprehensive explainations of all the figures and provide recommendations on the choice of stocks that the user has chosen. Make your answers detailed and in-depth.  \

     each section should contain a short paragraph on what the section is about, what qualities in a portfolio makes the section 'good' and whether the user portfolio satisfies the qualities. \

     for example: Industry composition, this helps us understand diversification. Diversification is important because it makes sure that our portfolio is spread out across different industries. our portfolio is good because it is sufficiently diversified or it is bad because it is not sufficiently diversified.\

     Answer in markdown.\

     Use the following format: \

     # Portfolio report \

     ## Overall portfolio summary \

     ## Portfolio composition \

     ## Industry composition \

     ## Risk analysis \

     ## Recommendations"""),

    ("human", f'My individual stock data is in {df} and my overall stock data is in {other_info}'
```

This gave me a decent output but needs more polishing. One major issue the model faces now is distinguishing between the current and optimised portfolio. 


