---
layout: post
title:  "Chrome Extension Developer Intern - From Menial to Meaningful"
date:   2018-09-29 16:00:00
author: Mitchell Sotto
categories: Web-Scraping JavaScript
---
I was hired as a "web developer" intern at Universal Technical Institute (UTI), only to find out that "web developer" did not mean what I thought it meant. My coworker and I were tasked to help the QA team compare old Flash versions with new HTML5 versions of online automotive courses to make sure the text was the same...for the whole summer...needless to say I was slightly disappointed. After two days of manually comparing text, my coworker and I mentioned to our boss that we could probably automate most of the work we were doing, and that's when the fun began. 

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

The internship started out looking pretty dismal, but it transformed into one of my favorite development experiences in my career.

## Appendix

Below is the README for the extension that served as our help document for employees at UTI.



Quality Assurance Helper - Chrome Extension README
===========================================

Introduction
------------

The QA Helper is a tool designed to streamline the process of performing
1:1 Validations between the old and new UTI courseware by minimizing the
ill effects of some of the process\'s biggest pain points. This tool was
originally developed for supporting Content QA, but could be expanded in
the future to aid in other areas of need. The usage of its features are
the same, independent of the page that it is running on:

1.  A box with buttons will appear in the top-left corner of the page
2.  This box can be dragged around to any location on the screen that is
    convenient for the task at hand
3.  Buttons within the box can be clicked to invoke the help of the tool

Features by Page
----------------

### Blackboard

![qa helper](/assets/blackboard-ui.JPG)

1.  Jump to Web

    Clicking this button will present you with a dialog box containing
    two dropdown boxes and a button labeled \'Jump\'. Once all dropdowns
    are selected and the \"Jump\" button is pressed, a new slide and its
    corresponding old slide will pop up.

    ![qa helper](/assets/blackboard-ui1.JPG)

    1.  The Course Dropdown
        -   This dropdown box will contain a list of all the courses QA Helper has learned about (see NOTE below).

    2.  The Web Dropdown
        -   When a course is selected in the Course dropdown, this dropdown box will contain a list of all the webs in the selected course that QA Helper has learned about and can open for you.

    3.  The Jump button
        -   Click this button after you\'ve selected the appropriate course and web, and it will open the correct web for you in Blackboard and in the DR site! If QA Helper has not yet learned about a course, you cannot navigate to it in the dropdown menus.

    **NOTE**: To teach QA Helper about a new course, navigate to the
    course page in Blackboard that lists all the webs you\'d like to
    teach QA Helper about. As soon as any given course page has finished
    loading, you should notice that the Course dropdown will then be
    populated with an additional field representing that course.

    ![qa helper](/assets/course-page.JPG)

### TFS - Board View

![qa helper](/assets/tfs-ui.JPG)

1.  To QA

    Clicking this button will automatically scroll the screen over to the QA section of the Kanban board.

### New Slide

![qa helper](/assets/newslide-ui.JPG)

1.  Next Slide

    NOTE: because QA is best done as close to the student experience as possible, it is not recommended that this button is used while doing actual QA work Clicking this button will force the Web to navigate you to the next slide, regardless of the normal constraints that are placed upon navigation for students.

2.  Run Comparison

    NOTE: due to imperfections in the OCR technology that is used as the backbone of this feature, it is considered experimental, and QA results should not depend upon its output 
    
    NOTE: Although rate limits
    are high, it is possible that this feature could be limited.
    Clicking this button when both a New Slide and an Old Slide are open
    at the same time in Google Chrome will trigger a visual programmatic comparison using Optical Character Recognition technology. This means the computer will try and read the text on the screen and then compare the results. Text that the computer flags as "matching" will be marked in green, while text that the computer flags as "not matching" will be marked in red. Since this tool's accuracy entirely depends on the accuracy of the third-party OCR engine that it relies upon, its results are not completely accurate and should not be fully trusted.

3. Add Bug

    Clicking this button will automatically grab the reference information from the current slide and send it to TFS's backlog view (a TFS tab must be open in the browser for this to work). That backlog view will receive the information and use it to find the appropriate Content QA folder on the page and programmatically fill out the basic template for adding a bug, complete with the appropriate tags and initial title name.

4. Previous Slide

    NOTE: since QA is best done as close to the student experience as possible, it is not recommended that this button is used while doing actual QA work Clicking this button will force the Web to navigate you to the previous slide, regardless of the normal constraints that are placed upon navigation for students.

### Limitations
The tool sometimes causes the following problems:

- Next button on Blackboard slides remains grayed out even after the narration is finished.
- Answers won't scramble when user clicks "Redo" on a multiple choice question.
- Checkmarks will not be shown next to correct answers when "Check Answers" is clicked.
- On very rare occassions, the "Jump to Web" button on the blackboard website may navigate you to a new slide and an old slide that do not match.
- If two old slides or two new slides are open at the same time when the text comparison is run, one of the two new or old slides will have a black box remain on it.
- See Troubleshooting below for solutions to these problems.

1.4 Troubleshooting

To overcome the limitations of the QA-Helper tool listed above, do the following (numbers are comparable):

- (1-3) Close out of and reopen the web you are currently doing QA for.
- (4) Navigate to the courses individually by clicking the proper links on the Blackboard & Avondale sites.
- (5) Restart your QA-Helper tool by closing out of all pages that the QA-Helper tool set up for you and clicking on the Chrome extension again. Then retry the run comparison with only one new slide and one old slide open.

If problems persist, please contact any developers working on this tool.

### TODO
See if there is any value in upgrading our OCR API access to an increased number of requests per month.
