

# Did the Hall of Fame voter purge make a difference?

In a recent Jayson Stark article and about [lessons in hall of fame voting](http://espn.go.com/mlb/story/_/id/14521041/five-things-learned-2016-hall-fame-election), he mentions the following three assumptions about the Baseball Hall of fame voters after a significant number of non-active voters were eliminated:

> An electorate in which 109 fewer writers cast a vote in this election than in 2015.
>
> An electorate that had a much different perspective on players who shined brightest under the light of new-age metrics.
>
> And an electorate that appeared significantly less judgmental of players shadowed by those pesky performance-enhancing drug clouds.

However, are these last two assumptions true?  Did the purge of Hall of Fame voters make a difference?  Did the set of Hall of Fame voters least active have a different set of values than the those who are still voting? 


Arbitrarily, I decided to test this against the years 1995-2016, which gives a good 20 elections as well as starting at the year Mike Schmidt was elected to the Hall of Fame (which is utterly arbitrary other than Mike Schmidt being my favorite player when I was young).  However to figure this out, the first question that has to be answer is how does the average percentage change from year to year.  This ends up being a little surprising when you just look at the numbers: 



![png](hof_voters_files/hof_voters_11_0.png)


As a matter of fact, this year saw one of the largest increases at 8.2%.  Taken alone, this may indicate that something has changed with the removal of so many voters, but when viewed with all the other years, it does not look very exceptional as the values range between -6 to +8%.  The average change is an increase by 2% per year, but with a standard deviation much larger than it of 4%.  *The average change in percentage is either highly random or driven by something other than change in the number of votes.*  In fact, the change in percentages does not show any strong correlation with the number of voters or the change in number of voters.  


## Correlations with Hall of Fame classes

At initial glance, there is not much pattern to the data so pure randomness could be an explanation.  However, we can define a few other metrics to take a look at the data and it might give us a better idea of what is going on.  The first would be the number of Hall of Famers (hofs) elected in the previous class.  The second is defined as the strength of the class as the number of first ballot hofs in that class (For the record, I consider Bonds and Clemons as first ballot hall of famers as the would have been if not for their Performance Enhancing Drug (PED) history).  The third is the total number of hofs in a class, but that is uncertain for the most recent classes.    

A very strong trend does appears between the average change in the percentage and the strength of an incoming class minus the number of hofs elected the year before.  Unsurprisingly, when a strong class comes onto the ballot, they tend to take votes away from other players. Likewise, when a large number of players are elected, they free up votes for other players.  A linear relationship of $$s = 0.0299*nhof_{previous} -0.0221\times Strength - 0.0034\times(Total-Strength) - 0.00299$$ gives a very good fit to  $\Delta p$ and shows a strong linear correlation indicated by an r-pearson statistic of 0.95.  


![png](hof_voters_files/hof_voters_22_0.png)


## Change in Voting Habits


If we use this relationship, we can look at what the expected percentage average change in the votes were for 2016.   The expected change based on the existing data (1 First ballot hofs, 4  hofs the previous year, 1 total hof for class of 2016) was an increase of +9.0%.  The average increase for 2016?   That was +8.2%.  So, at least overall, the increase in percentages is exactly what was expected based on a moderate incoming class (if you also assume Trevor Hoffman will eventually be elected the expected change for this year is then 8.7%) and four players entering the Hall the previous year.  **From this perspective, the voting purge made little difference in how the  percentage of votes for a player changed.**  


Historically, players with higher vote percentage generally have seen their voting percentages increase.    In the figure below, we look at the difference between the change in vote percentage for a given player, $\Delta p$, and the expected average change for all players that year as compared to the player's percentage,  p, for the previous year.   The 2016 year (red squares) does not appear signficantly different than any other years (blue circles).  It is just more common that players with low vote percentages tend to have their vote percentages suppressed than players with higher vote percentages.   Nonetheless, there is large scatter in the distribution, which for any given player in any given year does not make it very predictive.   



![png](hof_voters_files/hof_voters_28_0.png)


### Have voters changed in terms of WAR or PEDs?

If we look at the corrected change in voting percentage as a function of WAR, there does appear to be a stronger correlation between WAR and percentage change this year (red and green squares) than seen last year (blue circles), although some correlation does exist.  The three points not falling near the correlation are Barry Bonds and Roger Clemons (PED history for otherwise certain hofs) and Lee Smith (reliever).  Going back further years shows a large scatter in terms of WAR and corrected percentage change, and it would be interesting to see how this has changed over all the different years and to see if the strength of this correlation has been increasing.  Furthermore, it would be interesting to see how this relates to a players other, more traditional metrics like home runs or wins.   

The green circles are players that have been a strongly association with PEDs.  Barry Bonds and Roger Clemons are exceptions, but the drop in the percentages for the other three players is in line for the drop for players with similar values of WAR.   Along with the average change in voting seen for Bonds and Clemons, it does not look like the behavior for players associated with PEDs is very different than other players.   

![png](hof_voters_files/hof_voters_31_0.png)

## Conclusions and other thoughts

The overall average change in vote percentage was almost exactly what was predicted based on the strength of the incoming class and the large number of Hall of Famers elected the previous year.   Along with the fact that percentages tend to increase relative to the average change for players with higher percentages, it does not look like there were any major changes to the voter patterns between this year and last year due to the *purge* of voters.


In terms of players that took PEDs, no major differences are detected in the voting patterns as compared to other players or the previous year.    

In terms of WAR, the percentage change for a player does seem to correlate with WAR and possible has become a stronger correlation.  

However, it should be noted that this is one year, a relatively small sample size, and that something very different could be occuring here. 

Relievers still are an exceptional case with Lee Smith having a very low WAR.  His vote percentage did decrease relative to the overall class and it will be interesting to see what happens to the three relievers (Trevor Hoffman and Billy Wagner along with Lee Smith) next year.   If Lee Smith is an example of how the new group of voters view relievers, we would expect to see all of their percentages drop relative to the average change, but it will be interesting as Trevor Hoffman is already very close. 

The player with the worst performance though was Nomar Garciaparra with a drop in voting percentage of -12% as compared to the average.  He was never associated with PEDs, and this was arguably expected due to being the lowest, second year positional player by WAR on the ballot.  On the other hand, the player with the largest increase, Mike Mussina, has the largest WAR of any player outside of Bonds or Clemons.  

As a final aside, Jeff Bagwell, Curt Schilling, and Mike Mussina are the only players in the last 20 years with no known associated with PEDs and WAR > 75 to not be elected, so far,  to the hall of fame.   Along with Phil Neikro and Bert Blyleven (and exlcuding Roger Clemons and Barry Bonds), these five players are the only players with WAR > 75 and not be elected on their first ballot in the last twenty years, whereas 13 other players with WAR > 75 were elected on their first ballot.  


### References

[A Jupyter notebook](https://github.com/crawfordsm/crawfordsm.github.io/blob/hof/_posts/hof_voters_files/hof_voters.ipynb) is available with all the code associated with the calculations in this post. 

This post used data download from [Baseball Reference](http://www.baseball-reference.com/).
