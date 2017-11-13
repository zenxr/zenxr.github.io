---
layout: post
title:  "Automating github fetch and push for jekyll"
date:   2017-11-13
author: Cody Stephenson
---
This web server runs on a VPS I'm renting from [SSD Nodes](https://www.ssdnodes.com). However, I'd like to be able to add posts without having to ssh into the VM.

### Ideal Interface
I'd like to be able to:
* Edit the server from anywhere (even on my phone)
* Still use PHP, MySql, etc if I wanted to
* Have it be as seamless as possible. If I update the repo, I want the server to automatically update the jekyll folder.

### Scripts
I'm writing some bash scripts. 
1. One checks to see if the remote GitHub repo has changed and calls the other script if so.
2. The other script (because I'm scrub and haven't properly set up jekyll yet) just pulls the latest changes, and places the `_site` folder generated as `/var/www/html`.
3. Then I can use a chronjob to automatically run the outer script.

*I'm actually writing this post to see if the scripts will work properly right now.*
