---
layout: post
title:  "Dauntless Bot"
date:   2017-12-28
author: Cody Stephenson
category: projects
---

A few friends and I have been watching a new MMORPG called Dauntless. We played a game called Raiderz that was shut down about a year ago, and are craving another MMO with true action combat. Dauntless has been in development for a while and is currently expected to fully release in early 2018. It's been in closed beta for a few months, but we had no luck getting beta-testing keys. However, occasionally keys are given away online by kind redditors and streamers!

----

### In comes the bot
* bot type: [discord.py](https://github.com/Rapptz/discord.py) and [praw](https://praw.readthedocs.io/en/latest/#)
* github link: [here](https://github.com/zenxr/dauntless_watcher_bot)

**Description**
I had an excuse to make another bot! I knew that the only possible way to ensure a quick reation time without constantly monitoring the reddit post was to have a bot do it for me. The bot checks for new messages every 60 seconds and sends them to our discord server if a new message is found.

1. The bot checks [this post](https://www.reddit.com/r/dauntless/comments/7jl6k3/reminder_sellingbegging_codes_is_not_allowed_if/?sort=new) every 60 seconds for updates.
2.	If a new comment is found, it formats a discord embedded message with the post, or if the post is too long the embed text indicates the message is too long to display.
3.	Next, a message is sent to a specific text channel where I'd like the messages displayed. If it is configured to tag users to alert them, they'll be @mentioned in the post.


### Success!
As of now, 6 people including myself have managed to get a key. The game still needs a lot of work, but it has potential.

![alt text]({{site.baseurl}}/img/blog_images/discord_reddit_success.png "bot screenshot")
![alt text]({{site.baseurl}}/img/blog_images/discord_reddit_success2.png "bot screenshot")
