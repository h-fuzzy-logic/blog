---
layout: post
title: Using data for more than prediction
summary: While making predictions with data is a frequent goal, having other goals can be useful too
categories: [Data Science, Scientific Habits]
mainimageurl: "/img/2019-12-20-alternatives-to-prediction.jpg"
mainimagealt: "Test tubes"
mainimageattribution: "Photo by Chokniti Khongchum from Pexels"
---

<h1 class="h4">Introduction</h1>
Way back in 2008, <i>The Journal of Artificial Societies and Social Simulation</i> published <a href="http://jasss.soc.surrey.ac.uk/11/4/12.html" target="_blank"> "Why Model?"</a>  which discusses goals for models in addition to prediction.  These are some of my favorites: 

<ul>
	<li>Explain (very distinct from predict)</li>
	<li>Illuminate core uncertainties</li>
	<li>Demonstrate tradeoffs / suggest efficiencies</li>
	<li>Discover new questions</li>
	<li>Reveal the apparently simple (complex) to be complex (simple) </li>
	<li>Expose prevailing wisdom as incompatible with available data</li>
	<li>Promote a scientific habit of mind</li>
</ul>  

Fast forward to 2019 when I often hear acquaintances lament: <i>We don’t have spring anymore. We skip spring and go straight to summer. I miss spring-like temperatures.</i>  My analytical nature wondered if data could support this belief.  To seek out more evidence and to promote a scientific habit of mind, I decided to analyze publicly available NOAA weather station data collected from 1910 - 2019 at the Knoxville, TN airport.  The first order of business: define the terms spring, summer, spring-like and decide how to measure them.  

<h1 class="h4">Promoting a scientific habit of mind</h1>
Using a scientific approach, I translated the complaints into measurable timeframes and temperatures.  When I’ve heard people say <i>We don’t have spring anymore</i>, it is unlikely that they were comparing present-day to the year 1910.  Realizing this allowed me to zoom in on a smaller time frame (1990 - 2010).  Thinking about the comment <i>We don’t have spring anymore</i> made me think that probably people weren’t complaining about the March or June temperatures, that more likely they were complaining about the temperatures in middle-spring (April 1 through May 31).  These are the definitions used in the analysis:

<ul>
	<li>Spring is March 20 to June 21 (94 days)</li>
	<li>A spring-like temperature is 78℉ or below</li>
	<li>A summer-like temperature is 79℉ or above</li>
	<li>The days of focus are April 1 - May 31, or middle-spring which corresponds to Days 12 - 42</li>
	<li>The Historical years are defined as the fifteen year span of 1990 - 2004</li>
	<li>The Recent years are defined as the fifteen year span of 2005 - 2019</li>
</ul>

<h1 class="h4">Results of analysis</h1>
From the statistical analysis done and the visualizations created, there is evidence to support the perception that summer-like temperatures in middle-spring have happened more often since 2005 in Knoxville, TN.

<h1 class="h4">Code</h1>
Head over to <a href="https://github.com/h-fuzzy-logic/R---Are-spring-like-temperatures-disappearing" target="_blank">GitHub</a> to see the Jupyter Notebook of R code and ggplot visualizations.    


