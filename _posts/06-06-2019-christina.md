6/5/19
================

<p class="meta">5 June 2019</p>

My time today was split between two main tasks: figuring out the fact automation that I began yesterday, and researching the many forms our final project could take. I started the morning by continuing the fact automation, putting my strategy into place. However, we decided to split up the work, and my partner took over processing the facts while I worked on researching packaging options as well as familiarizing myself with the work done with the shade canopy from last summer. 

I began by looking into creating an AppScripts library, which seemed doable given the form of what we had already done. A library just required the work to be uploaded and simple documentation to be attached. Like any other library, the applications of this library are solely within Google App Scripts projects. This means that other users could write App Scripts code including methods from our program, however this did not address the non technical user we had intended: the nonprofits themselves. Hassling with code and breaking our work into components, I felt took away from its strengths, so this left a couple of other options. Next, I looked into Google Extensions, such as those downloaded on the Google Chrome web store. This was a step in the right direction as it allowed our code to remain together and be utilized without any scripting by the end user. However, we really just need our program to operate attached to the spreadsheet, otherwise functions such as getUi() and the like, do not work. This informed my search, and publishing as a Google Sheets extension seemed to be the best way to go. Even this was not ideal, though. How were we to ensure that the user had the proper forms set up, a Twilio number, and an OWM API key? Despite these concerns, I looked further into the requirements for an add-on and familiarize myself with Google’s requirements. Google has a strict UI style guide, so I changed text features within our program to adhere to the guide. I also had to reformat our menus, as add-ons do not have the necessary permissions to make extra, top-level  menus. These both were an easy fix. Google’s other requirements seem a little less simple, however, and I am concerned going forward because of the amount of personal data our program needs to access. I feel as if this is outside of the realm of a normal Google Sheets add-on. Because of how many permissions we need, there is an extra process to go through in order to get verified before publishing. 

For the second part of the day, after coming to a rough conclusion on publishing, I went back to work on the transfer and integration of tree facts. I had noticed that my partner had not made progress on his morning task of automating the choice of tree facts into the sendMessages() function. After 3-4 hours, he had been able to select the current sheet of the spreadsheet of tree facts, but not much further:

    function getSheetId() {
      var ss = SpreadsheetApp.getActiveSpreadsheet();
      var sheet = ss.getSheets()[0];
    }

At this point, I wanted to help him out a bit, because this was not a task that was meant to take more than a day. So, I decided to write some basic code in the way that I would have done it to give him a basic outline and maybe spark some more ideas. Looking back, this is a bad idea because, to him, it appeared as if I didn’t trust him to do the task. At the time, I didn’t see this, and I ended up writing a successful function to process, select, and log tree facts, integrating them into the messages sent. I quietly put this into the main code, and then asked my partner to improve upon it. He was understandably a bit upset that I had seemingly done the task for him, but with the lack of work that got done, I was just trying to push the larger project along.  He didn’t want to try to improve it, so I went ahead and placed it into the code. Below is a brief rundown of how the code I wrote functions: 

The data from the fact sheet is imported into the MessagingBase.gs file
Check each row’s status column, if there is a date logged, the fact has already been used and will not be used again
A list of the row numbers of rows with available facts is made
A row number is randomly chosen from its list
The status column of this row is logged with the date, documenting use and preventing future use of fact
The fact in this row is returned
“%fact” in the body message is replaced with the fact before translation and transmission of message

Tomorrow I want to work further on actually packaging the program, rather than just reading about it. I am thinking about ways to set global variables when a new user begins to use the program. Tomorrow I plan on creating that feature, and doing research on ways to store data indefinitely, as would be necessary for the global variables. 
