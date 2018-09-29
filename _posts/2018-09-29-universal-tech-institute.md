---
layout: post
title:  "Chrome Extension Developer Intern - From Menial to Meaningful"
date:   2018-09-29 22:15:00
author: Mitchell Sotto
categories: chrome-extensions
---
I was hired as a "web developer" intern at Universal Technical Institute (UTI), only to find out that "web developer" did not mean what I thought it meant. My coworker and I were tasked to help the QA team compare an old and a new version of the same course to make sure the text was the same...for the whole summer...needless to say I was slightly disappointed; however, the second day in, my coworker and I mentioned to our boss that we could probably automate most of the work for the project we were put on, and that's when the fun began. 

#### The Bookmarklet

To start, we created a bookmarklet (an application in a Chrome bookmark) that helped to set up the QA environemnt.

 The bookmarklet dropped the setup before course comparison from 3-5 minutes to 17 seconds. Instead of 30 minutes of setup time for 8 courses every day, it now only took 2-3 minutes. Add the 800 courses that were in the backlog to this calculation, and our simple bookmarklet saved UTI 2700 minutes, or 45 hours in work setup time.

#### The Chrome Extension V1
After our success with the bookmarklet, we turned our attention to automating the comparison of text between course pages.

As interns, we had no authority to add a backend system that could compare two different webpages' content, so we had to find a way to have two browser tabs communicate with each other; the answer? Chrome Extensions.

Using an external API for optical character recognition (OCR), we automated the comparison of 90 percent of the text on each page. What used to take 45 seconds per page now only took 12 seconds. Multiply this by 15 pages per course, and 800 courses in the backlog, and our OCR comparison saved UTI approximately 6600 minutes, or 110 hours of text comparison work. There was also a noticable improvement in job satisfaction for our QA coworkers because they didn't have to strain their eyes doing monotonous work for nearly as long each day. They enjoyed using the tool to do their work.

#### The Chrome Extension V2
While comparing the text from the old Flash courses to the new HTML5 courses, my coworker and I found out that somebody was manually typing out all of the text from the Flash courses to use in the HTML5 courses. That's why there was such a big need for the QA team to do text comparison and spell checking in the first place--to account for the human errors in typing. They told us there was no way to scrape a Flash object for text (which is true), but after doing some research we found out that the the Flash courses making an HTTP request for XML documents that held all the text. 

For the last few weeks of our internship, we outfitted our chrome extension to intercept the XML sheets that were populating the bulk of the text in the courses and to insert the intercepted text into an online editor we built with the CodeMirror library. This allowed the creators of the new HTML5 courses to copy the text they needed instead of hand typing it.