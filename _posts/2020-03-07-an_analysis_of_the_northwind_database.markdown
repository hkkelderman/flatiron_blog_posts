---
layout: post
title:      "An Analysis of the Northwind database"
date:       2020-03-07 18:17:33 +0000
permalink:  an_analysis_of_the_northwind_database
---


Well, it’s hard to believe that I’m almost halfway through with the Data Science Course. It feels like I only just started, but here I am finishing up my third module and my second independent project. The deliverables for the Mod 3 were to generate questions that you were then supposed to analyze with statistical testing about the Northwind database. For a bit of background, the Northwind database is an SQL database created by Microsoft that contains information about a fictional company, Northwind Traders.

Flatiron kickstarted the project by giving me the first question to answer, but I was then required to come up with 3 additional questions. This post will be a reflection on the process and what I learned from answering one of those questions.

## My Question

>  Do some product categories generate more money per order for Northwind Traders than others?

The Northwind database contains information regarding the sales of various products, and these products belong to eight different product categories. I wanted to see, based on the average order cost of these product categories, which product type generates the most money per order for the company.

### Null Hypothesis

> There is no statistical significance between the amount of money each product category generates per order.

## Alternative Hypothesis

> Some product categories do make significantly more money per order than others.

## Analysis

After pulling the required information from the database, and calculating the order cost for each order in each product category, I checked the distribution of order costs for each category and found that some categories had pretty large outliers. I removed all orders that were above \$2,000 and then ran statistical testing on the resulting data.

I used a **Tukey’s Range Test** (documentation found here) to determine significance. A Tukey’s Range Test compares each sample group against every other sample group, and returns a table depicting which pairings can reject the null hypothesis and which cannot. Here is a portion of the resulting table from my test.

<a href="https://imgur.com/jbH0CV9"><img src="https://i.imgur.com/jbH0CV9.png" title="source: imgur.com" width="707" height="325" /></a>


The python function for the Tukey’s Range Test also has this nice built in method that allows you to visualize this information.

<a href="https://imgur.com/XpXgs5M"><img src="https://i.imgur.com/XpXgs5M.png" title="source: imgur.com" width="707" height="325" /></a>

As you can see by now, some categories do in fact generate more money per order than others, though it’s not as clear cut as one would hope. By looking at the visualization you can see that there are some categories with a lot of overlap in their confidence intervals. These correspond to the pairings in the table that cannot reject the null hypothesis.

However, from this, I was able to create a grouping of various categories.

1) **Group 1** (Categories with highest average order value)
* Produce
* Dairy Products


2) **Group 2**
* Grains/Cereals
* Confections
* Condiments


3) **Group 3** (Categories with lowest average order value)
* Seafood
* Beverages
* Meat/Poultry


To try and tighten up the order even more, I calculated the effect size using **Cohen’s d**, between each pairing and created a more specific order based off the effect size between **Produce** and each other category.

<a href="https://imgur.com/vnkAkBL"><img src="https://i.imgur.com/vnkAkBL.png" title="source: imgur.com"  width="450" height="246"/></a>

1) **Produce:** $598.10/order


2) **Dairy Products:** $534.03/order


3) **Condiments:** $451.62/order


4) **Grains/Cereals:** $446.54/order


5) **Confections:** $421.38/order


6) **Seafood:** $371.66/order


7) **Beverages:** $366.20/order


8) **Meat/Poultry:** $268.77/order


It should be remembered though that certain groups of categories don’t show a statistically significant difference, like **Condiments**, **Grains/Cereals**, and **Confections**.

## Conclusion
The reason this question is important is because it is one of many metrics that can be used to determine which parts of the company are more profitable than others. It can also be used in tandem with some basic calculations to identify areas where the company should invest more time to generate more income.

In this example, the **Produce** category of products sold by Northwind Traders makes statistically more money per order than every other category but **Dairy Products**, but it has the second fewest number of orders.

<a href="https://imgur.com/bmWeAqd"><img src="https://i.imgur.com/bmWeAqd.png" title="source: imgur.com" width="236" height="301" /></a>

If I were Northwind, I would start having my employees try to sell more **Produce**, since there is a lot of potential for growth and increased income.

