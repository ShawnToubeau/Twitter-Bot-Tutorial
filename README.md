# Twitter Bot Tutorial

Hello new bot commander. This post uses a very basic bot framework that I've put together, and I'd encourage you to fork it for your own bots. You should also be able to create your own from scratch using my instructions here.

## Create a Twitter Account
Possibly the hardest part of creating a Twitter bot is coming up with a good username that isn't already taken. I can't help much with that, but once you've come up with something, [register the account](https://twitter.com/). You can futz with the avatar, description, cover photo, and all that now, or wait until later.

## Create the Twitter App
In order to post to a Twitter account automatically, you have to get access keys for your account. To do this, you have to register a Twitter app. Head over to [apps.twitter.com](apps.twitter.com) and click "Create New App".

You should note that you need to have a unique phone number associated with the Twitter account in order to create an app; this is a damn pain. For those such as myself who have more Twitter bots than we have phone numbers, there's only one real solution, and it's not a good one:

1. Choose an account to use as your developer account and associate your phone number with it.
2. Create a new account for your bot.
3. Register the Twitter app for the bot on the developer account.
4. Head over to Twitter API support and select "I need to transfer an API key to another account".
5. Fill out the form (make sure you're still signed into the developer account).
6. Wait an arbitrary amount of time (it's usually been about a week for me, but sometimes much longer) for someone at Twitter Support to manually transfer the key.
7. Grumble about how there's got to be a better way to do this.
Once you create the account, it'll ask you to fill out a few fields:
1. Name: Whatever you want to call your bot.
2. Description: A short description of what the bot does.
3. Website: I usually just put down my own website or my Github, or the link to the Github repo for the given bot.
4. Callback URL: You can skip this.

Check the box to agree to the developer agreement, and click create!

Go to the "Permissions" tab and set the access level your application needs. This will probably be "Read and write".

Go to the "Keys and Access Tokens" tab of the application and click the "Create my access token" button under the "Your access token" heading.

##Write the bot! 
I've created a very simple bot framework to go along with this tutorial. It will give you the general structure, as well as some simple logging functionality, which I find very useful for debugging purposes.

This tutorial assumes some knowledge of Python. It's also going to assume that your project is structured like so:
```
twitter-bot/  
|-- bot.py
|-- secrets.py
```
`bot.py` will hold all the code for the bot. `secrets.py` will store your access keys, and should be added to your `.gitignore` if you're going to be publishing the code. Anyone with access to your keys can read or write from this Twitter account, so you really don't want to make these public.

##Pick your library
If you like making things difficult for yourself, or if you're using a language without a [Twitter library](https://dev.twitter.com/resources/twitter-libraries), then I suppose you can communicate with the [Twitter API](https://dev.twitter.com/rest/public) directly. Otherwise, I'd highly recommend picking one of the many Twitter libraries. My personal favorite is [tweepy](http://www.tweepy.org/), and that's what this tutorial uses.

Install tweepy by running `pip install tweepy` in your terminal. Now you can just `import tweepy` at the top of `bot.py`.

##Authenticate
In order to read or write from the Twitter account, you need to authenticate.

Go back into the "Keys and Access Tokens" tab of your Twitter app. In secrets.py, add:
```python
C_KEY = ""  
C_SECRET = ""  
A_TOKEN = ""  
A_TOKEN_SECRET = ""  
```
Add the following from the Keys and Access Tokens page inside the quotation marks:
1. `C_KEY`: Consumer Key (API Key)
2. `C_SECRET`: Consumer Secret (API Secret)
3. `A_TOKEN`: Access Token
4. `A_TOKEN_SECRET`: Access Token Secret

Again, if you're going to be publishing this code, it's important that you don't publish the `secrets.py` file.

In `bot.py`, add the following:
```python
from secrets import *

auth = tweepy.OAuthHandler(C_KEY, C_SECRET)  
auth.set_access_token(A_TOKEN, A_TOKEN_SECRET)  
api = tweepy.API(auth) 
```

##Create tweets
This bit is somewhat up to you. You'll need to create the content yourse, but I can give you some resources that I've found to be really useful:
1. News headlines: Guardian API, Google News RSS (needs to be parsed)
2. HTML parsing: BeautifulSoup
3. Parts-of-speech tagging: topia.termextract
4. Word and dictionary magic: Wordnik
5. Rhymes: RhymeBrain API
6. Weather information: Forecast.io API
7. Markov chaining: cobe
8. Interesting corpora
9. Other APIs: Mashape

##Post tweets
Once you've got your tweet all together, post it!
```python
api.update_status(tweet)
```
This only posts a standalone tweet. If you want to reply to another tweet, direct message someone, or do other fun things, check out the [tweepy documentatio](nhttp://docs.tweepy.org/en/latest/api.html).




