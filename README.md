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
8. Once you create the account, it'll ask you to fill out a few fields:
⋅⋅⋅Name: Whatever you want to call your bot.
⋅⋅⋅Description: A short description of what the bot does.
⋅⋅⋅Website: I usually just put down my own website or my Github, or the link to the Github repo for the given bot.
⋅⋅⋅Callback URL: You can skip this.
⋅⋅⋅Check the box to agree to the developer agreement, and click create!

Go to the "Permissions" tab and set the access level your application needs. This will probably be "Read and write".

Go to the "Keys and Access Tokens" tab of the application and click the "Create my access token" button under the "Your access token" heading.
