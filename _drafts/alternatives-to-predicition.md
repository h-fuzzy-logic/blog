---
layout: post
title: Using data for more than prediction
summary: Explore some reasons for creating a model other than prediction 
categories: [Data Science]
mainimageurl: "/img/2019-12-18-alternatives-to-prediction.png"
mainimagealt: "Heatmap"
---

<h1 class="h4">Introduction</h1>
Way back in 2008, The Journal of Artifical Societies and Social Simulation published <a href="http://jasss.soc.surrey.ac.uk/11/4/12.html" target="_blank"> <i>Why Model?</i> </a> which discusses goals for models in addition to prediction.  

<h1 class="h4">Some reasons to create a model other than prediction:</h1>
<ol>
	<li>Explain (very distinct from predict)</li>
	<li>Illuminate core uncertainties</li>
	<li>Demonstrate tradeoffs / suggest efficiencies</li>
	<li>Promote a scientific habit of mind</li>
	<li>Reveal the apparently simple (complex) to be complex (simple) </li>
</ol>
(Head over to <a href="http://jasss.soc.surrey.ac.uk/11/4/12.html" target="_blank">the article</a> for the complete list of 16 alternatives.)


<h1 class="h4">An example of promoting a scientific habit of mind</h1>
For several years now, I’ve heard acquaintances lament: <i>We don’t have spring anymore. We skip spring and go straight to summer. I miss spring-like temperatures.</i>  To see if data supports this belief, I decided to analyze publicly available NOAA weather station data collected from 1910 - 2019 at the Knoxville, TN airport.  

From the statistical analysis done and the visualizations created, there is evidence to support the perception that summer-like temperatures in middle-spring have happened more often since 2005 in Knoxville, TN.

Head over to <a href="https://github.com/h-fuzzy-logic/R---Are-spring-like-temperatures-disappearing" target="_blank">GitHub</a> to see the Jupyter Notebook with the full explanation of definitions used in the analysis plus the R code and ggplot visualizations.    


