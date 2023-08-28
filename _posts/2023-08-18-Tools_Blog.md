---
toc: true
comments: true
layout: post
title: Tools Blog
description: Why I Love My Tools
type: plans
courses: { csse: {week: 1}, csp: {week: 1, categories: [4.A]}, csa: {week: 0} }
categories: [C1.4]
---
# Why I Love My Tools

I love my laptop because it allows for me to work on my AP Computer Science A projects without any worries. I love Github because it allows me to display my code to the whole wide world and save my work to the Cloud. I love Visual Studio Code because it allows me to display my blog when other methods of doing so don't work. I love Github Pages because it can display my blog for everyone to see most of the time. I love Jupyter Notebooks because they allow me to run machine learning models on large datasets in a very convenient manner. In addition, I can also run segments of Java, Javascript, and Python and demonstrate the usefulness of these languages in Jupyter Notebooks. I love Slack because it allows me to work, collaborate, and transfer ideas with my teammates in a very efficient manner (at least compared to Discord). I love Docker because it allows me to test and deploy any of my applications. In addition, I love Docker because it allows me to test deployment scripts on their local machines. I love Conda because it allows me to avoid dependencies and run data science projects in a very fast manner. I love Homebrew because it allows me to install tools in a very efficient and centralized manner. Lastly, I love AWS because it has deployed many of my previous projects in AP Computer Science Principles.

> ## VSCode and Github Pages Setup Hacks
>>Take note and describe the type of shell commands that you are using through Terminal in this installation procedure.
- wsl - This command is used to interact with the Windows Subsystem for Linux (WSL), which allows you to run a Linux distribution alongside your Windows system.
- cd - The `cd` command stands for "change directory." It's used to navigate between different directories (folders) in the file system. For example, `cd myfolder` would take you to the "myfolder" directory.
- git -  Git is a version control system used to track changes in your code. Commands like `git clone`, `git pull`, and `git push` are used to manage and synchronize your codebase with a remote repository.
- apt -  This command is specific to Debian-based Linux distributions like Ubuntu. It's used to manage software packages. For instance, `sudo apt update` refreshes the package list, and `sudo apt install` is used to install new software packages.
- mkdir - Creates directories
- ls - Lists files and directories within a directory
- rm - Used to remove files

>>In the Development process, developers use Version control. Annotate in notes what you have learned about Version Control while doing this setup process.

>>>>Where are the files from GitHub placed on your local machine. How do you navigate to those files?
- The files from GitHub the local machine are inside the directory that was specified when `git clone` was used. It can also be inside the directory that the user was in when `git clone` was run. The `cd` command can be used to navigate to the directory containing those specific files.

>>>>Where are the files placed in the GitHub Cloud, how do you navigate to those files?
- You can navigate to these files on GitHub by visiting the repository's URL. These files are on the GitHub Cloud Servers, and whenever local changes are pushed, the changes are uploaded to this location.

>>>>How would you update your Fork of student repository if teacher wanted you to pick up an update?
- There are multiple ways. The coding way is to add the original as a remote "upstream", and fetch the changes. After this, return to your local main branch and merge the changes - if there are merge conflicts, you must resolve. Another way is to find the changes in the original repo and manually copy and paste into your repo.

>>Put into words the difference between viewing GitHub Pages running on localhost machine versus running on a deployed server.

>>>>What is the localhost URL for your distribution? Can anyone else see it?
- The URL for my localhost is [http://localhost:4000/](http://localhost:4000/), and no one but me can see it. This is because I am running the website locally on my computer, which allows me to see my website before it is deployed to a live server.

>>>>What is the GitHub Pages URL for your distribution? Can anyone else see it?
- The GitHub Pages URL for me is [https://taykimmy.github.io/CSA_Repo/](https://raunak2007.github.io/csa-pages/), and is available to anyone with internet access. This is because GitHub pages are publicly accessible and are published to the internet when I deploy it.
