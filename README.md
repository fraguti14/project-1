# project-1
Project one shared repo - 

https://docs.google.com/document/d/1aZwXaf_V16ow_V9Iu0e2M0qthkHqcROnqCWSrYeRoEc/edit?usp=sharing

Project title:  Stocks Analysis for Distribution of Capital

Team members:
Arezoo Tavakoli
Andrea Barreto
Juan Diaz Gutierrez
Francisco Jose Diaz Gutierrez

Project description:
The board of directors at a company has assigned this team the responsibility of conducting a thorough analysis of potential investment opportunities within the highly prominent stocks listed on the NASDAQ stock index. The company has recently acquired additional capital resources, and wants to invest in the two most compelling stocks from a list of eight prospective options. To fulfill this mission, we have been entrusted with the task of meticulously evaluating the performance of the following stocks over the past year, utilizing the Nasdaq Data API: TSLA (Tesla), AAPL (Apple), AMZN (Amazon), INTC (Intel), META (Meta), MSFT (Microsoft), AMD (Advanced Micro Devices), and NVDA (NVIDIA Corp).

Research Questions to Answer:
Which stocks are trending upward? 
Which are trending downward?
Which stocks have the best Price-to-Earnings (P/E) Ratio?
Which stocks have the most volatility relative to the overall market? (Based on Beta)
Based on the data, what two stocks would you recommend to The board of directors at the company to buy?

Datasets to be used:
https://www.alphavantage.co/ 
Yahoo Finance API

Rough breakdown (Git projects)
Project ideation
Data fetching/API integration 
Data analysis 
Data visuals 
Data summary & recommendations
Testing (code)
Testing (Git)
Creating documentation
Creating the presentation
Delivering presentation


 Stocks Analysis For Distribution Of Capital
Andrea Barreto
Arezoo Tavakoli
Juan Diaz Gutierrez Francisco Jose Diaz Gutierrez
 
  Executive Summary
The board of directors at a company has assigned this team the responsibility of conducting a thorough analysis of potential investment opportunities within the highly prominent stocks listed on the NASDAQ stock index. The company has recently acquired additional capital resources, and wants to invest in the two most compelling stocks from a list of eight prospective options. To fulfill this mission, we have been entrusted with the task of meticulously evaluating the performance of the following stocks over the past year, utilizing the Nasdaq Data API: TSLA (Tesla), AAPL (Apple), AMZN (Amazon), INTC (Intel), META (Meta), MSFT (Microsoft), AMD (Advanced Micro Devices), and NVDA (NVIDIA Corp).
Research Questions to Answer:
● Which stocks are trending upward?
● Which are trending downward?
● Which stocks have the best Price-to-Earnings (P/E) Ratio?
● Which stocks have the most volatility relative to the overall market? (Based on Beta)
● Based on the data, what two stocks would you recommend to The board of directors at
the company to buy?


  Research Methodology
For the purpose of this project, we have narrowed down our research focus to a selected group of 8 stocks. These 8 stocks are considered representative of the major players in the NASDAQ
stock market and are generally perceived as low-risk investment options (TSLA (Tesla), AAPL (Apple), AMZN (Amazon), INTC (Intel), META (Meta), MSFT (Microsoft), AMD (Advanced Micro Devices), and NVDA (NVIDIA Corp)). Our analysis and recommendations in this project will be guided by a set of research questions. We will assess these questions by examining a set of key performance indicators (KPIs) to provide accurate and descriptive answers.
Our research questions will be addressed as follows:
"Which stocks are showing positive trends?"
● KPI 1: Weekly Delta timeseries (Data sourced from alphavantage)
● KPI 2: Bollinger Bands, including Simple Moving Average (SMA) and Standard
Deviations (SDEVs) (Data sourced from alphavantage)
"Which stocks are showing negative trends?"
● KPI 3: Weekly Delta timeseries (Data sourced from alphavantage)
● KPI 4: Bollinger Bands, including Simple Moving Average (SMA) and Standard
Deviations (SDEVs) (Data sourced from alphavantage)
"Which stocks have favorable Price-to-Earnings (P/E) Ratios?"
● KPI 5: Stock P/E Ratio (Data sourced from finance.yahoo)
"Which stocks exhibit significant volatility compared to the overall market?
● KPI 6: Stock Beta (Data sourced from finance.yahoo)
“Based on the data, what two stocks would you recommend to The board of directors at the company to buy?”
● Based on the data collected while addressing all these research questions, we will determine two stocks to recommend to the company's board of directors for potential investment.
The final recommendations presented to the board will consider stocks that are trending upwards, demonstrating sustained momentum, and exhibiting strong P/E performance, all while maintaining a stable Beta value to ensure a lower level of risk. We will utilize the Delta timeseries to assess growth and performance trends, the SMA within the Bollinger Bands to determine the overall trend direction, and the 2 standard deviation-based bands to identify potential sentiment and buy and sell signals. Furthermore, we will use the P/E ratio to evaluate stock profitability, sentiment, and performance, and we will contrast it with the Beta value to gauge the stock's volatility within the broader market context.


  KPI defintions Bollinger Bands
  
Bollinger Bands are used to gauge the price's relative position within these bands. When the price is near the upper band, it may indicate that the stock is overbought, and when it's near the lower band, it may suggest that the stock is oversold. They consist of four lines:
● The middle band, which is typically a simple moving average (SMA).
● An upper band that is placed above the middle band and is typically two standard
deviations away from the SMA.
● A lower band that is placed below the middle band and is also usually two standard
deviations away from the SMA.
● The stock price line to indicate signals across the stated bands
Delta
The percent change in price of the stocks compared to the previous week’s prices.
Beta:
Beta measures how much a stock’s price typically moves compared to the overall stock market.
P/E Ratio:
The Price-to-Earnings (P/E) ratio is a measure in the stock market that shows how much investors are willing to pay for a company's earnings


  Code Logic & Highlights
The submitted repository contains all the relevant data including code, logic and planning for project one. This section here focuses on explaining the code and the logc used as well as highlighng efficiencies and limitaitons in our code. (Repository)
API
The Python code presented in the Jupyter notebook showcases two API calls to Alphavantage. You might wonder why we've made two calls. Well, it's because we are investigating a total of 8 stocks, and Alphavantage's free API imposes a limit of 1 call every 5 minutes, allowing for a maximum of 5 stocks per call. In light of this limitation, we have executed two identical, yet separate, calls to the Alphavantage API to retrieve the complete dataset.
To enhance user experience and minimize potential errors when others use our code, we have incorporated a 5-minute delay between each API call. Additionally, we have included a progress bar to provide users with a clear indication of the expected waiting time. This progress bar is implemented using the 'time' and 'ipywidgets' libraries.
Imported Libraries
In addition to our API call to Alphavantage, we utilized Yahoo Finance's Python library to retrieve data related to P/E and Beta values for all the stocks in our analysis. This approach provided us with an alternative method to collect and refine data from Yahoo Finance's datasets. Furthermore, we imported the following components to support our code: matplotlib.pyplot, pandas, plotly.express, json, requests, yfinance, from apikeys import alpha_api, numpy, time, ipywidgets, from IPython.display import display
Data Slicing (daily, weekly)
Our primary dataset combines daily closing prices, tickers, and data frames for all the stocks under scrutiny in this analysis. We maintain daily data as our primary reference point and make adjustments as needed based on the specific task at hand. Additionally, we have a secondary dataframe that encompasses all stocks along with their corresponding Beta and P/E ratios.
For our time series charts and Bollinger Bands charts, we transformed our daily data into a weekly format either through a function or a loop. This decision was made to enhance the visual representation of the data, as weekly intervals provided a clearer presentation.

  Code Efficiency
We make use of Python functions wherever applicable to generate our charts. These functions encapsulate a substantial portion of code to streamline and simplify our for-loops. As a result, we've created a variety of charts, including bar charts, line charts, and multi-line charts, to effectively present all our available metrics.
Example:
<img width="864" alt="Screenshot 2023-10-25 at 6 30 18 PM" src="https://github.com/fraguti14/project-1/assets/139180717/e644afa6-477b-44b6-bb46-f29d3848e380">



 Furthermore, we have incorporated time constraints to prevent potential API call failures stemming from client-side limitations. We have implemented precise timing restrictions and included a progress bar to inform the user about the ongoing progress and anticipated completion time.
Example:
  Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  Stock Analysis Beta Summary
TSLA has the highest beta value (2.25), indicating that it is the most volatile stock in this group. This means TSLA's returns are expected to fluctuate more significantly than the overall market. AMD also has a relatively high beta value (1.65), suggesting above-average volatility. AAPL, META, and AMZN have beta values above 1, indicating that they are more volatile than the market but to a lesser extent than TSLA and AMD. INTC has the lowest beta value (0.89), implying that it is less volatile than the overall market.
P/E Summary
7
  TSLA has a high PE ratio of 60.25, indicating that investors are willing to pay a premium for its earnings. This could be due to high growth expectations. AMZN also has a relatively high PE ratio of 100.44, which suggests that investors have high expectations for its future earnings growth. META and AAPL have PE ratios of 36.6 and 29.03, respectively, indicating moderate valuations compared to TSLA and AMZN. Both AMD and INTC have PE ratios of 0, which could be an anomaly in the data or could suggest negative earnings or no earnings reported (in the case of a PE ratio of 0).
 Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  Stock Trend Summary
AAPL
Summary: Over the year-to-date period, Apple's stock has exhibited an upward trend, maintaining momentum until the most recent three months when it experienced a reversal, shifting towards a downward trajectory. Over this year-to-date span, the stock has gained 16.2%, but in the past three months, it has declined by 12.6%. The current stock value is positioned below the simple moving average line, and the Delta stock trend consistently indicates negative week-to-week changes.
Recommendation: HOLD
Reason: Over the year-to-date period, the stock has demonstrated strong performance with bullish momentum. However, this momentum has recently waned, raising concerns about its future performance. It's worth noting that the stock has a high Price-to-Earnings (P/E) ratio, indicating that investors have high earnings expectations. Given the recent downturn and the elevated P/E ratio, a cautious approach is advisable.
8
   Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  AMD
Summary: Over the year-to-date duration, AMD's stock has demonstrated modest growth of 6.3%, aligning with the typical market average growth rate. This growth has primarily occurred during the most recent quarter, as the stock rallied to reach its year-start levels. Considering the stock's high Beta, there was an expectation that it might outperform the market average at some point. Presently, the stock's value lies below the simple moving average, as seen in the Bollinger Bands chart, and the Delta timeseries indicates a decline in week-to-week growth. Recommendation: SELL
Reason: The stock's performance has been lackluster, with a recent quarter-long downward trend, suggesting a potential regression to lower stock values from mid-year levels. Despite its high Beta, the stock hasn't delivered the expected gains, and there appears to be a lack of momentum. Hence, the decision to recommend selling.
9
   Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  TSLA
Summary: Notably, in the TSLA charts, there was a substantial price drop between August and September, primarily attributed to Tesla's 1:3 stock split, which took effect on August 25, 2022. This event held significance for both Tesla as a rapidly growing tech giant and its shareholders. Since the stock split, Tesla's stock price has displayed significant volatility, fluctuating within the range of 200 to 300. As of now, post-split, TSLA stock has declined by 33%. The Delta time series indicates a consistent three-point downward trend, and the Bollinger Bands currently signal a downward trend as well.
Recommendation: SELL
Reason: TSLA exhibits an exceptionally high Beta, rendering it a highly volatile stock. Coupled with an unattractive P/E ratio, it fails to offer any enticing incentives for investors to bear this level of volatility. Moreover, the stock has been on a sustained downward trajectory since the significant split. Considering the bearish outlook, unfavorable P/E ratio, and pronounced volatility, it appears prudent to recommend selling.
10
   Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  META
Summary: The META stock has experienced remarkable growth over the past year and continues to maintain its momentum. Year-to-date, it has achieved a growth rate of 60.8%, and there are currently no indications of this growth slowing down. Moreover, when considering the stock's Beta in relation to market volatility and its appealing P/E ratio, it presents itself as an attractive candidate for a "BUY" recommendation. The current stock price aligns with the simple moving average of the stock price, and the Delta timeseries consistently exhibits non-anomalous week-to-week growth.
Recommendation: BUY
Reason: META presently carries bullish momentum, characterized by sustained week-to-week delta growth. Additionally, the stock price is in alignment with the simple moving average. The upward trajectory of the stock, coupled with its attractive P/E ratio and a Beta value indicating reasonable stability, positions it as a strong candidate for acquisition and long-term holding in one's portfolio.
11
   Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  AMZN
Summary: It is important to note a significant price drop in the AMZN stock around March of 2022, much like the TSLA stock. This occurred due to a 20:1 stock split announcement by Amazon on March 9, 2022. The split took effect on June 3, 2022, for stockholders recorded on May 27, 2022. For tax-related details regarding this stock split, reference Form 8937. AMZN has achieved an adjusted year-to-date growth of 49.80%, and the overall trend appears to be bullish. The Delta timeseries demonstrates a consistently positive and sustained week-to-week growth pattern, with no apparent indications of slowing down.
Recommendation: BUY
Reason: The bullish trajectory of AMZN, combined with its non-volatile Beta value and highly appealing P/E ratio, positions it as an exceptional candidate for acquisition and long-term holding. The ongoing positive momentum shows no signs of waning.
12
   Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  INTC
Summary: Among the 8 selected stocks in this analysis, INTC stands as the poorest performer. Over the year-to-date period, the stock has witnessed a significant decline of 25% in its stock price value, and the prevailing momentum continues to drive the stock in a downward direction. Furthermore, the P/E ratio for this stock is unattractive, contributing to its current low performance.
Recommendation: SELL
Reason: The stock's persistent downward trend, resulting in a 25% loss year-to-date, coupled with the week-to-week losses indicated by the Delta timeseries, collectively render it an unfavorable choice for investment at this juncture.
13
   Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  MSFT
Summary: Over the year-to-date period, MSFT stock has exhibited approximately 29% growth. As observed in the accompanying charts, the stock encountered turbulence during the initial quarter but has since shown strong performance. Currently, the stock price surpasses the simple moving average, and the Delta weekly time series indicates increased stability in the percentage changes week-over-week. However, the momentum of MSFT stock appears to have faltered over the past few months.
Recommendation: HOLD
Reason: The stock's Beta value, nearing one, in combination with its sustained but decelerated growth and an unattractive P/E ratio, positions it as a suitable candidate for holding in an existing portfolio. However, it may not be the optimal time for new purchases.
14
   Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  NVDA
Summary: Over the past year, NVDA has experienced significant growth, with its value increasing by approximately 80% across the spectrum from low to high. The current stock price resides in the lower $400 range, and it appears that momentum is stabilizing within this new price range. Analyzing the delta time series reveals volatility in the stock, but the cumulative net positive results suggest that momentum remains robust, despite ongoing fluctuations. In conclusion, NVDA has exhibited substantial growth over the past year, and there are no immediate signs of a slowdown.
Recommendation: BUY
Reason: Considering the continuous momentum, price stability evidenced by the Simple Moving Average (SMA), and the consistent trends in the delta weekly time series, along with its highly attractive P/E ratio (the second highest among the group) and its low volatility, NVIDIA emerges as an excellent choice for investment.
15
   Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  Research Questions
Which
stocks are trending upward?
Which
are trending downward?
Which
stocks have the best Price-to-Earnings (P/E) Ratio?
Which
stocks have the most volatility relative to the overall market? (Based on Beta)
● AMZN, NVDA, META
● MSFT, AAPL (Slowing momentum)
● INTC, AMD, TSLA
● Top 3: TSLA, NVDA, AAPL
● Top3: TSLA, AMD, NVDA
Based
the company to buy?
on the data, what two stocks would you recommend to The board of directors at
● META, NVDA or AMZN
GIT REPOSITORY FOR DATA
16
  Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

  Recommendation
Official Recommendation: BUY META & NVDA
● We recommend to the board that investments be made in META and NVDA. META stands out as a robust stock with minimal volatility and high profit expectations, consistently maintaining an upward and sustained growth trend. Furthermore, NVDA, while presenting a higher level of risk due to its pronounced volatility, is complemented by an exceptionally attractive P/E ratio and an overall bullish trend.
Additional information on stocks:
META
● The META stock has experienced remarkable growth over the past year and continues to maintain its momentum. Year-to-date, it has achieved a growth rate of 60.8%, and there are currently no indications of this growth slowing down. Moreover, when considering the stock's Beta in relation to market volatility and its appealing P/E ratio, it presents itself as an attractive candidate for a "BUY" recommendation. The current stock price aligns with the simple moving average of the stock price, and the Delta timeseries consistently exhibits non-anomalous week-to-week growth.
● META presently carries bullish momentum, characterized by sustained week-to-week delta growth. Additionally, the stock price is in alignment with the simple moving average. The upward trajectory of the stock, coupled with its attractive P/E ratio and a Beta value indicating reasonable stability, positions it as a strong candidate for acquisition and long-term holding in one's portfolio.
NVDA:
● Over the past year, NVDA has experienced significant growth, with its value increasing by approximately 80% across the spectrum from low to high. The current stock price resides in the lower $400 range, and it appears that momentum is stabilizing within this new price range. Analyzing the delta time series reveals volatility in the stock, but the cumulative net positive results suggest that momentum remains robust, despite ongoing fluctuations. In conclusion, NVDA has exhibited substantial growth over the past year, and there are no immediate signs of a slowdown.
● Considering the continuous momentum, price stability evidenced by the Simple Moving Average (SMA), and the consistent trends in the delta weekly time series, along with its highly attractive P/E ratio (the second highest among the group) and its low volatility, NVIDIA emerges as an excellent choice for investment.
17
  Andrea Barreto | Arezoo Tavakoli | Juan Diaz Gutierrez | Francisco Jose Diaz Gutierrez

