---
layout: post
title: Gaining insights from user-generated event data
summary: Using Python and Pandas to gain insight from detailed user event logs   
categories: [Python, Pandas, Exploratory Data Analysis, EDA, User Events]
mainimageurl: "/img/2020-1-26-analyzing-user-events.jpg"
mainimagealt: "Event data"
mainimageattribution: "Photo by Vitaly Vlasov from Pexels"
codeexamples: "https://github.com/"
---

<h1 class="h4">Introduction</h1>
Imagine gigs and gigs of data captured for months as users tap through a mobile app - timestamps, session ids, event codes, location in the app, and even the location of the tap on the screen.   It can seem overwhelming to gain insights from this type of data, but that is the goal of the <a href="https://www.kaggle.com/c/data-science-bowl-2019/overview" target="_blank">2019 Data Science Bowl sponsored by Kaggle</a>.  The competition provided CSV files with these columns:
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
	<li>Processing such a large amount of data take a lot of time and cause out of memory errors. </li>
	<li>Because the data is structured in such a detailed way (i.e., a timestamp for each user event), it is hard to spot trends or patterns.</li>
	<li>Because so many users are represented, it is difficult to know if calculations are correct.</li>
	<li>Parsing and understanding JSON data can be tricky.</li>
</ul>
Below are ideas and code samples for handling each challenge.

<h1 class="h4">Reducing processing time and preventing memory errors</h1>
<p class="ml-4"><text class="font-weight-bold">Be mindful of which columns of data are needed for the task at hand.</text> <br/> 
For example, if answering the question "When do most users play," then only use the relevant columns (timestamp and possibly installation_id in this data).  This might mean only reading certain columns from the CSV file and/or dropping nonessential columns from dataframes.
</p>

<p class="ml-4">
<text class="font-weight-bold">Be open to different ways to accomplish the task at hand and be sure you understand the impact of each operation.</text>
For example, Pandas provides many different ways add a column to a dataframe.  Some of them create a new dataframe (leaving the original alone), while some do not create a new dataframe.  And over time frameworks added faster and faster functionality.  Be sure if you are using a Q & A site (like StackOverflow) to check the date on the accepted answer to make sure it is recent.  Consulting the documentation (such as <a href='https://pandas.pydata.org/docs/index.html'> Pandas docs</a>) can help too. 
</p>

<pre class="ml-4">
<code class="language-Python">
#different ways to add a column to a dataframe
df1['e'] = &lt;&lt;new values&gt;&gt;
df1.loc[:,'e'] = &lt;&lt;new values&gt;&gt;
df2 = df1.assign(e = &lt;&lt;new values&gt;&gt;)
</code>
</pre>

<h1 class="h4">Spotting trends and patterns</h1>
<p class="ml-4">
<text class="font-weight-bold">Start with how one user interacts with the app.</text>  There are many different metrics that can be calculated per user with the Data Science Bowl data.  Analyzing the timestamp column can pinpoint the most common days of the week or times of day that the app is used.  Summing event codes (that represent user-initiated actions such as starting an assessment, asking for help, skipping a tutorial, etc.) by user can show what actions are taken most often.  Analyzing the location of mouse clicks can show what users find important.  By analyzing events in timestamp order, the user's path through the system can be seen. Organizing and visualizing the data by user can provide powerful information about how the most successful players use the app.  Check out this <a href="{{ page.codeexamples }}" target="_blank"> Jupyter notebook</a> for examples of how to summarize event codes by user.              
</p>

<div class="mb-4">
	<img alt="Datafame of event summary" class="img-thumbnail" src="../img/EventSummary.png" />
</div>  

<h1 class="h4">Finding errors and mistakes early and often</h1>
<p class="ml-4">
<text class="font-weight-bold">Verify that each transformation/calculation matches the expectation from the raw data.</text>  With the Data Science Bowl data, the test.csv file shows that game_session <code class="font-italic">000326e9d4516dd0</code> has 301 events. Once this expectation is known, it can be compared with the actual value after each transformation or calculation and code can be written to show alerts for mismatches. The expected number of events can be determined several ways: 
<ul>
	<li>Manually counting the events in the file </li>
	<li>Using the "Find" feature in a text tool (such as TextEdit) that shows the number of occurrences</li>
	<li>Writing code to calc the expected number as soon as the file is read into the development environment and before any transformations</li>
</ul>
</p>

<p class="ml-4">
<text class="font-weight-bold">Verify values in each column are within expected ranges.</text>  Finding the distinct (or unique) values, the min value, and the max value for each column can uncover mistakes.  Check out this <a href="{{ page.codeexamples }}" target="_blank"> Jupyter notebook</a> for examples of how to find errors and mistakes early and often.
</p>


<h1 class="h4">Understanding JSON data</h1> 
<p class="ml-4">
<text class="font-weight-bold">Get comfortable with JSON.</text>
The Data Science Bowl data presents event detials in JSON format and Python provides functionality to handle JSON data.  The <a href="https://docs.python.org/3.7/library/json.html" target="_blank">loads method in the json module<a>  accepts a string (like the event_data column in the CSV file from the Data Science Bowl) and will return a Python object for easier manipulation.  Once the Python object is created, it is easier to find specific keys and values (such as <code class="font-italic">correct</code> is set to <code class="font-italic">true</code>).  For the Data Science Bowl, event_data column had to be used to determine if the user got the correct answer for an assessment.  For background information about how JSON data is structured, visit <a href="https://www.json.org/json-en.html">JSON.org</a>.  Check out this <a href="{{ page.codeexamples }}" target="_blank"> Jupyter notebook</a> for examples of how to handle the event_data column from the Data Science Bowl.
</p>



