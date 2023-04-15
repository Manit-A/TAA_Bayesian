# TAA_Bayesian
The project is system, for Medium-Long Term Trading for Tactical Asset Allocation using Bayesian Network Models
A key factor in any optimum portfolio is its “Strategic Asset Allocation”. It has been shown that strategic asset allocation is the greatest contributor to portfolio performance. However, there are times when an asset class, or a market sector experiences an elevated risk, or enters a regime change that is detrimental to the portfolio performance in the medium term. Hence ‘Tactical Asset Allocation’ is a powerful method to take advantage of adverse risks and steer the strategic asset allocation accordingly and generate alpha.

The problem remains how to generate timely and actionable information and re-allocate the assets among the asset classes in a realistic trading strategy. The portfolio should not be rebalanced among its asset classes too frequently as it drives up the costs of due to increased trading into its constituent assets and securities. On the other hand, the trading signals should be automated and generate a medium-term outlook for an asset class. 
This project will create an automated trading system to generate signals at fixed date of each month using ‘Gold’ as an asset class to rebalance among asset classes. The asset classes are Developed Market Equities (US), Equities in Other Developed Markets (UK), Emerging Market Equities, Real Estate Investment Trusts (Alternative Investments), Corporate Bonds (Fixed Income), Currency Markets (Money Markets) and Gold (Commodities)

We define our Asset Classes as:

Developed Market Equities in US S&P500: "^SPY" 

Equities in Other Developed UK FTSE: " ISF.L" 

Alternative Investments Real Estate Investment Trusts (REIT): " ESS" 

Commodities -Gold , "AAAU"

Emerging Market Equities as repreented by MSCI Emerging Markets ETS iShares ("EEM") 

Currency Markets as represented by Invesco Euro Currency ETF "FXE"

Fixed Income (HY Corporate Bonds): "BoFA"

We first build a SAA combination of these asset classes using data from Yahoo Finance and Fred using Start Date: 2020-01-01,End Date: 2022-01-01 
Assets = ['AAAU', 'SPY', 'ISF.L', 'ESS', 'EEM', 'FXE']

We build a policy mix or Strategic Asset Allocation.

Then we build a Bayesian Model using signals from other financial and macroeconomic variables to shift the allocation to a Tactical Asset Allocation. 
1. Crude Oil Price: West texas Intermediate (WTISPLC). Monthly Series
2. Export Price Index of Gold: IQ12260. The series is Monthly. https://fred.stlouisfed.org/series/IQ12260
3. 
We have implemented Bayesian models to forecast the price of physical Gold GOLD.AX 1 month in the future. So we use an additional variable of the current price of Gold as a predictor in the Bayesian Network and a variable ‘Forecast’ to capture the next month’s Gold Price. Hence the combined data frame has 18 nodes, or variables with an additional Forecast variable for the  1𝑠𝑡 of a month  𝑚+1
which is associated with Gold and 17 other variables for 1st of prior month  𝑚. 

The combined data frame was appended by an observed price of Gold for each of the following month and the data sample was partitioned into a training set using data from years prior to 2021, a validation set for the data from year 2021 and a testing set with data from the year 2022. This is referred to as DiscreteF_DF
