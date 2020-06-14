---
layout: post
title:      "Tanzanian Water Well Data"
date:       2020-06-14 17:51:37 +0000
permalink:  tanzanian_water_well_data
---


For the Data Science Curriculum 2.1 Module 3 project (between finishing my last project for Module 3, the curriculum changed and here I am finishing another Module 3 project), I was required to create a classification model using a dataset of my choosing, either from a curated list they provided, or from a datasource I found on my own.

I ended up going with one of the datasets provided, [Tanzanian Well Water Data](https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/page/23/), which happened to be in an active competition. The goal of this competition was to come up with a classifier that used data from Taarifa and the Tanzanian Ministry of Water to predict whether a well was functional, non-functional, or in need of repair. The dataset included variables like surrounding population, region, quality of water, type of pump, etc. for each individual well. Using those variables, I was tasked with trying to create the most accurate classifier.

Your score in the competition was your classification rate (or accuracy), which was the percentage of rows where the predicted class (y_hat) matched the actual class (y), however, I don’t think this is the best metric to use for a competition like this.

Below is the spread of wells among the three different labels in my training dataset:

1. Functional: **21,121**
2. Non-functional: **14,691**
3. Functional, in need of repair: **2,783**

As you can see, our data is highly unbalanced. The wells in need of repair, arguably our most important class of wells, only make up 7% of the total wells. Of course I balanced the data for the different classification methods used, but because the wells in need of repair are such a small subset of the whole dataset, I would argue that the recall score for the wells in need of repair is a much more important metric than the overall accuracy of the model.

Recall, in regards to the third group of wells, is the proportion of wells in need of repair correctly classified as “in need of repair.” This means that the higher our recall score for this label, the higher the proportion of wells in need of repair we correctly labeled as such. The reason recall is better than accuracy in this instance, is that accuracy can lead to false assumptions regarding the performance of the model. For example, the model could accurately predict all functional and non-functional wells and incorrectly predict all wells in need of repair, but as I mentioned earlier, wells in need of repair only account for 7% of all the wells, meaning our model would have an accuracy score of 93%. If instead, if we focus more on increasing the recall score for wells in need of repair, we will have a model that correctly predicts a larger portion of wells in need of repair, but most likely at the expense of the overall accuracy.

The reason all this matters is because being able to identify and predict a higher number of wells in need of repair will allow for the government and NGOs to go out to those wells and fix them, leaving a larger number of communities with working wells and access to drinking water. 

