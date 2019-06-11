6/3/19
================

<p class="meta">3 June 2019</p>

Despite last Friday’s frustrations, I was able to work today to finish up the time preferences on my code. I ended up integrating them as if-statements within both the sendMessages() code and the custom/scheduled messages functions called directly by the spreadsheet. I also was able to figure out my logging issues and it was laughably simple, but it took me a very long time to realize it. 

The main problem in logging that I encountered was its inconsistency within the try-catch statement used in sendMessages and the way that the list the errors created (update_status) was implemented into the status column of the spreadsheet. I began the day by testing where it ran into errors, and making some logical assumptions based on what I found. I found that the dates logged for all of the functions, which was good, but the errors never logged, unless they were the result of the first row called. I was confused how errors could be appearing if there was no error, because this defied what was written in the code. If something had an error logged, this meant the code had run in the catch statement, which would imply that the rest of the catch statement should have also run, but I didn’t find this. The catch statement was supposed to send an email for errors encountered, yet this seemed to function perfectly as intended; emails were not sent when the code ran successfully, even when the status column logged an error. How, then, could just part of the catch statement run? In retrospect, this should have been my first clue that my assumptions were wrong, and not my code. I had assumed that the physical logging of the errors were correct, but this is what turned out to be wrong in the end. It was sort of comical, really. Ater spending most of the day on this problem, it came down to a simple ‘s’ on a built-in function call that messed up my logging. Instead of “SetValues”, I was calling “SetValue” when I assigned the list created to the status column. This meant that only the first value of this list was getting assigned to ALL of the cells in the column, accounting for the odd occurrences of errors. Once I fixed this small error, the function worked exactly as intended.

Another task I began today was looking at automatic unsubscription. We had already made a Google Form on the Green Crew website for this task, but it relied on an individual cross referencing its results with the information on the spreadsheet. Because of the built-in compatibility of Forms and Sheets, I felt that it would be beneficial to automate this process, and wouldn’t take an absurd amount of time. I started the task by strategizing. This is the approach I decided to take:

1. Send unsubscription data directly to a sheet within our spreadsheet. 
2. Get the range of this data
3. Check a “status” column to see if the data had been processed
4. Select all rows without a date as their status (similar to sendMessages())
5. Search main sheet for the contact information provided in form, delete that row
6. Log date processed next to unsubscribed row

I didn’t get much beyond the planning of this, however, I plan on spending significant time tomorrow on creating this feature and ensuring that it works without a hitch. I find it very important to ensure perfect function because deleting data seems to be a task that cannot be undone. If the wrong data was deleted, there would be unfortunate repercussions. 
