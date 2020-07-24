---
layout: post
title: Visualizing Simpson's Paradox
summary: Exploring CDC COVID-19 data for insights into how race and ethnicity impact COVID-19 numbers in the US
date: 2020-07-24  
categories: [Python, Seaborn, Visualization]
mainimageurl: "/img/stacked-rocks.jpg"
mainimagealt: "Stacked of rocks, showing layers"
mainimageattribution: "Photo by Pixabay from Pexels"
codeexamples: ""
---

<h1 class="h4">Introduction</h1>
I’ve been hearing and reading that race and ethnicity are impacting COVID-19 cases and deaths in the United States, specifically that being non-white in the US increases your chance of getting or drying from COVID-19.  Related to this, I read a blog post titled “Race, COVID Mortality, and Simpson’s Paradox” by Dana Mackenzie (one of the authors of The Book of Why).  I decided to analyze COVID-19 data from the Centers for Disease Control 1) to see if I could see Simpon’s Paradox and 2) to practice visualizing such an important story.  
  
<h1 class="h4">Data disclaimers</h1>
Getting the data involved several manual steps.  At <a href="https://www.cdc.gov/covid-data-tracker/index.html#demographics" target="_blank">the CDC site</a>, I had to click on the charts for the day, switch the view to a tabular view, and grab the percentages from there.  The CDC site notes that race/ethnicity data is unavailable for some of the data.  It is missing in 47% of the cases data and 17% of the deaths data.  I accessed the data on July 12, 2020.  

<h1 class="h4">My assumptions </h1>
When I think about COVID cases and deaths, I assume that when the data is divided by race, it will follow the percentages of the US population.  So I checked out <a href="https://www.census.gov/quickfacts/fact/table/US/PST045219" target="_blank">the US Census Data</a>  and found that 60.1% of Americans are White, not-Hispanic or Latino.  Therefore, I would expect approximately 60% of the COVID cases and deaths should be in the White, not-Hispanic or Latino group.  And that 39.9% should be from non-whites (minorities).

<h1 class="h4">The actual COVID data</h1>
When I looked at <a href="https://www.cdc.gov/covid-data-tracker/index.html#demographics" target="_blank">the CDC data</a> from July 12th, I found that for all ages, 36.6% of cases are in the White, not-Hispanic or Latino group and 49.7% of the deaths are from that group.  Both percentages are below my expectation (60%).  And when I explore the CDC charts by Age AND Race/Ethnicity, the trends are hard to spot because of the way the data is visualized: <a href="{{ site.baseurl }}/img/cdc-all-ages.png" target="_blank">screenshot 1</a>, <a href="{{ site.baseurl }}/img/cdc-by-ages-group.png" target="_blank">screenshot 2</a>, and <a href="{{ site.baseurl }}/img/cdc-all-ages-table.png" target="_blank">screenshot 3 (tablular view)</a>. So here is my attempt to visualize it better, using Python and Seaborn.  


<h1 class="h4">Visualized with bar charts</h1>
 <img src="{{ site.baseurl }}/img/cases-bar.png" class="img-fluid" alt="Cases as a bar chart"/>
 <img src="{{ site.baseurl }}/img/deaths-bar.png" class="img-fluid" alt="Deaths as a bar chart"/>

<h1 class="h4">Visualized in table format</h1>
 <img src="{{ site.baseurl }}/img/cases-table.png" class="img-fluid" alt="Cases in table format"/>
 <img src="{{ site.baseurl }}/img/deaths-table.png" class="img-fluid" alt="Deaths in table format"/>

<h1 class="h4">Conclusion</h1>








