---
layout: single
title:  "Overwatch League Data Cleanup"
excerpt: "I used SQL to clean 4,958,301 rows of data from the Overwatch League and organized the data into an SQL database that was connected, easy to access, and immediately ready for use."
breadcrumbs: true
---

```
import pandas as pd
df = "dog fight"
test code block
looking good
print(cat)
```

\>INVENTORY
{: .notice--primary}
- SQL

\>BRIEF
{: .notice--primary}

  I used SQL to clean 4,958,301 rows of data from the Overwatch League and organized the data into an SQL database that was connected, easy to access, and immediately ready for use.
  
\>VERBOSE
{: .notice--primary}

  I took data from [the Overwatch League website](https://overwatchleague.com/en-us/statslab){:target="_blank" rel="noopener"} and uploaded it to my SQLite database. This was 4,958,301 rows of data from 14 flat CSV files. Some of the challenges with this data included:
  - Spelling errors
  - Inconsistent formatting  (e.g. match start times were in different time formats)
  - Incorrect values  (e.g. some round numbers increased in increments of 2 instead of 1 and some match times were listed as being shorter than how long the match actually lasted)
  - Missing values
  - Duplicate rows
  - Outdated names  (e.g. McRee has since been renamed to Cassidy)
  - Lack of overarching organizational structure

  After transforming the data with SQL code (which you can find on my GitHub [here](https://github.com/mtollefsen/overwatch-league-data-projects/tree/main/Data%20Cleanup){:target="_blank" rel="noopener"}) the end result was a connected database of 7 tables (pictured below) in first normal form. I fixed all of the problems listed above and further enhanced the data by adding:
  - **primary** and *foreign* keys
  - constraints
  - data on all of Overwatch's current heroes (the `hero` table in the image below)

  Many times I had to consult VODs of the matches using the URL [https://overwatchleague.com/en-us/match/match_id](https://overwatchleague.com/en-us/match/match_id){:target="_blank" rel="noopener"} (replacing "match_id" with the actual match ID) or [Liquipedia](https://liquipedia.net/overwatch/Main_Page) to ensure I was understanding where my data was incorrect and how I might troubleshoot it.
  
  ![Overwatch League Database Schema](/assets/images/Overwatch League Database Schema.png)
