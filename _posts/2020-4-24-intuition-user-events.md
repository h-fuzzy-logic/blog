---
layout: post
title: Exploratory data analysis of user generated events
summary: Focusing on a few users can offer clues about the "typical" user and guide decisions about features
date: 2020-4-24   
categories: [EDA, User Events, Python]
mainimageurl: "/img/neon-party.jpg"
mainimagealt: "Crowded neon party"
mainimageattribution: "Photo by Marcin Dampc from Pexels"
codeexamples: "https://github.com/h-fuzzy-logic/Python-Visualizing-User-Events-By-Session/blob/master/Visualizing%20User%20Events%20By%20Session.ipynb"
---

<h1 class="h4">Introduction</h1>
Event data is often created as users navigate from screen to screen while using websites and other software.  Engineering features for this type of data can be tricky. There can be lots of data and it may first seem unpredictable and hard to wrangle, just like the swarm of people pictured above at a neon party. Even finding publicly available user generated event data to explore can be hard, but Kaggle’s 2019 Data Science Bowl offers a wonderful opportunity to practice wrangling this type of data. The goal of the competition is to determine how different media types can improve performance on in-game assessments.  
       
<h1 class="h4">Data Details</h1>
The competition data is anonymous gameplay data from kids using the PBS Kids Measure Up! app and is organized by installation and session.  The events are logged in sequence during gameplay which results in an overwhelming amount of detailed data. Avoiding out of memory errors and performance issues while doing exploratory data analysis and running models is just as challenging as grasping the paths of typical users. To make getting started less overwhelming, there are several ideas below with specific examples related to the competition.  

<h1 class="h4">Tips for developing an understanding a "typical" user</h1>
1. Try to truly understand the data and how each logged event corresponds to gameplay
* For the competition, I could play the MeasureUp! app and have the same experience as a user.
1. Read any available documentation 
* Kaggle Discussion had an article called <a href="https://www.kaggle.com/c/data-science-bowl-2019/discussion/115034" target="_blank">Measure Up! media types introduction</a>  which explained the different media types (Clip, Activity, Game, or Assessment). 
1. Get clarity about the allowable paths through the system
* Is the user forced to take ordered steps or can media/screens be accessed in a haphazard way? 

<h1 class="h4">Exploratory data analysis to build intuition</h1>  
Chapter 6 of the book <i>Doing Data Science: Straight Talk from the Frontline</i> has useful advice about exploring the data from from a single user’s point of view.  This can be done in a variety of ways, including plotting events over time for different users.  Specificially for the competition, plotting the media types accessed by users on a timeline and then comparing the gameplay approaches to assessment outcomes can start to uncover which media types and gameplay patterns create higher assessment outcomes.  The plots below show two different approaches to playing the game.  Game events are blue; Clip events are orange; Activity events are green; Assessment events are red.

<h1 class="h5">Narrative for User 1</h1>
User 1 played 20 sessions, with the longest one lasting around 8 minutes.  User 1 mostly experienced Clip and Game media types and only attempted one Assessment. 
<img src="{{ site.baseurl }}/img/user1.png" class="img-fluid" alt="User 1 session summary"/>

<h1 class="h5">Narrative for User 2</h1>
User 2 played 42 sessions, none lasting longer than 5 minutes.   User 2 experienced all four media types (Game, Clip, Activity, and Assessment) and attempted an Assessment 10 times.  
<img src="{{ site.baseurl }}/img/user2.png" class="img-fluid" alt="User 2 session summary"/>

A next step could be checking the users' assessment outcomes to see which type of gameplay resulted in higher assessment outcomes. 

<h1 class="h4">Using intuition to engineer features</h1> 
Initially exploring the data from a single user perspective can help generate ideas about which variables correlate to having a positive assessment outcome, such as:
* Viewing Clips, Activities, or Games prior to taking an Assessment  
* Time gaps between viewing a Clip, Activity, or Game and taking an Assessment 
* Length of each session

<h1 class="h4">Closing</h1> 
Check out this <a href="{{ page.codeexamples }}" target="_blank"> Jupyter notebook</a> for ideas about wrangling and visualizing using Python, Pandas, and Seaborn.

Happy Exploring!





