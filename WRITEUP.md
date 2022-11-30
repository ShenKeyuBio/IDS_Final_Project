# IDS_Final_Project
***World Happiness Report / Index Analysis:***

**Question-**

The question we sought to answer is what effects do life expectancy, social support, and gross domestic product have on a population's average happiness?

**Hypothesis-**

We expect that an increase in all three variables (life expectancy, social support, and GDP) will result in a higher happiness score (life-ladder). We also expect to see a difference in importance of certain variables in some continents compared to others. For example, social support may contribute more to the population's overall happiness in Europe than in the Americas.

**The data-**

Our data set is the World Happiness Report. The original data set came with 12 variables and 2089 observations. The variables included were country name, 
year, life ladder, log GDP per capita, social support, healthy life expectancy at birth, freedom to make life choices, generosity, 
perceptions of corruption, positive affect, negative affect, and confidence in the national government. We filtered the dataset to include only the variables we were interested in; year, life expectancy, and social support. We then merged the data set with another that had a 
variable for continent so we could separate countries into their respective continents. After joining the two data sets, we did some data cleaning, 
primarily checking for name differences that resulted in the data not merging properly. We did a similar join to include data containing each country's GDP
since we wanted to use the actual GDP figures instead of the log(GDP) provided in our original data frame. We also filtered the data to include only the 
year we're interested in, 2011.
In order to make use of the linear regression and prediction models later on, we had to standardize all of our data values (ie find their z-scores) so when we got coefficients later on, the numbers were comparable and we could make direct comparison between life expectancy, social support, and GDP values.


**Definition of variables-**

*life-ladder:* quantified the level of happiness on a scale of 1 to 10 (1 being the lowest and 10 the highest). We use "life ladder" and "happiness"                      synonymously throughout the presentation and the write up.

*life-expectancy:* the healthy life expectancy at birth

*social support:* having someone to count on in times of trouble (binary response of 0 (no) or 1 (yes))

*GDP:* gross domestic product for each country, measured in thousands of USD


**Method-**

Once we had the data filtered and split by continent, we plotted the variables life expectancy, social support, and GDP against life-ladder. We then ran 
linear regression models for all the plots and calculated the r-squared values. From the linear regression models, we primarily looked at the slopes 
associated with each variable for each and compared across continents to try and predict whether certain variables hold more significance in some parts
of the world than in others. 
We also made separate plots for each variable including all the data and color coordinated by continent and created lines of best fit for each continent 
so we could compare the slopes more easily. DESCRIBE PLOTS WITH CONTINENTS AND LINES

We also made a histogram to see the distribution of the life ladder variable. With a binwidth of 0.5, the distribution appears roughly bimodal with the higher mode being around 5 and the smaller one around 6.5 / 7. While the histogram is not symmetric because of the higher mode on the left, it is also not skewed either left or right.

**Prediction Model-**

We also wanted to see if we could create a model that could predict a country's life ladder score. We split the 2011 data into a train and test set and used a linear regression model since logistic regression would not make sense in the case of our data. We made a recipe, workflow, fitted the data, and then created a prediction model that outputs a predicted life ladder score when given a country's life expectancy, social support, and GDP. 

**Findings-**

*Linear Regressions:*

*Americas fit:* life-ladder-hat = 6.042 - 0.063(life expectancy) + 0.781(social support) + 0.437(GDP)
               R^2 = 0.6339
               
*Europe fit:* life-ladder-hat = 4.892 + 0.603(life expectancy) + 0.61(social support) + 0.348(GDP)
                 R^2 = 0.7397 -> 73.97% of the variation in happiness can be accounted for by the linear regression model of life expectancy, social                         support, and GDP on life ladder.
             
*Africa fit:* life-ladder-hat = 5.063 + 0.06(life expectancy) + 0.308(social support) + 0.541(GDP)
               R^2 = 0.4013 -> 40.13% of the variation in happiness can be accounted for by the linear regression model of life expectancy, social support,                 and gdp on life ladder. This R^2 is significantly lower than those for the other continents. Looking at the scatterplot, it can be seen                     that the data does not have a very strong linear trend.

*Asia fit:*   life-ladder-hat = 5.308 + 0.4(life expectancy) + 0.315(social support) + 0.429(GDP)
              R^2 = 0.6273 -> 62.73% of the variation in happiness can be accounted for by the linear regression model of life expectancy, social support,                 and gdp on life ladder.
           
*2011 fit:*   life-ladder-hat = 4.765e-01 + 3.573e-02(life expectancy) + 3.01e+00(social support) + 2.205e-05(GDP)
                R^2 = 0.6921 -> 69.21% of the variation in happiness can be accounted for by the linear regression model of life expectancy, social                          support, and gdp on life ladder.
           
Based on the slope coefficients from the linear regression models for each continent, we can see that life expectancy seems to have the biggest impact on life ladder in Europe and the smallest in the Americas. The Americas actually have a negative slope coefficient for life expectancy which implies that higher life expectancy results in lower happiness scores which does not make sense. We can also see that social support contributed the most to life ladder in the Americas, secondly in Europe, and then much less in Africa and Asia which have similar slope coefficients. When it comes to GDP, the slope coefficients are more similar across all continents than they were for the other variables. Africa has the highest of 0.541 and Europe had the lower of 0.348. We believe that these differences in the slope coefficients can be explained by cultural differences between the different continents. 
**TALK ABOUT 2011 MODEL**
**NOTE: MAYBE WE SHOULD BE LOOKING AT THE ADJUSTED R^2 BC WE HAVE MULTIPLE PREDICTORS**


*Prediction Model:*
Our prediction model performed pretty well with an r-squared of 0.815 (although a high r-squared was expected given we fitted multiple variables) and an rmse of 0.5317. The rmse seems reasonably small considering that for the testing data the minimum was 2.9362	and the maximum 7.7882.


**Limitations**
1) No data on countries in Oceania (except New Zealand and Australia) and limited data on countries in the Caribbean. 
2) No data on variables such as crime, travel, and others that we could have used.

**Future-**
MENTION T TESTS AND OTHER PLOTS
