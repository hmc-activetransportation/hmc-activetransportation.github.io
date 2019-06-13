6/12/19
================

<p class="meta">12 June 2019</p>

Today I was finally able to tackle the HTML dialogs and use their data to define the global variables used in the entirety of ‘Contact.gs’. I struggled with familiarizing myself with the JSON format, but once I understood what JSON actually looked like,  I was able to reference other places within the code in which I had previously used it to get an idea of how to parse and process it. I was initially confused because I thought what was JSON was simply what parsed objects look like. The dictionary of weather conditions that we got from the OWM API was the thing that was guiding me, but had I realized that this dictionary was actually already parsed, I would have saved a lot of time. 

Luckily, Professor Medero came early in the day, and she was able to clear up the confusion I had with the format. From there, I was able to alter my makeParameters() function to return an array of the values retrieved by the form. From this array, I used a helper function that I had already written to write an array to a column. I created a new sheet and hid it, so that it would be hard to edit, and therefore the program attached to it would be more robust. From here, I could use the App Scripts Sheet and Range classes to select this newly written column, and use specific cell values as my variables. This worked for almost all instances, however, I needed to change my approach a bit for the column assignments to assign columns for the contact and unsubscription sheets. When making the form, I decided to have the user input a list of the numerical columns used in the format of an array. I was hoping that, when parsed, I could recover this array and index into a list-of-lists to set individual column values. When I went to attempt this, though, what I had hoped was an array was actually a string. I tried using various Javascript methods on this string, until I found exactly what I was looking for: Array.from(). This function would have taken my array in the form ‘[1,2,3]’ and returned it as [1,2,3] when combined with parsing the initial list as JSON. I soon came to find out, unfortunately, that this method, like so many others, was not supported by Apps Script, so I needed to start my search again.

From there, I found a promising method: splitting a string by its characters and returning an array using string.split(). I checked that this was supported by App Scripts, and thankfully it was. When used on the string ‘[1,2,3]’, though it gave [“[“,”1”,”2”,”3”,”]”] which was very far from what I wanted. I then realized that I was the one requesting the input data, and could simply change the initial formatting. This made my task much simpler. Now, instead of requiring array format from the user, I require a string of numbers. Not only is this more computationally effective, it’s easier for the user themself. I split this string using the aforementioned string.split(), and it returned exactly what I wanted: a simple array. With this, I was finally able to index into the list-of-lists to retrieve the column numbers I desired. 

After finishing with the HTML form, Vivian and I spent time on understanding and fixing Parts I & II of the Tree Benefit Analysis code, starting with the selection methods used. None of us liked the use of dialogs to select start and end rows, so we decided to change this process to be more similar to the selection method on the Contact Info spreadsheet: determining the first and last row from the active range. This took much longer than expected because of the many offset values based on what was defined as the data range, and the normal repercussions that come along with changing an aspect of code that is called multiple times within the program. There was a lot of trial and error, and we lacked a good method of locating the errors specifically. I find handling errors very difficult when working in Google Sheets because of the vague and inconsistent error messages it throws off. Despite this, we were able to find success at the end of the day, realizing that our data range was much smaller than the original data range, so we needed to adjust how it was indexed. This seems like an easy mistake, but it got lost in the code and its complex logic. Now, the new selection system functions much better and faster than the old one, and we were able to simplify many of the functions to reduce run time. 

Tomorrow, I hope to dig even further into the intricacies of the Tree Benefit programs. I have ideas of where improvements can be made, and I look forward to starting to implement these ideas in order to improve efficiency and understanding of the program. Breaking this down, I plan on combining some of the recursive search functions, getting a grasp on xml, and finding ways to generalize the program to be used outside of its immediate purpose at Sustainable Claremont.  I also want to fix the individual benefits function, however, I think that this is a task that will persist beyond the scope of a single day.