---
layout: post
title: Are spring-like temperatures disappearing in Knoxville, TN?
summary: Analyzing 110 years of temperature data to see if perceptions about a shorter spring season can be supported with data
date: 2020-05-01  
categories: [EDA, R, Statistics, Heatmap, Project]
mainimageurl: "/img/summer-like-temps.png"
mainimagealt: "Heatmap showing middle-spring days with summer-like temperatures from 1990 to 2019"
mainimageattribution: "Heatmap showing middle-spring days with summer-like temperatures from 1990 to 2019"
codeexamples: "https://github.com/h-fuzzy-logic/R---Are-spring-like-temperatures-disappearing/blob/master/Analyzing%20110%20Years%20of%20NOAA%20Weather%20Station%20Data.ipynb"
---

<h1 class="h4">Introduction</h1>
I often hear acquaintances lament: <i>We don’t have spring anymore. We skip spring and go straight to summer. I miss spring-like temperatures.</i>  My analytical nature wondered if data could support this belief.  To find evidence, I decided to analyze publicly available NOAA weather station data collected from 1910 - 2019 at the Knoxville, TN airport.  

<h1 class="h4">Finding data to analyze</h1>
<a target="_blank" href="https://www.ncdc.noaa.gov/cdo-web/search">NOAA's Climate Data Online Search tool</a> allows searching and downloading past weather and climate data.  After some trial and error, I was able to retrieve air temperature data from the weather station at the Knoxville, TN airport from 1910 to 2019.  Each row in the CSV file contained the datetime of the observation, the average temperature for the day, the maximum temperature for the day, minimum temperature for the day, and the temperature at the time of the observation.  NOAA provides <a href="https://www.ncdc.noaa.gov/cdo-web/datasets#GHCND" target="_blank">documentation </a> which describes the dataset in more detail.

<h1 class="h4">Translating perceptions into something that can be measured</h1>
Next, I translated the complaints into measurable time frames and temperatures.  When I’ve heard people say <i>We don’t have spring anymore</i>, it is unlikely that they were comparing present-day to the year 1910.  Realizing this allowed me to zoom in on a smaller time frame (1990 - 2010).  Thinking about the comment <i>We don’t have spring anymore</i> made me think that probably people weren’t complaining about the March or June temperatures, that more likely they were complaining about the temperatures in middle-spring (April 1 through May 31).  These are the resulting definitions used in the analysis:
<ul>
	<li>Spring is March 20 to June 21 (94 days)</li>
	<li>A spring-like temperature is 78℉ or below</li>
	<li>A summer-like temperature is 79℉ or above</li>
	<li>The days of focus are April 1 - May 31, or middle-spring, which corresponds to Days 12 - 72</li>
	<li>The Historical years are defined as the fifteen year span of 1990 - 2004</li>
	<li>The Recent years are defined as the fifteen year span of 2005 - 2019</li>
</ul>

<h1 class="h4">Comparing the "hotness" of each year</h1>
Counting the number of summer-like days in middle-spring is one approach to quantifying the "hotness" of each year.  My thinking is that having summer-like days when the temperatures should be spring-like contributes to the perception <i>We don’t have spring anymore.</i>   And that having more summer-like days in middle-spring in recent years could explain the complaints.  If spring seasons are staying the same from year to year, then I'd expect the number of summer-like days to be mostly consistent from year to year.  

<h1 class="h4">Analysis of the number of summer-like days</h1>
There is evidence to support the perception that summer-like temperatures in middle-spring have happened more often since 2005 in Knoxville, TN.

The heatmap above shows more summer like days on the right (as spring progresses), which is to be expected.  Starting at Day 58, the year 2018 has 14 consecutive summer-like days and 2019 has 15 consecutive summer-like days.  Since these are the two most recent years, they are likely the most memorable, and could be overly influential in people's perceptions. 

The boxplots below compare the count of summer-like days per year in the two time frames Historical (1990 - 2004) and Recent (2005 - 2019).  My thinking for analyzing the data this way is that if spring temperatures are staying steady from year to year, then the distribution of number of summer-like days should look similar in Historical and Recent time frames.  The Historical median is 25 summer-like days and the Recent median of summer-like days is 31, meaning on average the Recent time frame has 6 more summer-like days.  The interquartile range for Historical is 7 and for Recent is 9, showing that the Recent time frame has more variance on the number of summer-like days and is less consistent.     

<img src="{{ site.baseurl }}/img/middle-spring.png" class="img-fluid" alt="User 1 session summary"/>

<h1 class="h4">Closing</h1> 
Check out this <a href="{{ page.codeexamples }}" target="_blank"> Jupyter notebook</a> for the code and more detailed analysis of each visualization.  






