---
layout: post
title:      "Wildfire Capstone - Part 2"
date:       2021-01-27 03:46:54 +0000
permalink:  wildfire_capstone_-_part_2
---


It was pretty clear from my last post that the predictor variables I was using for the multiple linear regression model I was trying to generate for the wildfire dataset did not have a clear, linear relationship with my target variable. For some context, my predictor variables were climate data (max temperature, min temperature, precipitation), geographic data (state or ecoregion), and some fire condition data (temperature) and I was trying to predict the burn area of the wildfire (acres).

Due to there being no existing relationship between any of my predictors and my target, as well as some missing data (topographic, fuel type, human response, and more fire weather conditions), my linear regression models didn’t turn out. After a conversation with my instructor, he asked why I didn’t try any nonparametric models. The short answer: I didn’t think to.

So, I went back and tried to create a Random Forest Regressor (RFR) that would still predict the burn area of a fire, but without the requirement of already existing linear trends in the data. Before I go over the results of my RFR, I want to reiterate a point I brought up in my last post. This dataset is missing a lot of data that could make these models better. As mentioned earlier, knowing the topographical features, fuel type, human response, and fire weather conditions for all of these fires would make a more robust model than I could generate here. Because of this, I chose to simply generate one model to see what the results might be, rather than going through the same process I went through last time with the linear regression models.

After fitting my RFR model with the training data and calculating some performance metrics, the results were mixed. My r-squared value was infinitely better than any of the scores I generated from the linear regression models (**0.855**), however, my mean absolute error (**10,866 acres**) was garbage. The mean absolute error meant that anytime my model predicted fire size, it was off, on average, by **10,900 acres**. In other words, I had overfit my model. It did a great job with the training data, but had a hard time with the test data.

I could go through and remove some of the variables experiencing collinearity and use feature selection to reduce the number of variables used in my decision trees, but that’s a task for another day and with better data. For now, it was worthwhile to know that there's another way to approach regression modeling when linear regression doesn't seem to be working.

