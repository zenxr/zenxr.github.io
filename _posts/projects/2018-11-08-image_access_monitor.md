---
layout: post
title:  "Image Access Monitor"
date:   2018-11-08
author: Cody Stephenson
category: projects
---
I stumbled upon a post by [/u/phpnode](https://www.reddit.com/user/phpnode) detailing his [efforts to track the movements of his resumè.](https://www.reddit.com/r/programming/comments/9x2es/hi_reddit_my_employer_went_insolvent_yesterday_so/)
Although I'd prefer to keep my resumè in `.pdf` format for now, I thought this was an interesting application. Each script will still be independently useful for me later, so I've decided to build something similar to what he's done.

### The Image Access Monitor
The GitHub repo can be found [here](https://github.com/zenxr/ImageAccessTracker). 

The functionality of the project can be broken down into clear steps:

1. `monitor.sh` - Use a cronjob or other means of automatically checking for updates in an Apache2 access log. Note that the location will be different for many users. Although a bit crude, my method is to copy the file after every check; next time the file is checked we can compare against the previous copy.
2. `process_log.py` - Grab the IP from the access and return it's geographical location and organization. This functionality could be increased by doing a `whois` on the IP. Format the message body to include the desired information (that is: IP, location, date).
3. `sendmail.py` - Send the email using my gmail account

### Deployment
Note that this project won't work on windows, but could be modified to do so.

* Clone the repository, and create a `config.py` file based on `example_config.py`
* Ensure apache2 is running on your server, and has an image on it you would like to track. Locate it's access_log file after making sure it is enabled.
* Modify paths in `monitor.sh` as needed.
* Create a cronjob or some other method of automatically running the `monitor.sh` script.
