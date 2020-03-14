---
layout: post
title: Modern Web Development with Containers
summary: Using containers for localhost development requires a different mindset than traditional development 
date: 2020-3-14 00:30:00  
categories: [Development, Containers]
mainimageurl: "/img/containers.jpg"
mainimagealt: "containers"
mainimageattribution: "Photo by Ella Olsson from Pexels"
---

<h1 class="h4">Introduction</h1>
<p>
I have many years of experience as a software engineer doing traditional “localhost” web development.    Each time a developer joins the team or gets a new machine, I know how much time is wasted setting up a new local environment - installing dependencies, creating and connecting to databases, trying to figure out good test data and test accounts, making sure the local machine has all the right directories, paths, etc.  I know the frustration of not being able to recreate a production bug on my local machine because my local environment is different from production.  I know the “it works on my machine” mentality.  I take my chances that my local machine will behave the same as the actual development, staging, or production servers.
</p>

<p>
When I do “localhost” web development with Visual Studio, I normally press “F5” and wait for a moment while IIS Express fires up.  After it launches, a new browser window opens and I’m ready to start debugging or writing new code.  If I need to query data in the database, my database tools can connect to the database on my machine.  Everything I need is on my machine. 
</p>

<h1 class="h4">Containers to the rescue</h1>
<p>
Containers, which are isolated units that contain everything an application needs to run, can let applications run reliably from one environment (i.e., developer machine) to the next.   A popular container option, Docker, offers a more detailed description with 
<a href="https://www.docker.com/resources/what-container" target="_blank">“What is a container?”</a>
</p>

<h1 class="h4">Considerations for localhost development with containers </h1>
<p class="ml-4">
<text class="font-weight-bold">I have to build and start the container, possibly for each development session.</text>
This process can be time consuming and repetitive.  I need to think about how it can be automated for maximum productivity.
</p>

<p class="ml-4">
<text class="font-weight-bold">I have to remember that commands can be run on my local machine and commands can be run on the container.</text>
How do I handle now interacting with <b>two</b> environments?  
</p>

<p class="ml-4">
<text class="font-weight-bold">I have to figure out how to do my normal development tasks (debug, write new code, query the database) in the context of the container.</text>
Can I keep my development tools on my local machine and "connect to" the source code in the container to debug and edit it?  Are there other options? 
</p>

<p class="ml-4">
<text class="font-weight-bold">I need to consider what happens to the container at the end of my development session.</text>
Do I need to preserve the container as is or is it beneficial to start from scratch with each development session?
</p>

<h1 class="h4">Summary</h1>
<p>
Even though using containers may seem more difficult at first, they can save time in the long run and boost your team's productivity.  And their flexiblity can most likely support your team's preferred process.      
</p> 




