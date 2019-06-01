5/30/19
================

<p class="meta">30 May 2019</p>

Today was the first day that I have really, truly been frustrated. Before now, I have run into roadblocks, but they turned out to be something I could work around by changing my paradigm or even just putting more time into tackling. Interestingly enough, it wasn’t the complexity of my code, or even the logic of the problem that I set out to solve, that made my day so difficult: it was the criticism and lack of help from my partner. We began work today by trying different strategies on the same problem: trying to figure out how to take user time preference into consideration to send automatically triggered messages at three different times of day. This would allow for residents served by Sustainable Claremont to receive reminders when it is most convenient to them. In theory, if the reminders come at a time that is conducive with their schedule, they will have the time to water trees before forgetting about the reminder altogether. For example, if I got a reminder to water my trees while I was at work during the day, I would likely forget to water by the time I got home in the evening. Ideally, I would request reminders in the evenings while I am at home so watering my trees can be a more immediate task. Because the schedules of individuals vary greatly, we wanted to provide flexibility.

After trying our separate strategies for a bit, we conferenced with problems we had found in each of our work. This is where I felt trouble began, as my partner would continue to shoot down my code, my strategy, and my competency. Though I’m sure it was unintentional, it hurt nevertheless. When I tried to explain myself, I was ignored and the whole dynamic was very tense. That was a lesson to me not to try to attempt the same problem at the same time again. If this exercise had worked out as I had hoped, we would have been able to help each other see different logical pathways and combined the best aspects our code for a stronger overall product, but this did not happen. Sadly, I really think talking the problem out would have helped me. 

I started the day with the hopes of using triggers for three different sheets within our spreadsheet as to avoid iterating down the rows more than necessary. Because timing is based on external elements to the program (triggers), I did not feel as if I could have worked it into our current for-loop that checks the data for language, zip code, and contact information. After reading App Scripts documentation on triggers, I felt that this definitely was not the way to go, so instead I decided to run one trigger for each time preference at each time. This was the simplest set up I could envision. This, however, necessitated three sheets where before we had just one, so my goal became to automate the creation of these three sheets. I took the following approach:

1) Get data from the Google Forms response sheet
2) Process only the data that had not already been processed by checking where the last entry in a logging column was
3) Iterate through those rows, checking the value of the column in which time preference is stored
4) Copy the data of the rows to the bottom of one of three different sheets based on this value: ‘Morning’, ‘Afternoon’, and ‘Evening’
5) Log a date of transfer in the logging column of the form response sheet

After writing a successful program to do just this, I presented it to my partner who referred to it as a “stupid” way of doing things. Whatever. Even if it was not what we needed, I was impressed with myself for working with the complex App Scripts methods it called upon. I had intended for there to be three triggers attached to the spreadsheet calling each of the three sheets at their respective, appropriate times, but assigning a specific sheet to a trigger seemed undoable, so I scrapped my work and took a second approach at the problem. 

After lunch, I began to see if I could work the timing into the message-sending code itself. While my partner read articles online and watched TED Talks (I think the frustrating morning rendered him pretty much unproductive in the afternoon), I implemented conditional statements into our sendMessages(weatherData) function to check the user’s time preference within our already existing for-loop and the current time by checking a locally defined variable that represented the hour of the day 0-23. I defined hour ranges for morning, afternoon, and evening, and gave the following logical conditions:

	If it is morning and the user’s preference is morning:
		Send the message
	If it is afternoon and the user’s preference is afternoon:
		Send the message
	If it is evening and the user’s preference is evening:
		Send the message

Looped through the list, and triggered three times a day (once during each time period), this code worked and sent messages to the correct recipients at the correct times of day. I was incredibly pleased with my work and very happy that most of the requests by Sustainable Claremont had now been fulfilled. When testing, however, I ran into some inconsistencies in the logging of messages being sent. I fixed and rebroke the feature several times, and currently am getting very odd results that seemingly vary based on none of the ‘independent variables’ of my tests. This is a problem I will hopefully correct on Monday, along with fixing formatting, reducing runtime, and improving overall  efficiency. 

In the end, today was certainly a frustrating day. I am disheartened by the social aspects of my working environment, but it could have just been an unlucky day, a fluke. Despite this, I am still proud of my work that came out of the day, and I am determined to keep working on fixing this feature on Monday.


