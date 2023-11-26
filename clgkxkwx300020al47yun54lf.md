---
title: "How To Encourage Best Practices in Python Programming By Complying With PEP8 Style Guide"
seoTitle: "Enable PEP8 compliance in Visual Studio Code for python code"
datePublished: Mon Apr 17 2023 14:28:10 GMT+0000 (Coordinated Universal Time)
cuid: clgkxkwx300020al47yun54lf
slug: how-to-encourage-best-practices-in-python-programming-by-complying-with-pep8-style-guide
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1681741672672/831fd66d-2559-4fdc-807f-d43d6a33373e.png
tags: python, vscode, php8, vscode-extensions, type-checking

---

As part of this blog post, I have added a YouTube demo on how to enable PEP8 compliance in Visual Studio Code.

[Enabling PEP8 Compatibility of Python Code in Visual Studio Code - YouTube](https://www.youtube.com/watch?v=ZkwHwQ6l4wI)

%[https://www.youtube.com/watch?v=ZkwHwQ6l4wI] 

Some of the best practices in Python programming are:

1. Comply with PEP8 conventions.
    
2. Enforce data type checking.
    
3. Autogenerate docstring
    
4. Install autopep8 for code formatting.
    

# Complying With PEP8 Conventions

The key benefit of following best practices and conventions in Python programming is to improve the readability and consistency of code. The readability of code is very important because code is read much more than it is written. The readability of code cannot be over emphasized because it helps to improve the maintainability of code. Following the standards in PEP8 will go a long way in improving the quality of the code we write. PEP8 convention provides a style guide for writing consistent and readable Python code and I will show you how to enforce or encourage PEP8 conventions in Visual Studio Code. The first step is to install PEP8 which has the Python coding standards such as variable naming style, module docstring, function docstring, and inconsistent indentation.

The first step is to Install PEP8 by running the following command:

`$ pip install pep8`

The next step: To enforce the PEP8 standard, we will install Pylint in Visual Studio Code. Pylint is the tool that checks whether our code complies with the PEP8 standard and returns errors where we fail to comply. Install Pylint The easiest way to install Pylint is to go to the extension tab in Visual Studio Code, search for Pylint and then install it.  
Another way to install Pylint is to run the following code on the terminal:

`$ pip install pylint`

Then Pylint needs to be enabled on VSCode by following these steps:

1. Press "Ctrl + Shift + P" to get Command Palette
    
2. Type "Lint"
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681740639833/286d5a8a-dbf9-47b0-b62a-12c280337783.png align="center")

1. Select "Python : Enable/Disable Linting", and click on "Enable"
    
2. Repeat Steps 1 & 2, now select "Python : Select Linter", Select pylint from options
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681740958155/b26ca261-5da8-4072-95cd-3cdd6de3b484.png align="center")

Note: apart from highlighting stylistic problems, Pylint highlights syntactical errors in your code.

# Enable Type Checking

You might also enable type checking in VScode by going to settings, typing “type checking” and changing type checking mode to either basic or strict. This will highlight function parameters without data type specified.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1681741183839/a9118f47-24d2-488d-8303-1adf3634c05e.png align="center")

# Autogenerate docstring

For a large project, writing docstring could be cumbersome, so I use autoDocstring to automatically generate docstring for modules and functions. To install autoDocstring, go to an extension on VsCode, type autoDocstring and then install it. To generate a docstring, Cursor must be at the line where you want your docstring to start, right click and then click “Generate Docstring”. You must write your function first before you can generate a docstring for it.

# Install autopep8 Formatter Extension for VScode

autopep8 automatically formats Python code to conform to the PEP8 style guide. Install autopep8 formatter from extensions in Vscode.