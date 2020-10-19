---
layout: post
title:      "Zillow Time Series Analysis"
date:       2020-10-19 01:13:15 +0000
permalink:  zillow_time_series_analysis
---


Well, here I am, completing my final end-of-module project before I move on to my capstone! It seemed like forever ago I started this program, and here I am in my final stretch.

For Module 4, there were a variety of different final project options, but I ended up going with the time series project. The goal of this particular project was to forecast real estate prices for particular zip codes using historical median housing data from Zillow. Ultimately, I needed to answer the question: 

> What are the top 5 best zip codes to invest in?

#### Background/Data Exploration

The dataset included median house sales by zip code as far back as 1996 for over 14,000 zip codes. That’s a lot of zip codes! And since the time series modeling method I used (AutoRegressive Integrated Moving Average, or ARIMA) only generated one model per zip code, it was pretty important I dig into the data first to determine which zip codes would be best for modeling.

First, I chose to limit my data to median housing sales from 2009 onward. I chose to narrow my analysis to this timeframe to account for the housing bubble burst in 2008. By starting in 2009, the median housing sales will have reached, or come close to, their lowest point since the burst and would be on the rise again.

I then chose to look at both profit margin and return on investment (ROI) for each zip code. These stats let me look at the change in property value from a start date (January 2009) to an end date (April 2018) and see which zip codes returned higher profit margins or returns on investment, allowing for me to hone in on which zip codes would eventually be modeled. I looked first at average profit margin and ROIs by metro area, before zooming into zip codes, and what I found was pretty interesting. All the top metro areas are located out west, while some of the top zip codes include regions on the east coast.

**Top Metro Areas (ROI)**
<a href="https://imgur.com/MYpliZx"><img src="https://i.imgur.com/MYpliZx.png" title="source: imgur.com" width="707" height="400" /></a>

**Top Zip Codes (ROI)**
<a href="https://imgur.com/PvyQhxJ"><img src="https://i.imgur.com/PvyQhxJ.png" title="source: imgur.com" width="707" height="400" /></a>


#### ARIMA Modeling

I then took the top 10 zip codes (both lists of top 10 zip codes for profit margin and ROI included the same 10 zip codes) and started generating ARIMA time series models. In the first round, I just used the standard values for *p*, *d*, and *q* (1,1,1), but I found that though some models did alright with these parameters, others did not. I then created multiple models for each zip code, using each iteration of 1-5 used for each of the three parameters, and wound up with some models that seemed to fit the testing data a bit better. Then, finally, I generated a final model for each zip code using the best parameters for each.

##### **First Round Models**
**Good**

<a href="https://imgur.com/IX2hb1o"><img src="https://i.imgur.com/IX2hb1o.png" title="source: imgur.com" width="300" height="200" /></a>

**Bad**

<a href="https://imgur.com/7lNH7aK"><img src="https://i.imgur.com/7lNH7aK.png" title="source: imgur.com" width="300" height="200" /></a>

#### Summary/Findings
With a final model for each zip code, I forecasted the median housing sales data one year out and three years out, which resulted in the following recommendations for investment (based on ROI):

**One year:**

1. 94043 - Mountain View, CA - 17.3% ROI
2. 15201 - Pittsburgh, PA - 16.8% ROI
3. 80204 - Denver, CO - 16.0% ROI
4. 80010 - Aurora, CO - 14.8% ROI
5. 11222 - New York City, NY - 14.4% ROI

**Three years:**

1. 15201 - Pittsburgh, PA - 58.4% ROI
2. 94043 - Mountain View, CA - 57.7% ROI
3. 80204 - Denver, CO - 56.0% ROI
4. 80010 - Aurora, CO - 52.7% ROI
5. 11222 - New York City, NY - 48.4% ROI

I think it's best to base investment decisions off the one-year predictions, as the model will have more uncertainty the farther out you forecast.

#### Future Work

This was a very basic approach to determining potential real estate investment opportunities. The median housing sales by zip code dataset provided by Zillow is a little too simple to provide robust predictions on future housing sales. There are a lot of other factors to consider when investing in real estate:

**Resale value**, which can be affected by:

* proximity to amenities like grocery stores, transit lines, entertainment venues, etc.
* economic growth within the community; are there a lot of available jobs
* status of local schools and other opportunities for education

**Risk**, which is measured by:

* increasing vacancies
* declining rents
* economic downturn

And with these factors come other considerations. How long do you plan to own the property? Do you plan to fix up the house and resell? Or do you plan to just buy and hold the property for a longer timeframe, selling it once the price has increased a substantial amount?

With all these things in mind, you can see why this particular dataset is a little too simple for predicting solid investments. What with only providing the historical median housing sales by zip code, it's hard to calculate things like risk or account for factors that might affect resale value, like economic growth and proximity to amenities.

By pairing the Zillow dataset with other datasets, like Census data, economic growth, and other housing datasets that include additional data related to risk, profitability, and proximity, you'd be able to create a much more robust model and be able to recommend better potential targets for investment.

