---
layout: post
title: Key Features of Visual Studio Code
summary: Tips to make the most of Visual Studio Code   
categories: [Development, IDE]
mainimageurl: "/img/python-large.png"
mainimagealt: "Python logo"
mainimageattribution: "Image from Python Software Foundation"
---

<h1 class="h4">Extremely Extensible</h1>
Have the mindset that an extensions are often required.  Wanting to develop with Python?  You'll need an extension for that.  Wanting to work with Docker?  You'll need an extension for that.  

<h1 class="h4">Workspaces<h1>
Workspaces are important and it is a good idea to create a workspace (via a file with a .code-workspace extension) to reference your project folders and files.  The workspace file can be checked into source control or can be left out of source control, depending on your needs and your team agreements.  It does not have to be located with all of the other project files.   Opening a workspace file in Visual Studio Code will open all the associated files and folders in the Explorer.

 <h1 class="h4">Enable / Activate Features<h1> 
 In some cases, an actual code file, such as a Python (.py) file, needs to be open to enable certain features.  For example, if you have just cloned a repo and it seems like you can't "do" anything, try opening a code file to see if more features are activated.  

<h1 class="h4">Command Palette<h1> 
 The Command Palette allows you to search for and execute commands in an interactive way.  It can be activated by choosing View | Command Palette or using keyboard shortcut keys.  Each install has default shortcut keys which can be customized.  Command Palette normally launches with a > as the first input.  If the > is deleted, other options are available.  Depending on the command selected, the Command Palette may prompt for additional information, so use Enter or Esc as needed.  

 After commands complete, there are often notifications at the bottom right to explain next problems or possible next steps.  If the notification disappears before you can read it, click the blue information icon in the lower right hand corner to see it again. 

 <h1 class="h4">Customizations with .json Files<h1> 
 Visual Studio code relies on .json files to customize development tasks and settings.  As examples, launch.json is used to specify debug settings; devcontainer.json is used to customize Docker settings; and settings.json is used to customize other development settings.  

Happy Coding!
    




