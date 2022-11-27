# IDS_Final_Project
***World Happiness Report / Index Analysis:***

**Question-**

The question we sought to answer is what effects do life expectancy, social support, and gross domestic product have on a population's average happiness?

**Hypothesis-**

We expect that an increase in all three variables (life expectancy, social support, and gdp) will result in a higher happiness score (life-ladder). We also expect to see a difference in importance of certain variables in some continents compared to others. For example, social support may contribute more to the population's overall happiness in Europe than in the Americas.

**The data-**

Our data set is the World Happiness Report. The original data set came with 12 variables and 2089 observations. The variables included were country name, 
year, life ladder, log GDP per capita, social support, healthy life expectancy at birth, freedom to make life choices, generosity, 
perceptions of corruption, positive affect, negative affect, and confidence in the national government. We then merged the data set with another that had a 
variable for continent so we could separate countries into their respective continents. After joining the two data sets, we did some data cleaning, 
primarily checking for name differences that resulted in the data not merging properly. We did a similar join to include data containing each country's GDP
since we wanted to use the actual GDP figures instead of the log(GDP) provided in our original data frame. We also filtered the data to include only the 
year we're interested in, 2011.

**Definition of variables-**

*life-ladder:* quantified the level of happiness on a scale of 1 to 10 (1 being the lowest and 10 the highest)

*life-expectancy:* the healthy life expectancy at birth

*social support:* having someone to count on in times of trouble (binary response of 0 (no) or 1 (yes))

*gdp:* gross domestic product for each country


**Method-**

Once we had the data filtered and split by continent, we plotted the variables life expectancy, social support, and GDP against life-ladder. We then ran 
linear regression models for all the plots and calculated the r-squared values. From the linear regression models, we primarily looked at the slopes 
associated with each variable for each and compared across continents to try and predict whether certain variables hold more significance in some parts
of the world than in others. We also made separate plots for each variable including all the data and color coordinated by continent and created lines of 
best fit for each continent so we could compare the slopes more easily. 

**Prediction Model-**

We also wanted to see if we could create a model that could predict a country's life ladder score. We split the 2011 data into a train and test set and used a linear regression model since logistic regression would not make sense in the case of our data. We made a recipe, workflow, fitted the data, and then created a prediction model that outputs a predicted life ladder score when given a country's life expectancy, social support, and gdp. Our prediction model performed pretty well with an r-squared of 0.815 (although a higher r-squared was expected given we fitted multiple variables) and an rmse of 0.5317. The rmse seems reasonably small considering that for the testing data the minimum was 2.9362	and the maximum 7.7882.

**Findings-**
