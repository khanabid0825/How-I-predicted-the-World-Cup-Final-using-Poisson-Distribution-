# How I predicted the World Cup Final Using Poisson Distribution (Microsoft Excel)

INTRODUCTION: 
--------- 

There's hardly any competition in the world that comes any close to rival the suspense, the intensity, and the enthusiasm of a football World Cup, let alone surpass it. Just like all the previous tournaments that have been contested over a specific period of time with the sole pursuit to crown a World Champion, the latest edition of the FIFA World Cup had been nothing short of magic. The tournament attracted a lot of criticism from all over the world for reasons that demanded a fair debate, but as far as the football side of it was concerned, the World Cup did not fail any step of the way in delivering some of the most spell-binding football moments that will last a lifetime, specifically the very climactic stages.

![image](https://user-images.githubusercontent.com/123303003/215906135-bbf33d20-6cc7-4611-b8a0-30da0d840017.png)

With a successful addition of the very first major footballing tournament held in the Middle East, FIFA has now hosted a total of 22 World Cup tournaments. Like the graphical illustration above suggests, a total of 964 matches have been contested so far with a total of 2720 goals scored.

![image](https://user-images.githubusercontent.com/123303003/215906265-108a233d-e650-4ddc-aad3-11b76994a62f.png)

This year's FIFA World Cup ousted all other tournaments to record the highest number of goals scored in a single tournament. Football fanatics from all over the world tuned in to see Argentina and France, two respected football playing sides, go head-to-head in the final of the FIFA World Cup. The tournament came to a close with Argentina, led by Lionel Messi, dismissing all of France's heroic efforts to get their hands on the most coveted footballing prize on the planet. 

![image](https://user-images.githubusercontent.com/123303003/215906548-a1123988-c38a-4722-ae20-3661818af901.png)

ABOUT THE PROJECT: 
--
With the South American's side victory over France, they ended up joining Brazil and Italy as the only three nations to have won the final on penalties. Though many of the fans realized their long-awaited dream of seeing Argentina translate their hopes and dreams into a medal painted in gold - people like myself had been working nights and days to accumulate all possible data to predict the finals as accurately as possible. Predicting the outcome of a football match is always incredibly difficult; it is genuinely no flip of a coin. Even when personal sentiments coerce you to make allegiances with a specific side, you can never truly figure out how a certain match would play out until the referee has blown the final whistle. 

In my attempt to learn how to predict football matches with real-data, I made use of the Poisson Distribution model using Microsoft Excel. Brought forth by a genius-of-a-mathematician of the same name, Poisson distribution has been widely accepted as a very effective mathematical model in comprehending how a game just might play out. 

To model a Poisson distribution in Microsoft Excel, you can use the "POISSON.DIST" function. This function calculates the Poisson probability of a specified number of events occurring within a fixed interval of time or space, assuming a constant rate of occurrence.

           The syntax for the function is:
           POISSON.DIST(x, mean, cumulative)

Where:

"x" is the number of events for which you want to calculate the probability.
"mean" is the average number of events per interval.
"cumulative" is a logical value that specifies whether you want the cumulative distribution function (CDF) or the probability mass function (PMF). If "cumulative" is set to TRUE, the function returns the cumulative probability up to the specified number of events. If "cumulative" is set to FALSE, the function returns the probability of exactly the specified number of events.
Example:
To find the probability of exactly 3 events occurring in an interval with an average rate of 2 events per interval, you can use the following formula:
=POISSON.DIST(3, 2, FALSE)

The result is 0.180. This means there is a 0.180 or 18% probability of exactly 3 events occurring in an interval with an average rate of 2 events per interval.


FIRST STEP: EXTRACTING THE DATA FROM WEB USING MICROSOFT EXCEL
-
![image](https://user-images.githubusercontent.com/123303003/215907185-358ca285-cc75-4d02-82a8-39709eff0a94.png)
--

Since the outcome of the final is already known to us now, I used the data that I had directly acquired from https://www.transfermarkt.com/, https://en.wikipedia.org/wiki/2022_FIFA_World_Cup_squads, and https://fbref.com/en/ to check how accurately the model predicts the outcome.  After accumulation, all the data was cleaned and effectively altered using Microsoft Excel to sit well with the requirements of this analysis.


SECOND STEP: USING THE POISSON DISTRIBUTION FUNCTION

-->> Note: The data that I had accumulated to predict the final of the FIFA World Cup did not take into account the information of the 64th match of the tournament, i.e., the final. Also, since the matches were held in a neutral venue, adopting the home and away rule approach wasn't going to add any credibility to my analysis. After careful consideration, I went forward with the data I had accumulated on the average goals scored and conceded by both teams without taking into account their home and away performance. The table below gives you a brief idea on the total games played up until the huge Argentina-France clash as well as the total goals scored as well as conceded throughout the tournament.

![image](https://user-images.githubusercontent.com/123303003/215907468-617ba6f3-fdc3-460b-a023-b2b35015af56.png)


A) Calculating the average no of goals scored and conceded per game

Using the information present in the table, we can accurately calculate the average number of goals scored and conceded per game.  

                        Average number of goals scored = Total goals scored/Games played 

                         In our case, average number of goals scored per game = 166/63
                         
![image](https://user-images.githubusercontent.com/123303003/215907680-f5e3c010-4665-4779-bf02-dac0ac82efac.png)

In excel, the cells selected (G5 and G4) in the formula were used to derive the average number of goals scored per game. After dividing the  total number of goals scored (166) by the total games played (63), the average number of goals scored per game came out to be 2.63.

Similarly, the average number of goals conceded per game was also calculated in excel by dividing the number of goals conceded (164) by the total games played (63).

![image](https://user-images.githubusercontent.com/123303003/215907732-c15d65a7-d347-4eea-bfd4-6edb5858814d.png)

G6 divided by G4 gave me an average of 2.60 goals conceded per game. Using the same formula, I was able to calculate the average number of goals scored and conceded per game for each of the World Cup participant. Below is a graphical and tabular illustration representing the number of goals scored and conceded per game by each 2022 World cup participant.

![image](https://user-images.githubusercontent.com/123303003/215907849-773a4b16-c600-48f2-97c1-e0998d6b8d64.png)
![image](https://user-images.githubusercontent.com/123303003/215907874-6ee5e0bf-c88b-4e51-b981-9b079b341f3e.png)

Having figured out the average number of goals scored and conceded per game, the data I specifically cropped out of the above table for analysis was the average number of goals scored and conceded per game by the two World Cup finalists, Argentina and France. 

![image](https://user-images.githubusercontent.com/123303003/215907921-379ecfd3-ba91-407e-a5e3-ba449a5bd2d9.png)


![image](https://user-images.githubusercontent.com/123303003/215907948-09e242ca-70d2-4719-834c-418fafa4a382.png)


B) Calculating offensive and defensive strength

After deriving the average number of goals scored and conceded per game using the formula above, I used these numbers to further understand the defensive and offensive strength of the two final World cup teams. 

Calculating offensive strength:

The offensive strength of a team basically indicates a team's ability to make the most of its opportunities with the ball and score a goal. To calculate the attacking strength of a side,  I simply divided the team’s average number of goals scored per game by the average number of goals scored per game in the tournament.
                     
Calculating France's attack strength:

                                   In this case,

                         Average number of goals scored per game by France = 2.16

                        Average number of goals scored per game in the tournament = 2.63

                        Attacking strength of France = 2.16/2.63

                         = 0.82
                         
                         
Calculating Argentina's offensive strength:

Using the same formula above, Argentina's offensive strength came out to be 0.76



Calculating defensive strength:

Defensive strength is simply a team's capability to defend and stop its opponents from scoring. To calculate the defensive strength of a team, we simply divided the average number of goals conceded per game by a team by the average number of goals conceded per game in the tournament. 

![image](https://user-images.githubusercontent.com/123303003/215908273-71444a26-0dd3-4ef7-aabb-a84544f1463d.png)


![image](https://user-images.githubusercontent.com/123303003/215908300-96b0c717-9925-49c0-86da-a0743baf40b1.png)



C) Calculating Goal Expectancy

Now, to understand the goal expectancy, which translates into the number of goals a team is likely to score in a football game, I simply took either team’s offensive strength and multiplied it by its opponents’ defensive strength as well as the average number of goals scored in the tournament. Goal expectancy is a significant indicator in deciding which team is likely to get the most chances of scoring. 


![image](https://user-images.githubusercontent.com/123303003/215908355-e1101beb-513a-48d4-b293-d7ca099fee4a.png)


![image](https://user-images.githubusercontent.com/123303003/215908374-c5287f3f-c9e2-467e-90ee-5003c483de0f.png)


Having calculated the goal expectancy of both teams, I took all the necessary information I had acquired up until now to analyze the outcome of the final using the Poisson distribution model.

Like I mentioned above, Poisson distribution model is an effective probability function that analyzes the likelihood of a given number of independent events within a specific period of time. In this case, I have used the Poisson distribution function to understand the likelihood of France and Argentina scoring a specific number of goals. 

![image](https://user-images.githubusercontent.com/123303003/215908410-73497e9a-194d-4941-aeef-372bacc28422.png)

Since I used Microsoft Excel for predictive modeling, I made use of the expected number of goals France and Argentina can score per game into the Poisson Distribution function.

![image](https://user-images.githubusercontent.com/123303003/215908453-c34f38a3-b48f-4319-b094-4140b83f83a7.png)

An example of how I calculated the probability of both teams scoring a specific number of goals in the final using the statistical function in Microsoft Excel is given below. 
![image](https://user-images.githubusercontent.com/123303003/215908500-99c12a13-cee5-4ec4-880d-102f870a6144.png)

With the use of Poisson distribution, the probability of goals both teams are likely to score are presented in both tabular and graphical forms. 
![image](https://user-images.githubusercontent.com/123303003/215908529-c7e609a9-8227-476d-b8fb-ce8a9af603cc.png)

![image](https://user-images.githubusercontent.com/123303003/215908564-9b84836e-3a1c-470a-850e-be16df5c4f34.png)

Using findings to understand how the match would play out:

Now, to get each possible score using the findings uploaded above, I simply used Microsoft excel to multiply the probability of each possible score by France by the probability of each possible score by Argentina. After carefully executing the formula, I was able to acquire the following distribution you can see in the figure below.
![image](https://user-images.githubusercontent.com/123303003/215908634-935242bb-8b0c-48d0-9c56-aae611063b16.png)


Like you can see in the figure above, the chances of Argentina and France playing a 0-0 90-minute match would be the probability of France scoring 0 goals (0.58) multiplied by the probability of Argentina scoring 0 goals (0.54). Multiplication of the two probabilities gives us a 31% (0.31) chance of the match not being decided in the first 90 minutes. After doing the same for almost all scores possible within the specified number of intervals, the distribution above was compiled.

In excel, I used the sky blue color to highlight all the cells that would lead to France winning the World Cup final. On the other side, I used the green color to highlight all the findings that would lead to Argentina dethroning France from the very apex of national football. The yellow color in the cells have been used to define the likelihood of the outcome remaining undecided in the first 90 minutes. 

Calculating the estimated chances:

![image](https://user-images.githubusercontent.com/123303003/215908691-f1118fb3-e2ae-4874-b812-403a015a28be.png)


To calculate the estimated chances of France defeating Argentina, I simply added all the cells highlighted in sky blue from the table above. The estimated chance of France winning the world cup came out to be 0.26. Similarly, I calculated the estimated chances of an Argentina win by adding all the cells highlighted in green from the table above. The estimated chance of Argentina ousting France came out to be 0.30.

Since matches of this much promise and magnitude are pretty tight and intense, the likelihood of it not ending in 90 minutes was also needed to be calculated. For that, I added all the cells highlighted in yellow to calculate the estimated chance of the match heading into extra time. After calculation, the chance of the match not being decided in the first 90 minutes came out to be 0.43. 


![image](https://user-images.githubusercontent.com/123303003/215908736-0079f366-7f21-4929-8aa8-e5e387c6f537.png)


OBSERVATIONS:
--- 
Whilst one can never accurately predict the outcome of an event, the Poisson distribution model I used to analyze Argentina and France's chances of winning the FIFA World Cup did give me an idea that the match would likely end up being an even contest. With the help of Poisson distribution, the findings implied that Lionel Messi's side had a slight edge of ousting the defending champions in the finals of the World Cup.
![image](https://user-images.githubusercontent.com/123303003/215908843-26247303-e932-469f-a955-2d1ecf73a9e2.png)

The highest probability the Poisson distribution was able to register was a 31% chance of the match heading into extra-time. Even though both teams tested each other to the limits, the match eventually went into extra-time, some thing the Poisson distribution was able to predict before a ball inside Lusail stadium was even kicked. 

This is the very first time I have used the Poisson Distribution model for predictive modelling, and to my surprise, the findings weren't as inaccurate as I had first expected. You can always tweak the number of factors you want to consider to analyze which team has a better chance. 

Below is a dashboard I created on Power BI, displaying the distribution of all the 51 World Cup finalists with reference to different parameters.
![image](https://user-images.githubusercontent.com/123303003/215908898-7f949cd1-ddb4-4cf5-b538-e070c3dc30d5.png)















