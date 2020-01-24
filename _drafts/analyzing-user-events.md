---
layout: post
title: Making sense of user events 
summary: Using Python to gain insight from detailed user event logs   
categories: [Python, Pandas, Exploratory Data Analysis, EDA, User Events]
mainimageurl: "/img/2019-12-02-customizing-css-for-jupyter-notebooks-1.png"
mainimagealt: "Event data"
---

<h1 class="h4">Introduction</h1>
Imagine gigs and gigs of data captured for months as users tap through a mobile app - timestamps, session ids, event codes, location in the app, and even the location of tap on the screen.   It can seem overwhelming to gain insights from this type of data, but that is the goal of the <a href="https://www.kaggle.com/c/data-science-bowl-2019/overview" target="_blank">2019 Data Science Bowl sponsored by Kaggle</a>.  The competition provided CSV files with these columns:
<ul>
	<li>event_id</li>
	<li>game_session</li>
	<li>timestamp</li>
	<li>event_data (a string representing JSON-formatted data)</li>
	<li>installation_id</li>
	<li>event_count</li>
	<li>event_code</li>
	<li>game_time</li>
	<li>title</li>
	<li>type</li>
	<li>world</li>
</ul>

<h1 class="h4">What are the challenges of working with this kind of data?</h1>
<ul>
	<li>Processing such a large amount of data take a lot of time cause out of memory errors. </li>
	<li>Because the data is structured in such a detailed way (i.e., a timestamp for each user event), it is hard to spot trends or patterns.</li>
	<li>Becuase so many users are represented, it is difficult to know if calculations are "correct"</li>
	<li>Parsing and understanding JSON data can be tricky.</li>
</ul>
Below are ideas and code samples for handling each challenge.


<h1 class="h4">Reducing processing time and prevening memory errors</h1>
Be mindful of which columns of data are needed for the task at hand.  For example, if answering the question "When do most users play," then only use the relevant columns (probably installation_id and timestamp in this data).  This might mean only reading in certain columns from the CSV file and/or dropping nonessential columns from dataframes.  

When coding, be open to different ways to accomplish the task at hand.  For example, Python and Pandas provide many different ways add a column to a dataframe.  And over time frameworks added faster and faster functionality.  Be sure if you are using a Q & A site (like StackOverflow) to check the date on the accepted answer to make sure it is recent.  
```Python
#older to newer methods of adding a column to a dataframe
df1['e'] = <<new values>>
df1.loc[:,'e'] = <<new values>>
df1 = df1.assign(e = <<new values>>)
##insert and apply?

```
<h1 class="h4">Spotting trends and patterns</h1>
Thinking about how one user interacts with the app is a good staring point and there are many different metrics that can be calculated per user with the Data Science Bowl data.  Popular usage times can be determined by analyzing the timestamp column to determine the most common days of the week or times of day that the app is used.  Event codes that represent user-initiated actions (such as starting an assessment, asking for help, skipping a tutorial, etc.) can be summed for each user.   Analyzing the location of mouse clicks can show what users find important.  By analyzing events in timestamp order, the user's path through the system can be seen.  Organizing the data by user can provide powerful information about how the most successful players use the app.  For an example of how to summarize event codes by user, see $$$
$$ need image of data frame.  


<h1 class="h4">Parsing JSON data</h1> 
For background information about how JSON data is structured and its advantages, visit <a href="https://www.json.org/json-en.html">JSON.org</a>.  Python provides functionality to handle JSON data.  The <a href="https://docs.python.org/3.7/library/json.html" target="_blank">loads method in the json module<a>  accepts a string (like the event_data column in the CSV file from the Data Science Bowl) and will return a Python object for easier manipulation.  Once the Python object is created, it is easier to find specific keys and values (such as correct is set to true).  For the Data Science Bowl, event_data column had to be used to determine if the user got the correct answer for an assessment.  For code samples see ####



QA  

