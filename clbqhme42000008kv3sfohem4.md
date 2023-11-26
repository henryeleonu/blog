---
title: "Code Generation Using ChatGPT: Optimizing Language Models for Dialogue"
datePublished: Fri Dec 16 2022 12:29:30 GMT+0000 (Coordinated Universal Time)
cuid: clbqhme42000008kv3sfohem4
slug: code-generation-using-chatgpt-optimizing-language-models-for-dialogue
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1671833181440/94ac891e-2792-4316-b70e-9eda52c9642a.png
tags: machine-learning, chatbot, natural-language-processing, chatgpt, automated-code-generation

---

OpenAI has released a trained model called ChatGPT that can interact conversationally. I am particularly interested in how it generates code. In this post, I will be writing about my interactions with ChatGPT and some of my observations.

# My Interactions with ChatGPT

**I asked this question:**

How can I scrape a table from a website in python?

**I got this response from ChatGPT:**

To scrape a table from a website in Python, you will need to use a library called Beautiful Soup. Beautiful Soup is a popular Python library for extracting data from HTML and XML files. It provides simple, idiomatic ways of navigating, searching, and modifying the parse tree.

Here is an example of how you can use Beautiful Soup to scrape a table from a website:

%[https://gist.github.com/henryeleonu/c398d95b3eabb64b7f28d891a4d44952] 

This code will make a request to the specified URL, parse the HTML content of the page, find the table element in the HTML, and then loop through the rows and cells of the table, extracting the text from each cell and printing it to the console.

You can also use other libraries such as Selenium or Pandas to scrape tables from websites. Selenium is a tool for controlling a web browser through code, which can be useful if the table you want to scrape is generated dynamically by JavaScript. Pandas has a function called `read_html()` which can be used to automatically parse tables from an HTML page and return them as a list of DataFrame objects.

I hope this helps! Let me know if you have any questions.

**I asked the same question a second time and I got a different response, this time it gave the steps without writing any code.**

**This is the response I got:**

There are a few ways to scrape a table from a website in Python:

1.  Using the BeautifulSoup library:
    

*   First, install the BeautifulSoup library using pip install beautifulsoup4
    
*   Then, use the requests library to send a GET request to the website and retrieve the HTML content
    
*   Parse the HTML content using BeautifulSoup and find the table element
    
*   Extract the rows and columns from the table and store the data in a list or a dictionary
    

2.  Using the Selenium library:
    

*   First, install the Selenium library using pip install selenium
    
*   Then, use Selenium to open the website and retrieve the HTML content
    
*   Parse the HTML content and find the table element
    
*   Extract the rows and columns from the table and store the data in a list or a dictionary
    

3.  Using the pandas library:
    

*   First, install the pandas library using pip install pandas
    
*   Then, use the [pandas.read](http://pandas.read)\_html() function to extract the tables from the website
    
*   The function will return a list of DataFrame objects, which can be accessed and manipulated as needed.
    

**I then asked a this more specific question**

How can I write a python code to scrape a table from the website, [https://en.wikipedia.org/wiki/List\_of\_airlines\_of\_the\_United\_Kingdom](https://en.wikipedia.org/wiki/List_of_airlines_of_the_United_Kingdom)?

**This is the response from ChatGPT:**

Here is a sample code that demonstrates how you can scrape the table from the website using Python's Beautiful Soup library:

%[https://gist.github.com/henryeleonu/7d3f86733328e27cc6a56123d97459b4] 

This code will print out the contents of the first three columns of the table, which contain the name, IATA code, and ICAO code of the airlines. You can modify the code to extract other information from the table, such as the type of airline or the country of origin.

# My Observations

From my interactions, I can say that ChatGPT is impressive, especially from the way it makes the interaction feel natural and how detailed the responses it gives. But in terms of code generation, I will say that the code is more of a template that needs to be customized to meet your needs. The code generated is not guaranteed to run without errors, as the above code all have errors on running them. Generally speaking, the code generation aspect might be beneficial at the initial stage of a project especially to a beginner programmer to know the step to take to solve a problem.