---
layout: post
title: So much to read, so little time
summary: Using natural language processing to find concepts and themes in National Science Foundation awards
date: 2020-07-05  
categories: [Python, NLP, NLTK, nGrams, LSA]
mainimageurl: "/img/books.jpg"
mainimagealt: "Books on shelf"
mainimageattribution: "Photo by Element5 Digital from Pexels"
codeexamples: "https://github.com/h-fuzzy-logic/Python-Finding-NSF-Award-Themes/blob/trunk/NSF%20Awards%20NLP%20Analysis.ipynb"
---

<h1 class="h4">Introduction</h1>
Natural language processing (NLP) can help make sense of large volumes of data, when there is too much data for a person to read.  This post focuses on making sense of textual award data from the National Science Foundation.  
 
<h1 class="h4">Reason for analysis</h1>
Writing a proposal for an NSF award can be time consuming and the review process can seem mysterious.  To increase the chances of writing a winning proposal, natural language processing can uncover which phrases and topics have received funding.   It is also possible to determine if larger award amounts tend to be associated with certain words, phrases, and topics.  With this goal in mind, below are some insights about the NSF awards from 2019.  

<h1 class="h4">Data details</h1>
The National Science Foundation has its award data from 1966 - 2019 available for <a href="https://www.nsf.gov/awardsearch/download.jsp" target="_blank">download</a>.  The files are in XML format and contain information about each award such as title, abstract, dollar amount, and information about the institution receiving the award.  The XML was transformed to a CSV file for analysis.  These award summaries are written by NSF staff and are publicly available, but the submitted proposals are confidential.    

<h1 class="h4">NSF organizational structure and the impact on the analysis</h1>
Awards are granted by Directorate and some examples of Directorates are:  Biological Sciences; Computer and Information Science and Engineering; Mathematical and Physical Sciences.  The <a href="https://www.nsf.gov/about/research_areas.jsp" target="_blank">full list</a> is publicly available.  Due to the structure created by having Directorates, this analysis will be done at the Directorate level.   

<h1 class="h4">General considerations when analyzing text data</h1>
<ul>
	<li> Understand the source of the text and how it was collected.</li>
	<li> Spend time just looking at the raw data before loading it into your tools.</li>
	<li> Be mindful that most text has punctuation and undesirable characters such as brackets, commas, parenthesis that need to be removed before analysis. </li>
</ul>

<h1 class="h4">NLP techniques used</h1>
Common words, bigrams (phrases with two words), and trigrams (phrases with three words) are uncovered by splitting the abstract title and abstract text into words (tokenizing) and counting the occurrences.  Additionally, topics are uncovered using Latent Semantic Analysis (LSA).  This analysis uses the <a href="https://www.nltk.org/" target="_blank">Natural Language Toolkit</a> for nGram processing, <a href="https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.TruncatedSVD.html" target="_blank">scikit-learn's TruncatedSVD transformer</a> to uncover concepts and topics, and the full code is available in this <a href="{{ page.codeexamples }}" target="_blank"> Jupyter notebook</a>.  The notebook contains more details about decisions made during the analysis.  The conclusion of this blog post has additional resources to explain the techniques used.  

<h1 class="h4">Description of analysis</h1>
I decided to deep dive into the Directorate Direct For Computer & Information Science & Engineering since my background is in computer science.  The mean Award Amount was calculated and the awards were divided into two groups by Award Amount: above average and below average.  For the two groups, the top twenty-five individual words, bigrams, and trigrams were determined for the Award Title and Award Abstract.  Additionally, the top 5 topics were uncovered for each group.

<h1 class="h4">Results of analysis</h1>
Overall, the word/phrase occurrences between the above average and below average group are very similar and <a href="{{ site.baseurl }}/img/NSF-comparison.png" target="_blank">this image</a> shows the similarities.  The most common word in the Abstracts in both groups is **data**.  The word **collaborative** appears often in the titles, and I am surprised to see it so often because computer-and-math-types have the reputation for being introverted and preferring to working alone.  Acronyms (such as **satc**, **satc**, **shf**, **sch**, and **cns**) appear often in the titles and I had to do some googling to figure out that the acronyms indicate the Division within the Directorate.   For example, **CNS** stands for Division of Computer and Network Systems.  The Abstract bigrams and trigrams seem to show the benefits of the Award with phrases like: **intellectual merit**, **broader impacts**, **nsf statutory mission**.

Seeing the most common word occurrences this way, I am not able to understand the common technical topics in the Awards.  Next, I try topic modeling to uncover the five concepts and their associated topics.  Note that I assigned a concept title after interpreting the topics.

These are the concepts for the above average Award Amounts:
1. **Teaching data science**: data, science, learning, systems, data science, new, students, algorithms, software, models
1. **Data science plus materials science**: materials, data science, data, mechanical, science, alloys, mechanical properties, composites, properties, interpretable
1. **Fluid flows**: fluid, ibamr, multiphase, flows, fluid structure, manufacturing, energy, advanced, models, biological systems
1. **High performance computing**: parallel, pabb, mpi, programming models, programming, compiler, runtime, productivity, parallel programming, global
1. **Data science plus fluid flows**: data, data science, science, fluid, ibamr, multiphase, hub, hubs, fluid structure, flows

These are the concepts for the below average Award Amounts: 
1. **Teaching data science**: data, science, learning, students, new, systems, algorithms, machine, data science, computing
1. **Data science at colleges**: data science, data, science, holyoke, directorate, division, colleges, organizations, data revolution, revolution
1. **Identifying risks**: risk, prism, materials, risks, hdr, critical risk, cris, systemic risk, data, systemic
1. **Epidemiology and public health**: epidemiology, infectious, disease, computational, public health, response, concerns constraints, msml, msml networks, novel implementations
1. **Identifying risks, involving students**: risk, prism, risks, conference, critical risk, systemic risk, cris, systemic, indicators, students
   
To decide on some of the concept titles, I had to check the data file and do some googling to get more information:
* Holyoke is a city in Massachusetts, USA.  
* The word prism refers to 1)  “Predictive Risk Investigation SysteM” and 2) the geometric figure

<h1 class="h4">Ideas for further investigation</h1>
Thinking about how to provide useful information to those applying for an Award, this analysis prompted more questions:
* Does adding stopwords such as **statutory**, **mission**, and **intellectual** make the Abstract nGram analysis more helpful? 
* How do the Awards vary by Directorate?  Can text analysis be used to decide which Directorate to target? 
* How do the results change when calculating the average of Initial Award Amount and Award Amount?
* Do the topics become more distinct depending on the Award Type (Standard Grant vs Continuing Grant)? 
* What is going on in Holyoke, MA that has made it so prominent in NSF Awards in 2019? 
* Can text analysis uncover trends over time, perhaps finding the trending concepts in 2019? 

<h1 class="h4">Conclusion</h1> 
Check out this <a href="{{ page.codeexamples }}" target="_blank"> Jupyter notebook</a> for the code. These resources were espeicially helpful to me:
* <a href="https://www.youtube.com/watch?v=BJ0MnawUpaU" target="_blank">Mike Bernico's explanation of LSA</a>
* <a href="https://github.com/bendgame/kmeansChardonnay" target="_blank">Eric Kleppen's code to use NLP and k-means clustering for reviews</a>






