---
title: "Overwatch League Data Cleanup"
layout: single
classes: wide
permalink: /portfolio/overwatch-league-data-cleanup/
breadcrumbs: true
author_profile: true
share: true
---

I took 14 flat CSV files from the [Overwatch League website](https://overwatchleague.com/en-us/statslab){:target="_blank" rel="noopener"} containing nearly 5 million rows of data in total and cleaned and organized it into a connected database of 7 tables in SQL. The code I wrote to do this can be found [here](https://github.com/mtollefsen/overwatch-league-data-projects/tree/main/Data%20Cleanup){:target="_blank" rel="noopener"}.

## Before
#### 4,958,301 rows of data from 14 flat CSV files<br>
#### Problems included
- Spelling errors
- Inconsistent formatting
- Incorrect values
- Missing values
- Duplicate rows
- Outdated names
- Lack of overarching organizational structure

## After
#### 4,920,155 rows of data connected across 7 tables<br>
- 5 tables in a hierarchy `season` > `stage` > `match` > `game` > `round`<br>
- 2 reference tables `player_stat` and `hero`
  
#### Changes include
- Fixing all of the aforementioned problems
- Adding **primary keys**
- Adding *foreign keys*
- Adding constraints
- Adding new data via the `hero` table
- Bringing database to first normal form
  
  ![Overwatch League Database Schema](/assets/images/Overwatch League Database Schema.png)
  *The seven tables that make up my database, lines show which variables connect tables*
  {: style="text-align: center; font-size:0.8em;"}


