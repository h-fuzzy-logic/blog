---
layout: post
title: Debugging a Docker Container with Visual Studio Code
summary: Steps to debug a Node-Python-Django-Postgres website running in Docker
date: 2020-3-14 00:50:00   
categories: [Development, Docker, Python]
mainimageurl: "/img/code.jpg"
mainimagealt: "Code"
mainimageattribution: "Photo by Markus Spiske from Pexels"
---

<h1 class="h4">Introduction</h1>
<p>
For a while now, I have been wanting to contribute to an open source project so that I could get more experience with Django and Python.  I finally found an opportunity and was excited to see that I would also have the opportunity to use Docker for the first time.  The  project had very detailed directions and I was able to run the site and access it in my browser in no time.  Then I started thinking about debugging and how I could set breakpoints to more quickly learn how the project worked.  The developer instructions explained how to use The Python Debugger (pdb), which is a command line debugger.  I have never used a command line debugger before, and it seemed like a steep learning curve.  Because I was already learning several other technologies with this project, I decided to see if I could use Visual Studio Code to debug since it has a GUI debugger and supports debugging Docker containers. 
 
</p>

<h1 class="h4">The details</h1>
* Got existing source code from Github
* Node front-end, Python, Django, Postgres database
* Docker, with a docker-compose with three services: application, database, and front end
* The application was set to run on port 8000
* March 2020, Visual Studio Code version 1.43.0, running on macOS Mojave
* Was able to follow the instructions in the repo and use docker-command to manually build the container, run the application, and add test data

<h1 class="h4">How Visual Studio Code can help</h1>
* Building the Docker container and running the application, as specified by the docker-compose.yml 
* Attaching to the code in the container (to allow code edits)
* Debugging on the container (on a port different from 8000, which is where the application was running)

<h1 class="h4">How Visual Studio Code requirements</h1>
* docker-compose.override.yml file to let the application run on a second port (3000)
  * This approach keeps the open source repo from being altered and gives me the freedom to work how I want to work, regardless of the preferences of the other contributors.  
* devcontainer.json file to specify the two docker-compose files to use plus any Visual Studio extensions to install on the container
  * The two docker-compose files are 1) the original one from the open source project and 2) the override yml I added
  * The container needs the "ms-python.python" extension and specifying it in the devcontainer.json file gives me the freedom to work with Visual Studio Code instead of forcing everyone else to do the same

<p> Note: The following instructions assume an understanding of 
* Visual Studio Code workspaces (aka a .code-workspace file), 
* the Command Palette and 
* Docker extension ("ms-azuretools.vscode-docker") is installed on your local machine. 
* Understand how to debug Python in VS (adding debug configuations)
* The code is on your local machine, and a workspace file pointing to it. 
</p>

<h1 class="h4">Creating devcontainer.json in the local repo</h1> 
To add one to your workspace using the Command Palette, 
* Start typing devcontainer and you should see an option to add one.  (Note: The actual command is “Add Development Container Configuration Files”)
* Click the add option and then select docker-compose.yml to get a default one.  
* Verify the devcontainer.json file is located in .devcontainer (Create .devcontainer if needed and move the .json file there.) 

The generated devcontainer.json file will probably need to be adjusted.  Be sure that the service name it matches the service name in the docker-compose file.  In my case, I needed to set the service name to "app" (since that was specified in the docker-compose) and include an extension:
<pre class="ml-4">
<code class="language-Python">
"service": "app",
"extensions": ["ms-python.python"]
</code>
</pre>

<h1 class="h4">Add docker-compose.override.yml to the local repo</h1> 
* Manually add a new docker-compose.override.yml file to .devcontainer (so that now it has two files, the .json file and the .yml file): 
<pre class="ml-4">
<code class="language-Python">
app:
  ports:
    - "3000:3000"
</code>
</pre>
Note: "app" is specified in the original docker-compose

At this point, you should be able to launch the Docker container and attach Visual Studio Code to it: 

<h1 class="h4">Using devcontainer.json to launch the Docker container</h1>  
* Command Palette - Remote-Containers: Open container cofiguration file
* See notification in the lower right hand corner of VS and click the button: Reopen in Container
* Watch the lower right for the notification about installing Dev Container
* Visual Studio Code's Terminal tab will be active and will give you access to the container 
  * Try different commands like <code>uname -a</code> to find the Linux version

<h1 class="h4">Attach Visual Studio Code to the running container</h1> 
In the Docker extension (the whale icon), find the running service.  Right-click and choose "Attach Visual Studio Code" which will launch a new window.  In the lower left hand corner, there should be a green area showing the connection to the container.  

NEW SECTION?  PRE-REQS? 

<h1 class="h4">Create debug configuration</h1> 
Verify the Python extension is installed in the container
If you get a notification about “No Python interpreter is selected” choose one via the Notification.  You will see that the only choices are python versions installed on container.  

Go to the Debug tab in VS.  Click the “create a launch.json file.” Select Django. The result is a default file with “django” set to true.   You can change the name if needed and save the file. 

<code>
{
    "version": "0.2.0",
    "configurations": [
        
        {
            "name": "Python: Django",
            "type": "python",
            "request": "launch",
            "program": "${workspaceFolder}/manage.py",
            "args": [
               "runserver",
               "0.0.0.0:3000",
               "--noreload"
            ],
            "django": true
        },
    ]
}
</code>


Happy debugging!
    




