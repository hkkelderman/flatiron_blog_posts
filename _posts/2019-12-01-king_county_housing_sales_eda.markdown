---
layout: post
title:      "King County Housing Sales EDA"
date:       2019-12-02 01:51:55 +0000
permalink:  king_county_housing_sales_eda
---


As a research analyst for an environmental non-profit, cleaning and analyzing data for reports and projects is not a new experience for me, though having to do it all using Python (as up until this point I did most of my work in Excel), was a little overwhelming. I was assigned a project that required me to clean, explore, and model housing data from King County, Washington. Instead of going through my whole process in how I worked through this project, I wanted to highlight an issue I ran into when it came to the Exploratory Data Analysis (EDA) portion. During this aspect of the project, I was required to generate and then answer three questions through EDA. I thought all of my questions would have been answerable with this dataset, but as it turns out, two of the three I asked were left mostly unanswered. I want to explain why I couldn’t answer them, and how I might be able to answer these questions in the future.

#### My first question

First, does renovating a house increase the sale value of a house? And if it does, what types of renovations cause the largest increase in sale value?

I thought these would be simple enough to answer, all I needed was a subset of the original data that contained houses that had been sold multiple times and had also been renovated. The following columns were used to create that subset:

* ‘id’ - a column of unique IDs for each house in the dataset
* ‘yr_renovated’ - a column with the year the house was renovated 

The first step I took was creating a new column (‘renovated’) that would show whether or not a house had been renovated, regardless of the year. Next, I subsetted the original dataframe by filtering the ‘id’ column for just those IDs that appeared multiple times (these were not duplicates, but instead houses that were sold multiple times at different prices). Lastly, I took a subset of that dataframe by filtering the ‘renovated’ column for only those houses that had been renovated, and was left with a dataframe that only had eight rows and four unique house IDs.

<a href="https://imgur.com/HAfs5S8"><img src="https://i.imgur.com/HAfs5S8.png" title="source: imgur.com" width="300" height="300"/></a>

This was a bit upsetting, as I thought this would have been an interesting answer to find out, but clearly with only eight rows and four houses, I was not going to find anything useful from this small subset; my questions had narrowed the data too much. Upon further inspection, I also happened to notice that for all four of these houses, none of the renovations took place in between the two dates of sale, all of them had undergone renovations before the first date sold. Now, in addition to being too small, the subset of data was no longer capable of answering my question.

Since I no longer was able to answer my original questions, I ran a couple of statistical checks on the original dataset, to see if there were some differences in houses that had been renovated and houses that had not. What I found, was that on average, renovated houses were not only larger than non-renovated houses, but they also sold for at least $200 thousand more.

My hope was that when I subsetted the original dataframe for houses that had been sold multiple times and had been renovated, I would be able to see if the price of the house went up after the renovation. I was also hoping that I would be able to see which aspects of the house changed after the renovation (like number of bathrooms or square feet of living space), to determine if certain changes to the house would lead to larger resale prices. The only way I’d be able to answer this question in the future is with a much larger dataset over a longer period of time.

### My second question

More people seem to be downsizing their lives. Getting rid of cars, having less stuff, moving to cities, and buying smaller homes. Does the housing data in King County support this? Are more people buying smaller houses?

Now it’s no secret that people are buying smaller homes, just look at the front page of Google when you search “people buying smaller homes”:

<a href="https://imgur.com/MqwFgNi"><img src="https://i.imgur.com/MqwFgNi.png" title="source: imgur.com" width="400" height="700"/></a>

*Searched on 11/25/2019*

I wanted to see if the housing data from King County, WA would support this trend, but it does not. After a quick check in the square footage of living space over the years, it’s quite clear that houses have only increased in size.

<a href="https://imgur.com/F9E5miF"><img src="https://i.imgur.com/F9E5miF.png" title="source: imgur.com" width="500" height="300"/></a>

If you look more closely, from 2000 through 2015, you’ll see that there is in fact a decrease from 2000 until about 2009, but since 2009, the size increased again almost back to where it was in 2000.

<a href="https://imgur.com/z3b2s6R"><img src="https://i.imgur.com/z3b2s6R.png" title="source: imgur.com" width="500" height="300"/></a>

My assumption is that this might be more visible with newer data. If we added data for house sales from 2016 through 2018, we might be able to visualize the downsizing in houses. It is important when working with data to always have the most recent data available, otherwise you'll be working with stale information and the results won't be relevant.

### Conclusion

I thought I had come up with some interesting questions for this dataset, for which I thought I’d be able to answer. Unfortunately, I was unable to do so, as the subset of data either became to narrow or there was out of date, unable to explain more current trends. But, this was a good learning experience. I came up with original questions, something I’ve always struggled with, and I learned that there are limits to what data can tell us.


