---
layout: post
title: Building intuition to engineer features for user generated events 
summary: Lessons learned from participating in Kaggle’s 2019 Data Science Bowl
date: 2020-4-18 00:50:00   
categories: [EDA, User Events]
mainimageurl: "/img/neon-party.jpg"
mainimagealt: "Crowded neon party"
mainimageattribution: "Photo by Marcin Dampc from Pexels"
---

<h1 class="h4">Introduction</h1>
Event data is often created as users navigate from screen to screen while using websites and other software.  Engineering features for this type of data can be tricky. There can be lots of data and it may first seem unpredictable and hard to wrangle, just like the swarm of people pictured above at a neon party. Even finding publicly available user generated event data to explore can be hard, but Kaggle’s 2019 Data Science Bowl offers a wonderful opportunity to practice wrangling this type of data. The goal of the competition is to determine how different media types can improve performance on in-game assessments.  
       
<h1 class="h4">Data Details</h1>
The competition data is anonymous gameplay data from kids using the PBS Kids Measure Up! app and is organized by installation and session.  The events are logged in sequence during gameplay which results in an overwhelming amount of detailed data. Avoiding out of memory errors and performance issues while doing exploratory data analysis and running models is just as challenging as grasping the paths of typical users. To make getting started less overwhelming, there are several ideas below with specific examples related to the competition.  

<h1 class="h4">Tips for making sense of the data</h1>
1. Try to truly understand the data and how each logged event corresponds to gameplay
* For the competition, I could play the MeasureUp! app and have the same experience as a user.
1. Read any available documentation 
* Kaggle Discussion had an article called <a href="https://www.kaggle.com/c/data-science-bowl-2019/discussion/115034" target="_blank">Measure Up! media types introduction</a>  which explained the different media types (Clip, Activity, Game, or Assessment). 
1. Get a clear understanding of the allowable paths through the system
* Is the user forced to take ordered steps or can media/screens be accessed in a haphazard way? 

<h1 class="h4">Exploratory data analysis to build intuition</h1>  
Chapter 6 of the book <i>Doing Data Science: Straight Talk from the Frontline</i> has useful advice about 
exploring the data from from a single user’s point of view.  This can be done in a variety of ways, including plotting the data over time to compare different users.   After creating the visuals, it is important to create a narrative about the plots to explain each user’s approach to playing the game.  For the competition, an example is plotting the media types accessed by users on a timeline and then comparing the paths based on assessment outcomes.  

<h1 class="h4">Feature engineering</h1> 
EDA can help determine which variables correlate to having a positive assessment outcome, such as:
* Viewing clips, activities, or games prior to taking an assessment  
* Time gaps between viewing a clip, activity, or game and taking an assessment 
* Time of day of gameplay
* Length of each session

Happy Exploring!





