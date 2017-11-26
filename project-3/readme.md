# Project 3 - What Makes a PGA Tour Player of the Year Season?

## Introduction

This folder contains all data files and code for analyzing both the 2016 and 2017 golf seasons for professional golfer Justin Thomas, which is for the DATA 550 class at Mercyhurst University in Erie, PA for the Masters in Data Science graduate program.

## Objective

For this project, we want to find out what statistics were improved for Justin Thomas between 2016 and 2017.  Looking at the [supplied statistics for Justin Thomas](https://www.pgatour.com/players/player.33448.justin-thomas.html), we see that in 2016 he only won once, and finished 12th in the FedEx Rankings. In 2017, he won 5 times (one of which was a major tournament), finished 2nd in the FedEx Rankings, won the FedEx Cup Playoffs, and more than doubled his official money earnings. 

Year | Events Played | Wins | Top 10s | Missed Cuts | Win % | Cut %
--- | ---: | ---: | ---: | ---: | ---: | ---:
2017 | 25 | 5 | 12 | 6 | 20.0% | 24.0%
2016 | 28 | 1 | 7 | 6 | 3.5% | 21.4%
2015 | 30 | 0 | 7 | 7 | 0.0% | 23.3%

In an article in the November 2017 issue of Golf Digest, Thomas noted that "the big difference was working hard on my putting consistency" and that he "worked hard on putts over 10 feet". This project will investigate his targeted practice on putting and compare it with a variety of other stats that could have been a difference maker.  

## The Data

The data for this project comes via the [PGA Tour Shotlink Intelligence System](https://www.pgatour.com/stats/shotlinkintelligence/overview.html). In August 2017, I applied for and was given access to the data available. The particular set of data I will be using is the Round Details. I downloaded the full data for the 2016 and 2017 seasons for every player and every official tournament. These files are semicolon delimited text files and are named ```rround-2016.txt``` and ```rround-2017.txt```.

Within these files there are 176 columns of data and the definitions of which can be found in the [definitions file](Round Detail Field Defs.pdf).

## Cleaning and Parsing the Data

After filtering out only Justin Thomas's rounds from both the 2016 and 2017 files, a quick look at the "Round Score" field shows some interesting results for 2017.

```python
jt2017['Round Score'].describe()

count    86.000000
mean     68.558140
std       5.844262
min      36.000000
25%      67.000000
50%      69.000000
75%      71.000000
max      80.000000
Name: Round Score, dtype: float64
```

Any follower of golf will see that a minimum score of 36 for 18 holes of golf is not plausible. The official lowest round of golf on the PGA Tour is 58. Filtering out any Round Score less than 58 shows 2 rounds for the same tournament, the Zurich Classic of New Orleans. This tournament followed a less traditional scoring format. This was a team event, and the 2nd and 4th rounds of golf were in the four-ball format (i.e. best ball). This format has both players playing their own ball to completion, but the official score uses the best of the two player's scores. Because of this format, the Round Score for these two rounds can be eliminated from the data, leaving the following:

```python
jt2017 = jt2017[(jt2017["Round Score"] >= 58)]
jt2017["Round Score"].describe()

count    84.000000
mean     69.250000
std       3.721883
min      59.000000
25%      67.000000
50%      69.000000
75%      71.000000
max      80.000000
Name: Round Score, dtype: float64
```

Now we have a more accurate representation of his season, with those two rounds altering his average score by 0.7 strokes.

*show each plot with rest of field?*

## Off the Tee Analysis
* accuracy
* distance
* combined driving

## Approach Analysis
* shots into the green from varying distances
* break down by distance ranges and fairway vs. rough

## Short Game Analysis
* 100yds and in
* Not including putting
* Separate out bunker play

## Approach Analysis
* plot gir accuracy from each distance set (combined rough and fairway)
* compare rough vs. fairway
* proximity to the hole

## Putting Analysis
* 3, 4, 5, 6, 7, 8, 9 ft comparisons
* long putting comparisons 10-15, 15-20, 20-25, > 25

## Against the Field Comparisons
* compare 2017 with rest of field in major categories
* no laying up comparison

## Miscellaneous Analysis

* Compare tee times with performance
* Compare course length with performance
* No laying up
* Majors