---
layout: post
title:  "Automating github fetch and push for jekyll"
date:   2017-11-13
author: Cody Stephenson
category: projects
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

---
### Update
I ended up only creating one script. It checks the remote github repo's latest push vs the current version of the local repo. If changes are found, it
recompiles the jekyll site, and moves the \_site folder to /var/www/html while displaying some pretty text to the user. This could easily be made
a cronjob, it just isn't currently as it isnt a priority.

```bash
# Cody Stephenson
# checks github repo for updates
# if updates found, rebuild jekyll server and push to apache

# used to print pretty green font
green=`tput setaf 2`
red=`tput setaf 1`
reset=`tput sgr0`

cd ~/pages/jekyll_codystephenson/
git remote update
UPSTREAM=${1:-'@{u}'}
LOCAL=$(git rev-parse @)
REMOTE=$(git rev-parse "$UPSTREAM")
BASE=$(git merge-base @ "$UPSTREAM")
if [ $LOCAL = $REMOTE ];then
    echo "${green}Up-to-date${reset}"
# if we need to update, then update and do our page update script
elif [ $LOCAL = $BASE ]; then
    echo "${red}Need to pull${reset}"
    cd ~/pages/jekyll_codystephenson
    echo "${green}=====Pulling Changes=====${reset}"
    git pull origin master
    echo "${green}=====Building Site=====${reset}"
    bundler exec jekyll build
    echo "${green}=====Pasting to Apache=====${reset}"
    sudo rm -rf /var/www/html && sudo cp -r _site /var/www/html
    echo "${green}=====Restarting Apache=====${reset}"
    sudo /etc/init.d/apache2 restart
elif [ $REMOTE = $BASE ]; then
    echo "${red}Need to push${reset}"
else
    echo "${red}Diverged${reset}"
fi
```


