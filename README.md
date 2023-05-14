# TAA_Bayesian
The project is a system, for Medium-Long Term Trading for Tactical Asset Allocation using Bayesian Network Models
A key factor in any optimum portfolio is its “Strategic Asset Allocation”. Although it has been shown that strategic asset allocation is the greatest contributor to portfolio performance. However, there are times when an asset class, or a market sector experiences an elevated risk, or enters a regime change that is detrimental to the portfolio performance in the medium term. Hence ‘Tactical Asset Allocation’ is a powerful method to take advantage of adverse risks and steer the strategic asset allocation accordingly and generate alpha.

The problem remains how to generate timely and actionable information and re-allocate the assets among the asset classes in a realistic trading strategy. The portfolio should not be rebalanced among its asset classes too frequently as it drives up the costs of due to increased trading into its constituent assets and securities. On the other hand, the trading signals should be automated and generate a medium-term outlook for an asset class. 
This project will create an automated trading system to generate signals at fixed date of each month using ‘Gold’ as an asset class to rebalance among asset classes. The asset classes are Developed Market Equities (US), Equities in Other Developed Markets (UK), Emerging Market Equities, Real Estate Investment Trusts (Alternative Investments), Corporate Bonds (Fixed Income), Currency Markets (Money Markets) and Gold (Commodities)

We define our Asset Classes as:

a) Developed Market Equities in US S&P500: "^SPY" 

b) Equities in Other Developed UK FTSE: " ISF.L" 

c) Alternative Investments Real Estate Investment Trusts (REIT): " ESS" 

d) Commodities-Gold: Goldman Sachs Gold ETF "AAAU"

e) Emerging Market Equities as repreented by MSCI Emerging Markets ETS iShares ("EEM") 

f) Currency Markets as represented by Invesco Euro Currency ETF "FXE"

g) Fixed Income (HY Corporate Bonds): "BoFA"

We first build a SAA combination of these asset classes using data from Yahoo Finance and Fred using Start Date: 2020-01-01 and End Date: 2022-01-01

We build a policy mix or Strategic Asset Allocation.

Then we build a Bayesian Model using signals from other financial and macroeconomic variables to shift the allocation to a Tactical Asset Allocation. 
1. Crude Oil Price: West texas Intermediate (WTISPLC). Monthly Series. https://fred.stlouisfed.org/series/WTISPLC
2. Export Price Index of Gold: IQ12260. The series is Monthly. https://fred.stlouisfed.org/series/IQ12260
3. Federal Funds Rate. Daily. https://fred.stlouisfed.org/series/DFF
4. Market Yield of Treasury Securities (Inflation Indexed). Daily. https://fred.stlouisfed.org/series/DFII10
5. Market Based Expectation of 5 Year Breakeven Inflation. Daily. https://fred.stlouisfed.org/series/T5YIE
6. Gold ETF Volatility Index. Daily. https://fred.stlouisfed.org/series/GVZCLS
7. Laborforce Participation Rate in US. Monthly. https://fred.stlouisfed.org/series/CIVPART
8. Total Non-Farm Payroll in US. Monthly. https://fred.stlouisfed.org/series/PAYEMS
9. Unemployment Rate (US). Monthly. https://fred.stlouisfed.org/series/UNRATE
10. CPI Excludign Energy/Food (US). Monthly. https://fred.stlouisfed.org/series/USACPICORMINMEI
11. US S&P500 Index. Yahoo Finance ^GSPC https://finance.yahoo.com/quote/%5EGSPC/
12. China Equities. SSE Composite Index. Yahoo Finance 000001.SS https://finance.yahoo.com/quote/000001.SS/history
13. Indian Equities Index (Broad). BSE Sensex. Yahoo Finance ^BSESN https://finance.yahoo.com/quote/%5EBSESN
14. REIT. Essex Property Trust. Yahoo Finance ESS https://finance.yahoo.com/quote/ESS
15. iShares Core UK FTSE 100 ETF. Yahoo Finance ISF.L https://finance.yahoo.com/quote/ISF.L/
16. Physical Gold Price. Yahoo Finance GOLD.AX https://finance.yahoo.com/quote/GOLD.AX/
17. High Yield Corporate Bonds Total Return index. Bank of America. Fred. BAMLHYH0A0HYM2TRIV https://fred.stlouisfed.org/series/BAMLHYH0A0HYM2TRIV

We have implemented a Bayesian model to forecast the price of physical Gold GOLD.AX 1 month in the future. So we use an additional variable of the current price of Gold as a predictor in the Bayesian Network and a variable ‘Forecast’ to capture the next month’s Gold Price. Hence the combined data frame has 18 nodes, or variables with 17 nodes from the financial and macroeconomic and geopolitical variables and an additional node, Forecast, which is the variable for the  1𝑠𝑡 of a month  𝑚+1 which is associated with Gold and 17 other variables for 1st of prior month  𝑚. 

The combined data frame was appended by an observed price of Gold for each of the following month and the data sample was partitioned into a training set using data from years prior to 2021, a validation set for the data from year 2021 and a testing set with data from the year 2022. This is referred to as DiscreteF_DF

Usage Guidelines
# Download BayesianK2.pkl and store it in a Path on a Local Drive at 'C:/MScFE/Capstone/Models/'
# Download TAA_System.ipynb. This is the TAA System
# Fix a Startegic Asset Allocation (SAA) and a Tactical Asset Allocation (TAA) for your portfolio [Should have Gold as an Asset Class]
# TAA should have a higher proportion in Gold Asset Class as compared to SAA. SAA may be defined based on the risk profile of the investor.
# Run the TAA_System.ipynb
# Enter the Date in 'YYYY-MM-DD' format, on which we want to generate the Signal. 
# Condition 1. If the current date > the 1st of a month (not more than 3 days), use that 1st of a month as End Date (Recommended)
# Act: In this condition, if the Forecast Signal is 1 Rebalance to TAA, else stay with SAA.
# Condition 2. If current date <  1st of a month (when Signal should be generated). We can use that 1st of that month as End Date
# Run this system again close to the Date of Signal and Act as per above
