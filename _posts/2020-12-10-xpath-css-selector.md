---
layout: post
title: Getting elements in Webdriver using both XPath and CSS Selector 
date: 2020-12-09 13:14
tags: ["development", "testing"]
summary:
---

Writing a test to randomly click on any link on my webpage and all entries are wrapped within a particular CSS class named 'button white'.

There are many ways to select element in WebDriver and I have tried both XPath and CSS Selector..

### Xpath
I am using the code below in getting an array of elements with this particular class name. Notice of the use of "$$" which means retrieving all elements with this class name. If I only use $, it will only return the first one in the array.

`const elem = $$('//a[@class="button white"]')`

### CSS Selector
Similarly, I can use CSS Selector in getting the same array, the code is as follows,

`const elem = $$('a.button.white')`

No matter which approach to use, I can then get the "href" from a particular index through

`elem[0].getAttribute("href")`

Next, I would just determine the size of the array with `elem.length` and pick a random integer within the range.