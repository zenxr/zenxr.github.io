---
layout: post
title:  "Comic Scraper"
date:   2018-08-26
author: Cody Stephenson
category: projects
---
There are some comics and manga that I've been wanting to read, however I don't really enjoy reading them through a browser.
I'd prefer to use something of my choosing.

### The Python Comic Scraper
The GitHub repo can be found [here](https://github.com/zenxr/ComicScraper). 
The project utilizes beautifulsoup to scrape a site and downloads and organizes comics. I'm still deciding on what type of GUI to make for it,
I'm not a fan of tkinter, even though its pretty simple. I'd rather create a web app so that users on my local network can read from any device.
However, the downloading functionality is working flawlessly.

### What it does
The `scraper.py` script is given a URL to the main page for a comic which contains a list of URLs to chapters.
It builds a list of chapters to be downloaded, then for each chapter a list of images is saved.

Individual complete comics are stored in a configurable location (somewhat of a library) with the following structure:
```
Title
├── chapter01
|    ├── page01.ext
|    ├── page02.ext
│    └── page...
├── chapter02
|    ├── page01.ext
|    ├── page02.ext
│    └── page...
└── chapter...
     ├── page01.ext
     ├── page02.ext
     └── page...
```

### Project Structure
This is likely to change as I determine what direction to take for the GUI. The `example_config` file is intended to be copied to `config.py` and
edited for the user's preferences.

```
ComicScraper
├── README.md
├── config.py
├── example_config.py
├── gui.py
├── requirements.txt
└── scraper.py
```
