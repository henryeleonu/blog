---
title: "How to Install Multiple Versions of Python Using Virtualenv"
datePublished: Thu Dec 15 2022 09:11:12 GMT+0000 (Coordinated Universal Time)
cuid: clbov3ioq000008l99f9s0zjb
slug: how-to-install-multiple-versions-of-python-using-virtualenv
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1671833648682/fb2891d6-569a-4765-a840-2146cd21092c.jpeg
tags: python, virtualenv, virtual-environment

---

**Click this line to watch:** [how to install multiple versions of python using virtualenv - YouTube](https://www.youtube.com/watch?v=sk-ikK90AyQ)

There are situations when we need to have multiple versions of python, for instance, when we need to install dependencies that are not compatible with the python version we are running. I have run into a situation where a dependency I need to install is only compatible with previous versions of python. To solve this problem, I had to run the previous version of python in a virtual environment. I use virtualenv utility, which enabled me to run multiple versions of python. I will be explaining some of the steps I followed to get things running.

1.  Install virtualenv  
    pip install virtualenv
    
2.  Download the desired version of python  
    I already had my main python installed in this path: C:\\Python\\Python311\\  
    I install the previous version of python here: C:\\Python\\Python310\\
    
3.  Create a project directory  
    I created a project directory here: C:\\Python\_Workspace\\my\_project\\
    
4.  Create a virtual environment in your project directory  
    Open the terminal and change directory to project directory  
    cd C:\\Python\_Workspace\\my\_project\\  
    Create your virtual environment  
    python -m virtualenv -p C:\\Python\\Python310\\python.exe my-virtual-env
    
5.  Activate virtual environment  
    .\\my-virtual-env\\Scripts\\activate
    
6.  To deactivate the virtual environment, run  
    deactivate
    
7.  We can now go ahead to install all the dependencies we need.
    
8.  To create a requirements.txt file of all dependencies in the virtual environment, run:  
    pip freeze &gt; requirements.txt