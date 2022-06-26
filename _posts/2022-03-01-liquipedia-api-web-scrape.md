---
layout: single
title:  "Liquipedia API Web Scrape"
excerpt: "I wrote Python code that scrapes information on Overwatch League players from Liquipedia and uploads the data to my Overwatch League SQL database."
breadcrumbs: true
author_profile: true
related: true
share: true
tags: Overwatch League Python SQL API Web Scrape
---

```
>INVENTORY
```
- Python

```
>BRIEF
```
  I wrote Python code that scrapes information on Overwatch League players from Liquipedia.net and uploads the data to my Overwatch League SQL database.
  
```
>VERBOSE
```
  Liquipedia.net has an entry on most (if not all) professional Overwatch League (OWL) players. My [Overwatch League database](/overwatch-league-data-cleanup/){:target="_blank" rel="noopener"}, in contrast, only has each player's in game name (or game handle). To remedy this I wrote a Python script that would get a player's information from Liquipedia and upload it to my SQL database. Specifically the code grabs information on a player's:
  - real name 
  - romanized name (if applicable)
  - birthday
  - country
  
  My code accomplishes this by first taking every player's name currently in my database and sending GET requests to Liqupedia's API looking for the webpage on Liqupedia.net that matches that players game handle. When found, Liquipedia sends back the HTML code for that page which my code parses for the above listed information. After evry player's information has been scraped from Liqupedia the data is uploaded to my SQL database and automatically attached to 
