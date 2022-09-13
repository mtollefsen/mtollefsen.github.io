---
title: "Liquipedia API Web Scrape"
layout: single
classes: wide
permalink: /portfolio/liquipedia-api-web-scrape/
breadcrumbs: true
author_profile: true
share: true
---

#### Tools
{: .notice--primary}

- Python
  - BeautifulSoup
- SQL

#### Summary
{: .notice--primary}

  I wrote [Python code](https://github.com/mtollefsen/overwatch-league-data-projects/blob/main/Liquipedia%20API%20Web%20Scrape/player_info_web_scrape.py){:target="_blank" rel="noopener"} that web scrapes Liquipedia.net for information on Overwatch League players with a 98% success rate and uploads the data to my Overwatch League SQL database.
  
#### Details
{: .notice--primary}

  Liquipedia.net has an entry on most (if not all) professional Overwatch League (OWL) players. My [Overwatch League database](/portfolio/overwatch-league-data-cleanup/){:target="_blank" rel="noopener"}, in contrast, only has each player's in game name. To remedy this I wrote [Python code](https://github.com/mtollefsen/overwatch-league-data-projects/blob/main/Liquipedia%20API%20Web%20Scrape/player_info_web_scrape.py){:target="_blank" rel="noopener"}  that would scrape a player's information from Liquipedia.net and upload it to my SQL database. Specifically the code grabs information on a player's:
  - real name 
  - romanized name (if applicable)
  - birthday
  - country
  
  My code accomplishes this by first taking every player's name currently in my database and sending GET requests to Liqupedia's API, looking for the web page on Liqupedia.net that matches that player's game handle. When found, Liquipedia sends back the HTML code for that page which my code parses (using the Python package BeautifulSoup) for the above listed information. After an attempt has been made to scrape every player's information from Liquipedia the resulting data is uploaded to my SQL database and automatically connected to each player's game name.
  
  Because each webpage is case sensitive the code will try to search multiple formats of a player's in game name if the previous format doesn't find a webpage. Here's an example where we are trying to find the webpage for a player whose in game name is listed as "WiNner BIRD", the code will send GET requests for the following webpages in the order that they appear until one is found or none work:
  - WiNner BIRD (original format)
  - Winner bird (capital case)
  - Winner Bird (title case)
  - WINNER BIRD (upper case)
  - winner bird (lower case)
  
  Occasionally the code will reach a page that isn't the player's Liquipedia entry but instead has one or more redirect links to different entries on the site. If the code encounters only one redirect link it will send it's next GET request to the redirect link provided and get the player's information from that link if possible (a single redirect link is common where a player's name is commonly misspelled). If the code encounters multiple redirect links it will mark the player's name as "ambiguous" and move on to the next player name on its list (multiple redirect links are common when multiple player's share the same name, see the Liquipedia page for [Snow](https://liquipedia.net/overwatch/Snow){:target="_blank" rel="noopener"} as an example). Finally, if the code is not able to find a player's Liquipedia page after exhausting all of its options it will mark the player's name with "could not find page".
  
  At the time of writing this (March 1, 2022) of the 373 players it searched for, the code successfully found the pages and scraped the information of 364 players, a ~98% success rate.
  
  Below is a flow chart that shows the code's logic:
  
![Liquipedia API Requests Flow Chart](/assets/images/Liquipedia API Requests Flow Chart.png){: .align-center}
*Per Liquipedia's API Terms of Use all requests are spaced out by 30 seconds*
{: style="text-align: center; font-size:0.8em;"}

**Copyright:** Liquipedia content is licensed under CC-BY-SA 3.0, which requires that you attribute Liquipedia as the source of your data. See [Liquipedia:Copyrights](https://liquipedia.net/commons/Liquipedia:Copyrights){:target="_blank" rel="noopener"} for more information.
{: .notice--info}


