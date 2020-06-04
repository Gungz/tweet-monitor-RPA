# Tweet Monitoring RPA

## Theme
Governance & Administration

## Idea
Currently there're around 330 million monthly active users in Twitter and the users often tweet about hot topics that happen in the world and Covid19 is definitely one of them. Simple search in [Twitter](https://twitter.com/explore) shows there're Covid19 Hashtag for each country (e.g. #Covid19USA, #Covid19India, #Covid19Indonesia, etc.) and the tweets generated from Twitter users definitely are worth to watch for because it can give government insights directly from people who feel the hardship of Covid19 impact. 

The overall idea includes :
1. Monitoring a certain hash tag in Twitter using RPA bot and copy the tweet to excel
2. In the 1st phase, have someone from government manually analyze it and send to respective ministry department for follow-up (this 1st phase copy to Excel is what will be submitted and demonstrated in video).
3. In the 2nd phase, send the Tweets to Machine Learning API in the cloud to extract sentiment analysis to help government understand what the people feel about Covid19 from social media such as Twitter. Also, with help of Machine Learning the Tweet should be automatically classified to relevant Ministry Department of a country e.g. a Tweet about lack of hospital or medical equipment to test Covid19 should go to Health Ministry Department, Tweet about lockdown causing people living in rural area unable to get food or daily necessities should go to Social Ministry Department or Regional Government, Tweet about people losing job should go to Manpower Ministry Department, etc. These Machine Learning API for classification and sentiment analysis should be developed separately but the API call can be done by RPA.

## What it does (implementation)
The current RPA bot which is submitted in this hackathon is already able to:
1. Accept input from users on the hash tag to monitor, the folder where the excel file to capture the tweets is located, and the delay between loop.
2. Open browser with Twitter URL based on the hash tag to monitor.
3. Create excel in the specified location and add the column header (if not yet exist).
4. Loop to capture the Tweet and Twitter User ID and copy the same to the excel file until stop signal is given (by putting file named stop.txt in the same folder of the excel file capturing the Tweets).
5. Close the browser and the excel file (saving the data when closing).

## Prerequisite before Running the Bot
1. Ensure you have Google Chrome browser installed on the machine running the bot.
2. Login to your Twitter with the Chrome browser and you can close the browser (the bot doesn't handle login so you need to manually login to your Twitter account).

## How I built it
1. Find the idea to be implemented.
2. Learn about Automation Anywhere from the AA university (I even already took the exam for A2019 Advanced Certification).
3. Get hands dirty by implementing it.

## Challenges I ran into
1. Originally I want to use CSS selectors or XPath that take multiple HTML elements to capture the tweets, however I realized that the Recorder: Capture doesn't support it. Hence, I can only take top latest tweet after refreshing the screen. While it works for hashtag that generates new Tweets let's say per 5 seconds (if delay is put as 0), it will miss some tweets if many new tweets are generated per second or below 5 seconds. In order to handle this, I think I need to take the HTML as String and then do my own logic of parsing in Javascript or Python to fetch and extract data from relevant HTML elements, or experiment with XML: Execute XPath function to get multiple nodes (not sure it will work with HTML but not yet tried). 

It would be really great if Recorder: Capture can support capturing multiple HTML elements by modifying CSS selector or DOM XPath after capturing object on the window and allowing us to assign the elements to variable with type Record or List of HTML elements.

## Accomplishments that I'm proud of
1. The amount of time spent to make the bot is only between 2 and 3 working days (already including the learning for certification and exam). This is quite fast to achieve such results although my RPA bot is not perfect and many improvements can be done but in such short time to successfully build some interesting RPA bot, I am pretty proud and happy.

## Potential Impact
1. Help government leverage social media to understand the sentiment and situation of its people suffering the impact of Covid19.
2. Release manpower to copy paste Tweet from monitored hash tag to excel file.
3. By leveraging machine learning, I hope the right ministry department is contacted in timely and automated fashion to provide help and relief package to the people needing the most. Government can also make certain hash tag and socialize to people to use the hash tag for reporting people in needs of urgent help. As many people nowadays are mobile-phone savvy and have Twitter account, this could prove useful as one of communication channel for people to contact government when asking for help.

## What's next for Twitter Monitoring Bot
1. Implement Phase 2.
2. Improve the RPA bot so that it misses as few tweets as possible for the hashtag that generates huge amount of tweet stream and if the Tweet involves some reply in the conversation.
3. Handle Twitter login from RPA bot.