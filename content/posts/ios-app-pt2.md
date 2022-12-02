---
title: "Building an iOS app (pt 2)"
date: 2016-01-12
draft: true
---

I wrote this when I really didn't know much about apps and tech, decided to not edit for my naive genuine thoughts at the time.

It's been a while since I started making the app. After about a month I had all the features down and learned a lot about the Swift language and app making in general! After getting a job, I had less time to work on the app, so it has been on the list of things to do for me. In this post, I'll talk about some new features I added, some updates to the UI of the app and finally talk about why I've stopped working on the app as a product I will ultimately release.

Design Adjustments
[1] Login Screen
[1] Login Screen
[2] Sidebar and Main-View
[2] Sidebar and Main-View
[3] Search and Detail-View
[3] Search and Detail-View
Looking back at my initial post, I can see that my design needed significant improvement. One great aspect of iOS over Android is the consistent version control and user experience one can control across different devices and screen sizes. One aspect of my app I wanted to improve was the experience from opening the app to making the purchase. The old version of the app was clunky, not visually appealing and laggy at certain parts. Some of the fixes and additions to the design were:

Better Colours and Formatting
The first change was to make the login screen fit the colours of my logo. With a similar colour, it almost seems like the t-rex is a part of the background, with the triangles making the body in the negative space! The next change was to make the table cells more aesthetic, with the picture being the highlight, instead of the name of the fitness location. Overall this allows more information to be displayed to the user. Another addition was the background to the menu bar and fine tuning the transitions to feel more logical (a button on the right side of the screen should cause a transition from the right and so on).

A final change was moreso in the background and involved coding the requests to my Parse backend to not lock up the screen in certain situations. If you've ever used an app and had the screen not track your fingers movements or had to lose control of the app to some invisible buffering in the background, it's not a great feeling. Here's how the app looks after the changes:

The Story Behind the Logo
[4] Fiverr logo ($5)
[4] Fiverr logo ($5)
[5] Original Logo
[5] Original Logo
The initial plagiarized work

The "beautiful" redesigned logo

A tangent about the story behind the logo> When I first started, I wanted a cute animal to be the focus of my logo. Knowing how much it was to hire a real designer, I used fiverr (a website where people offer services for $5) to design my logo. After describing in detail what I wanted, I was ecstatic to receive something really great for only $5 (see left picture). After sending the jpg to my friend in product design, he sent me a link to the exact same design under the name of another artist. Going back to the fiverr designer (who resides in India like many of the vendors on fiverr) he reluctantly agreed to redesign the logo for me (picture on right). Needless to say, I did not like the new logo. The redesigned logo looks like he just overlaid the geometric shapes over an actual picture of a T-Rex. Instead, I decided to contact the original artist behind the plagiarized logo (http://www.drieren.nl/). I thought it was a long shot, but he ended up agreeing as long as I did not make a profit from my app. What a great guy!

Doing some market research
[6] Overview XIB
[6] Overview XIB
Prior to redesigning the look of the app, I sent out a blast of emails to various gyms across the city. After getting quite a few replies, I booked an entire week full of appointments to visit gym owners. The plan was to first do a bit of research into what common problems they had competing with the big gyms and what they thought could be done to make their experience better. I made a question list and a strategy for how I would convince them to use my app.

Gym # 9 - Question List
My questions were split into 2 phases, where the second set were asked after I spoke about the app I had created. Some of the most important questions I wanted to be answered were:

[General] Who are your members and which membership option is the most popular?
Do you make guests sign a liability waiver?
Do you offer day passes to your members?
How do you give members access (keycard, signin) and how do you track members?
To my surprise, I was able to meet with the owner or at least the manager of the gym on most occasions. Initially, I thought liabilities for guests would be an issue and a sticking point to gyms promoting one time use of facilities. However, after speaking to the owners, a couple new problems came up, the last making me rethink if there was a market for my app.

Integration into existing systems: The first was how my app would integrate into the way gyms managed their facilities. Before I had the conversations, I thought simply funnelling the guest pass fees through my app would suffice. However, after speaking to gym owners  I realized that most of them ran their businesses on practice management software. For the most part, the software makes it easier to manage membership fees, sign-ins and class schedules. However, being businesses that have to ultimately report to the CRA and also the owners themselves, the software is able to create reports and run analytics on the data obtained from business operations. If they decided to accept money from my app, they would not only have to train their front desk staff (given they are not a 24h gym with only keycard access), but also manually update their reports. One example of a similar process is Groupon:

Case Study Groupon - Groupon functions much in the same way I wanted to design my app. The merchant app would scan a coupon from the user and the merchant would then manually enter an entry into the system to indicate a Groupon sale. Funds flow from Groupon every week/month and the books of the merchant would be updated accordingly.

The main differences between a gym membership (though Groupon does offer gym discounts) and the generally more frequent transactions of most Groupon categories is how familiar staff is with complexity. In most gyms, the staff is trained minimally and only authorized to scan user membership cards and watch the gates. Without a base of users or a few successful users I could point to, getting new gyms to join would be difficult. Makes me wonder how Groupon started it all.

Taking a break

After starting work at my new job I had less and less time to dedicate to making the app work. But, I'll keep trying to learn more whenever I get the chance. Hopefully I can make another post soon! I'll leave you with the files and the storyboard of my app! I was going to write about what I learned, but it's 2017 now as I revisit this, so I'll just leave a thumbnail of the different things I used.