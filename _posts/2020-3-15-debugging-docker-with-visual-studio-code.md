---
layout: post
title: Setup Visual Studio Code to Debug an Application in Docker
summary: Steps to enable debugging for a Python-Django-Postgres website running in Docker on localhost
date: 2020-3-15 00:50:00   
categories: [Development, Docker, Python]
mainimageurl: "/img/debugger2.png"
mainimagealt: "Debugger"
mainimageattribution: "Visual Studio Code Debugger"
---

<h1 class="h4">Introduction</h1>
<p>
For a while now, I have been wanting to contribute to an open source project so that I could get more experience with Django and Python.  I finally found an opportunity and was excited to see that I would also have the opportunity to use Docker for the first time.  The  project had very detailed directions and I was able to run the site and access it in my browser in no time.  Then I started thinking about debugging and how I could set breakpoints to become more familiar with the code.  The developer instructions explained how to use The Python Debugger (pdb), which is a command line debugger.  I have never used a command line debugger before, and it seemed like a steep learning curve.  Because I was already learning several other technologies with this project, I decided to try to use Visual Studio Code to debug since it has a GUI debugger and supports debugging Docker containers. 
 
</p>

<h1 class="h4">Details</h1>
* Got existing source code from Github
  * Sass, Python, Django, Postgres database
  * Docker, with a docker-compose.yml with three services: front end, application, and database
  * The application was set to run on localhost on one port (8000)
* Was able to use docker-command at the command line to manually build the container, run the application, and add test data
* Worked on this during March 2020, with Visual Studio Code version 1.43.0, on macOS Mojave

<h1 class="h4">How Visual Studio Code can help with the development process</h1>
Visual Studio Code can: 
* Build the Docker container and start the application, as specified by the docker-compose.yml 
* Attach to the source code in the container (to allow code edits)
* Debug services in the container (on a port different from 8000, which is where the application was running)

<h1 class="h4">Overview of files to add in Visual Studio Code</h1>
* <b>docker-compose.override.yml</b> file so Visual Studio Code can run the application on a second port (3000) for debugging
  * This approach keeps the open source repo from being altered and gives me the freedom to work how I want to work, regardless of the preferences of the other contributors  
* <b>devcontainer.json</b> file so Visual Studio Code knows which docker-compose files to use and which extensions to install on the container
  * The two docker-compose files are 1) the original one from the open source repo and 2) the override added after cloning 
  * The container needs the "ms-python.python" extension 
  * Again, modifying the container with devcontainer.json gives me the freedom to work with Visual Studio Code instead of forcing everyone else to do the same
* <b>launch.json</b> file to specify the debug configuration so that Visual Studio Code knows what actions to take when debugging starts

The following instructions assume:
* Familiarity with Visual Studio Code:
  * An understanding of workspaces (a .code-workspace file) and the Command Palette
  * How to install extensions, and that these two extensions are installed on your local machine: Docker extension ("ms-azuretools.vscode-docker") and the Microsoft Python extension "ms-python.python" 
  * How to set the Python interpreter
  * How to debug Python by adding a debug configuration
* The source code is on your local machine, with a .code-workspace file pointing to it 
* The workspace is open on your local machine

<h1 class="h4">Add devcontainer.json using the Command Palette</h1>  
* In the Command Palette, start typing 'devcontainer' to find the command and you should see an option "Add Development Container Configuration Files"
* Click the option and then select 'docker-compose.yml' so a default file can be created  
* Verify on disk the devcontainer.json file is located in .devcontainer 
  * Create .devcontainer if needed and move the .json file there.
* If docker-compose.yml was added to .devcontainer, delete it. 
* Adjust the devcontainer.json file to make the service name match the service name in the docker-compose file and specify the extension to install: 
<pre class="ml-5">
<code class="language-Python">
...
"service": "app",
"extensions": ["ms-python.python"]
...
</code>
</pre>

<h1 class="h4">Add docker-compose.override.yml to .devcontainer and make devcontainer.json aware of it</h1> 
* Manually add a new docker-compose.override.yml file to .devcontainer (so that now it has two files, the .json file and the .yml file).  The .yml file needs to specify the debug port for the application: 
<pre class="ml-5">
<code class="language-Python">
app:
  ports:
    - "3000:3000"
</code>
</pre>
(Again, "app" is specified in the original docker-compose.)
* Edit devcontainer.json so that it is aware of the overridden docker-compose file.  Be sure to list the original docker-compose first.  The path to the original depends on how the original code is structured, but Visual Studio Code should have been able to figure that out when it created devcontainer.json.
<pre class="ml-5">
<code class="language-Python">
"dockerComposeFile":[
		"../your-project-directory-here/docker-compose.yml",
		"docker-compose.override.yml"
 ],
</code>
</pre>

The next steps explain how to build and start the Docker container and attach Visual Studio Code to container to access the source code and application running inside the container. 

<h1 class="h4">Using devcontainer.json to launch the Docker container</h1>  
* Command Palette - Remote-Containers: Open container configuration file
* See notification in the lower right hand corner of Visual Studio Code and click the button "Reopen in Container"
* Watch the lower right for the notification about installing Dev Container
* Note in the lower left-hand corner, there is a green area showing the connection to the container
* After everything finishes, Visual Studio Code's Terminal tab will be active and will give you access to the container.  Try different commands, such as: 
  * To find the Linux version: <code>uname -a</code> 
* Verify that the Python extension is installed in the container by checking the Extensions view

<h1 class="h4">Attach Visual Studio Code to the running container</h1> 
From the Docker extension (the whale icon), find the running application/service:  
* Right-click the application/service and choose "Attach Visual Studio Code" which will launch a new window 
* Verify in the lower left hand corner of the new window, there is a green area showing name of the connected container  
* Select a Python interpreter if you get a notification about “No Python interpreter is selected.”  You will see that the only choices are Python versions installed on <b>container</b> 
* Visual Studio Code's Terminal will be active to run additional commands if needed, such as running migrations or loading test data
  * <code>python manage.py migrate</code>
  * <code>python manage.py loaddata ...</code>
* Verify the app is running by browsing to http://localhost:8000
  
<h1 class="h4">Create the debug configuration</h1> 
Within the Debug view in Visual Studio Code:
* Click the “create a launch.json file” 
* Select Django 
* Verify the resulting file has “django” set to true   
* Change the "name" if desired
* Be sure the "args" specify the debug port (3000)

The file should be similar to: 
<pre class="ml-4">
<code class="language-Python">
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
</pre>

<h1 class="h4">Start debugging</h1> 
Set a breakpoint in a .py file.  Back in the Debug view, select the newly created configuration and click the green arrow to start debugging.  Alternatively, press F5 to start the debugger.  In your favorite browser, browse to http://localhost:3000 and start clicking around to fire the code marked with the breakpoint.   

<h1 class="h4">Conclusion</h1> 
It took some time to figure out how to get this working, but I think it will help me in the long run.  My biggest challenges were:
* Understanding how Visual Studio Code interacts with containers - that it can help launch the container and then provide access to the code in the container and access the service running in the container
* Getting the debugger to launch the app on a second port without changing the docker-compose.yml file from the open source repo

These links were very helpful during my adventure in March 2020:
* <a href="https://docs.docker.com/compose/extends/#multiple-compose-files" target="_blank">Multiple Docker Compose Files</a>
* <a href="https://code.visualstudio.com/docs/remote/containers#_attaching-to-running-containers" target="_blank">Attaching to Running Containers with Visual Studio Code</a>
* <a href="https://www.youtube.com/watch?v=eUitxqLxICo" target="_blank">Building Python Web Applications with Visual Studio Code Docker and Azure</a> (especially starting at the 24-minute mark)

Happy debugging!
    




