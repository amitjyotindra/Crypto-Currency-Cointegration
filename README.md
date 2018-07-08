# Statistical Arbitrage in R
[By Jacques Joubert] (https://za.linkedin.com/in/jacquesjoubert)

For those of you who have been following my blog posts for the last 6 months will know that I have taken part in the Executive Program in Algorithmic Trading offered by QuantInsti.

It’s been a journey and this article serves as a report on my final project focusing on statistical arbitrage, coded in R. This article is a combination of my class notes and my source code.

I uploaded everything to GitHub in order to welcome readers to contribute, improve, use, or work on this project. It will also form part of my [Open Source Hedge Fund project](http://www.quantsportal.com/home/collection/open-source-hedge-fund/) on my blog QuantsPortal

## History of Statistical Arbitrage:

*	First developed and used in the mid 1980s by Nunzio Tartaglia’s quantitative group at Morgan Stanly
*	Pair Trading is a “contrarian strategy” designed to harness mean-reverting behavior of the pair ratio
*	David Shaw, founder of D.E Shaw & Co, left Morgan Stanley and started his own “Quant” trading firm in the late 1980s dealing mainly in pair trading

## What is Pair Trading:
Statistical arbitrage trading or pairs trading as it is commonly known is defined as trading one financial instrument or a basket of financial instruments – in most cases to create a value neutral basket.

It is the idea that a co-integrated pair is mean reverting in nature. There is a spread between the instruments and the further it deviates from its mean, the greater the probability of a reversal.

Note however that statistical arbitrage is not a risk free strategy. Say for example that you have entered positions for a pair and then the spread picks up a trend rather than mean reverting.  

## The Concept:

* Step 1: Find 2 related securities
Find two securities that are in the same sector / industry, they should have similar market capitalization and average volume traded. 
An example of this is Anglo Gold and Harmony Gold. 

* Step 2: Calculate the spread
In the code to follow I used the pair ratio to indicate the spread. It is simply the price of asset A / price asset B.

* Step 3: Calculate the mean, standard deviation, and z-score of the pair ratio / spread.

* Step 4: Test for co-integration
In the code to follow I use the Augmented Dicky Fuller Test (ADF Test) to test for co-integration. I set up three tests, each with a different number of observations (120, 90, 60), all three tests have to reject the null hypothesis that the pair is not co-integrated.

* Step 5: Generate trading signals
Trading signals are based on the z-score, given they pass the test for co-integration. In my project I used a z-score of 1 as I noticed that other algorithms that I was competing with were using very low parameters. (I would have preferred a z-score of 2, as it better matches the literature, however it is less profitable)

* Step 6: Process transactions based on signals

* Step 7: Reporting
