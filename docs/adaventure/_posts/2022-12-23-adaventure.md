---
layout: post
title: The Adaventure
description: >
  Main page of our adaventure.
hide_description: true
redirect_from:
  - /download/
---


# The Adaventure

The [*Oxford Learner's Dictionaries*](https://www.oxfordlearnersdictionaries.com/definition/english/woke_2) define **woke** as: aware of social and political issues, especially racism. Our society is slowly evolving towards a feeling of inclusion and equality for different social groups. This is reflected by an effort to give equal opportunities and representation to minorities  in the media. In this project we will put the focus on ethnic diversity in the film industry worldwide. For this goal, we will use the movie metadata from the November 4, 2012 dump of Freebase to compare the representation of different ethnicities in different countries of production, and study their evolution over time.

1. this list will be replaced by the toc
{:toc .large-only}

## Data Overview

In this project, we are going to work on the representation of the ethnicity in movies from different datasets. We have approximately 450 000 characters aligned in the file `'character.metadata.tsv'` which was extracted on November 4, 2012 from freebase. It is the main data that we are going to use, as it contains the ID of the ethnicity. We are only going to keep 9 features, as the other features are not useful for our analysis. We will also drop the characters with unspecified ethnicity. Data after 2012 will be removed as our data is extracted from 1920 to 2012 and we don't have enough movies for 2012. 

From an initial exploration of the data, we could see that the dataset contains 476 different ethnicities, with the first few representing the vast majority; many ethnicities have only one actor in the dataset. Because the distribution is heavy tailed, ethnicities are represented below with a log axis.

![Ethnicities Occurrences](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/1.png)
Barplot showing the occurrence of different ethnicities in a log scale.
{:.figcaption}

### Proportion of different ethnicities over time

After cleaning our dataset, we started by plotting the evolution of the total number of ethnicities present in movies over the years.

![Number of eth over time](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/2.png)


### Number of movies by country over time
If we want to extract meaningful information from our data, we must first take into account different aspects and biases. In order to explore the 

> ***NOTE :***
First, we will examine the number of films produced in the two major film producing countries: `India`  and the `United States`. 

![Evolution of number of movies for different countries](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/3.png)

---
**Conclusion**

The timeline is not good because we can see that Indian movies are only represented after 1930, and they are also much less present in the dataset until 1960-1970. Thus, we can try to look at the data after56 1970.

![Evolution of number of movies](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/4.png)

---

---
**Conclusion**

We have a much better representation of the data set after 1970, with the same proportion of Indians and Americans in each period; we will use this time frame for the rest of our analysis. 

---

## How is ethnic diversity represented in each country's film industry<a name="paragraph3"></a> 
Looking deeper in the dataset for various geographic areas : `US`, `China`, `India`,`Europe`. 


### China

Unfortunately, our dataset didn't contain enough movies produced in China to extract any significant conclusions.

### USA

![Ev of rep usa](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/6.png)

Black and white populations appear to be increasingly represented in the film industry. However, the overall number of actors per film is increasing.

> ***NOTE :***
To determine the true trend in ethnic representation in the movie industry, we will normalize the number of actors by ethnic group by the total number of actors.

![Ev of rep of eth usa](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/7.png)

---
***Conclusion***

The results are quite surprising: while white actors are less represented over time, while black actors are more represented, but not significantly so. Others ethnic groups doens't appear to be more represented over time. Why does it not add up to 1? People of mixed race are not taken into account. Conclusion: Things are improving, with more black and mixed ethnicities are being more represented. Asian not so much, despite the large Chinese diaspora.

---


### India

![Ev of rep eth india](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/8.png)


![Ev of rep of soas](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/9.png)

### Europe

![Evo of rep eu](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/10.png)

Taking europe as a whole, we can observe a very strong representation of white people. Perhaps better to look at each country indivudually and look at ethnicity and not groups.

![Evo of rep eu](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/10_.png)

> **NOTE :**
We will look more closely to the 3 countries with more movies : `UK`,`France`,`Germany`.

#### UK

![Evo of rep uk](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/11.png)


#### France


---
**Conclusion**

There is a much better representation with a quite a good proportion of Americans actors and jewish people but the rest are mainly from neighbour countries. 

---

#### Germany

---
**Conclusion**

Surprisingly, a large number of African Americans. There isn't much German. Many ethnicities are represented, including neighboring countries as well as American countries. The dataset appears to be highly flawed.

---

### Top 100 movies

We chose to look at the 100 most famous movies based on the dataset's column **`revenue`** to examine them in greater depth. Then we will examine the countries that produced the films, as well as the ethnic representation in terms of ethnic group and overall.


Clearly, the United States has the most movies and the highest revenue, followed by India and the United Kingdom. We will now look at the top movies.

![Proportion of actors for each eth](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/12.png)

---
**Conclusion**

Because the top countries are mostly made up of Americans, the ethnic representation is quite skewed. As before, there is a large representation of white. There are many ethnicities, but they are not well represented. Black people appear to be more represented than other ethnic groups, with the exception of white people.

---



## Diversity score

One of the key goals of our project is to quantify the `ethnic diversity` present in our dataset. To achieve this, we need to find a metric or score that will allow us to determine the extent to which different ethnicities are represented in the data we are analyzing. This will help us understand the level of diversity within the dataset and identify any potential imbalances or disparities.

### Entropy score

Entropy is a measure of randomness or disorder within a system. In the context of ethnic diversity, entropy can be used to quantify the degree of variety within a population with respect to ethnicity.

To calculate the entropy of a population with respect to ethnicity, we used the following formula:

**Entropy = - ∑(pi * log2(pi))**

where pi is the proportion of individuals in the population belonging to each ethnic group. The sum is taken over all ethnic groups present in the population.

Using this formula, we will calculate the entropy of a population and compare it to other populations to assess the level of ethnic diversity. A population with a higher entropy would indicate a greater degree of ethnic diversity, while a population with a lower entropy would indicate less ethnic diversity.


![Entropy usa](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/13.png)


---
**Conclusion**

The entropy is quite high from 1920 to 1940, indicating a really high variability, but as previously stated, our dataset is primarily composed of movies from 1970 to 2010, so this variability is most likely explained by the low number of movies.  
After 1960 the entropy is clearly increasing indicating evermore diversity.

---


### Simpson index


The Simpson index is a measure of diversity within a population that takes into account both the number of different ethnic groups present and the relative proportions of each group. It is calculated using the following formula:

**Simpson Index = 1 - ∑(pi^2)**

where pi is the proportion of individuals in the population belonging to each ethnic group. The sum is taken over all ethnic groups present in the population.

The Simpson index ranges from 0 (complete uniformity, with all individuals belonging to the same ethnic group) to 1 (complete diversity, with each ethnic group represented equally). A population with a higher Simpson index would indicate a greater level of ethnic diversity, while a population with a lower Simpson index would indicate less ethnic diversity.

The Simpson index is useful for quantifying ethnic diversity because it takes into account both the number of different ethnic groups present and the relative proportions of each group.

![Simpson entropy usa](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/14.png)


---
**Conclusion**

Looking at the data, we can see that overall diversity is increasing over time, with a particularly strong increase from 1920 to 1925 and a slower increase until 2000. There is a noticeable decrease in diversity around 1975. This diversity score seems more realisatic showing more diversity over time in the movie industry with less variation than the entropy score.  

This score will be used in the following analysis because it is a good index for diversity as it takes into account the number of data points in each year.

---


> **NOTE :**
We will first group all of the movies by their wikipedia ID to calculate the diversity score of their actors, and then we will conduct an analysis to see if there is more diversity over time, as diversity representation is a hot topic these days, and we expect to see more diversity in western movies: Europe, USA, Canada...

**1. Calculate the diversity score**

First we have to calculate for each movie the diversity score (simpson) using actors `ethnicities` in each movies.

    
**2. Conduct a statistical test to determine whether there is a statistical difference between the different time periods**
   
Then we will run a statistical test on all of the dataframe's periods. To group movies by periods and have enough data, we will choose data from 1940 to 2010 and place each movie in a 10-year period.

    
**3. Create a heatmap with the p values for each period** 

We will store all of the p values in a 2D matrix (same period for the 2 entries) and generate a symetrical heatmap to show whether the p value is low or high, allowing us to determine whether the divergence is statistically significant.


#### T-test for different time periods

To begin, we must change the date to obtain all movies from a 10-year period in only one category, and then we will calculate the diversity score for each movie, excluding movies with fewer than four actors.

![Distrib of simp](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/15.png)

As our distribution is not normal we will use the **Kruskal-Wallis** test. It is a non-parametric statistical test that will be used to compare the diversity of ethnicities in different periods of time. It is commonly used when the data are not normally distributed or when the assumptions of other parametric tests, such as the one-way ANOVA, are not met.

Next, you will use the Kruskal-Wallis test to determine whether there is a statistically significant difference in the diversity of ethnicities between the different periods of time. To do this, we will calculate the test statistic called the H-value.

If the H-value is found to be statistically significant at a predetermined level of significance (0.05), it suggests that there is a significant difference in the diversity of ethnicities between the different periods of time. If the H-value is not statistically significant, it suggests that there is no significant difference in diversity between the periods.



#### Heatmap of p_value diversity for each period


![Weird heatmap](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/16.png)

---
**Conclusion**

Because we are comparing the same values, it is obvious that it is a simetrical matrix; additionally, the p value for the t test comparing the same data in the diagonal is 1 because there is no difference at all. It was to be expected. Other findings are more surprising, and they can be investigated using a confidence interval and mean ethnic score for each period to determine whether diversity is increasing or decreasing over time. 
Surprisingly, the p value is high between 1940 and 2000, implying that the null hypothesis is not rejected and that diversity is not significantly different between these two periods; the same conclusion is reached for 1950, 1980/1990, but also 1970/1960 and 2010. A more detailed analysis is provided below.

---

#### Mean diversity score for each period

![Div score overtime](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/17.png)

---
**Conclusion**

The data show a quite interesting story, overall looking at the entire dataset we cannot say really that diveristy increases for actors in movies as there is not a real difference between 1960/1970 and now but we can say that since 1990 diveristy increase significaly (looking at the p_values that are pretty low and indicate a significant difference in diversity). To understand the data and its variability better we could show the diversity for different countries, we could try to do the same analysis but for USA, India and Europe. 

---

## Correlation between success and actor ethnic diversity

We can look at the more successful films and their ethnic diversity to get a better understanding of ethnic representation in the film industry. To begin, we must define a successful movie. Because only 28% of the datasets have box office revenue, we define a successful movie as having at least two famous actors in the cast.

![Number of actors per movie](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/18.png)

The majority of actors have appeared in fewer than 100 films, as can be seen. We will use an arbitrary success threshold and define the most famous actors as the 5% with the most films. A film is considered successful if it features more than two famous actors.

![Number of movies - tf is this plot](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/19.png)


We can already tell just looking at the data that we have different data for famous and non famous movies, as checked before we have a similar number of movies for the two dataset but we have different number of countries producing: 90 different countries for the non_famous and 50 for the famous one. Again looking in more detail we can see difference in the movies producing famous or non famous countries. 


![Pieplot?](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/20.png)

As expected the famous movies are more present in US, India and Europe, we also have a good number of data for the Canada. As we have outliers like the United State of America and the distribution is more a distribution we used a log axis for the number of famous movies. Now we will look more into the ethnic diversity in these famous overall and in the main countries producing these movies. 


![Another weird pieplot](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/22.png)

Now to have a real estimation of the diversity and if there is a difference in ethnic representation for movie with success and without it, we will do an observational study by finding for each successfull movie an non successful one, for that we will look at different criterias. First the country movie has to me matched, secondly the year of production obviouly as to match maybe not the exact same year but we will do it 5 years by 5 years. Lastly the number of actors playing in the movie has to be similar to obtain a significant result. For that we will match cast that have more or less the same number of actors in 2 actors difference. After the matching we will use a linear regression to see if there is a difference in the ethnic diversity by printing a linear table of the diversity score for the two groups (successfull and non successfull movies). 
To understand a score and show diversity, we will calcularte the ethnic diversity with simpson's diversity index.

### Linear regression

![Linear regression plot](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/23.png)

---
**Summary linear regression**

The intercept 0.4713 is the mean outcome for the simpson index representing diversity for famous movies (x=0). The slope 0.08 is the difference in mean outcomes between the diversity index for x=1 (non_successfull movies) and x=0. It means that for famous movies the diversity of the actors playing in it is superior by 0.08 than for actors playing in non famous movies. Thus, there is a significant difference in diversity between the two groups of movies. To validate this conclusion, we can look at the p value, which is very low. The null hypothesis is rejected: there is a significant difference in diversity for famous or non famous movies.

---

## Correlation between gender and actor diversity

### Visualization of gender proportion

Gender as ethnicity is a big subject for the society nowedays, we will look at the ethnic diversity and if there is a difference in representation between man and female. First we will just look at a few datas on the gender and how they are represented in the datas we have. 


![Yet another plot](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/25.png)

We can see a slow increase in the number of females in movie casts; however, a strange data point is represented around 1930 with a better percentage of actresses. Again, to examine the gender diversity representation, we will conduct an observational study, pairing one film with a majority of actresses and another with a majority of actors:


1. Match the number of actors
2. Match the period of the movie release
3. Match the country of production
4. Diversity score calculation for actors in the cast
5. Linear regression
    
    
![YAP2](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/26.png)

We can deduce from the plot that a large portion of the movies lack diversity (all of the actors in the cast are the same ethnicity), which is more prevalent in films with a majority of female actors in the cast. As a result, the average diversity for female-majority films is lower. However, the observational study found that the difference in ethnicity between the two datasets is not statistically significant.


## Sentimental analysis

### Score on summary

Using the sentimental analysis, we will only look at data movies with more than 4 actors in it. For this, we are looking at sentiment scores depending on number of groups.


### Linear regression

![Second weird lin reg](https://raw.githubusercontent.com/epfl-ada/ada-2022-project-borroworrob/main/docs/figures/27.png)

---
**Summary linear regression**

The R-squared value of 0.008 indicates that the model explains a small portion of the variance in the dependent variable (sentiment score). The adjusted R-squared value of 0.007 is similar, and indicates that the model accounts for a small amount of the variance in the dependent variable after accounting for the number of variables in the model. The F-statistic and its corresponding p-value of 40.82 and 1.81e-10, respectively, indicate that the model as a whole is statistically significant. We can see that the mean of each groups is nearly the same. We can infer that the diversity of a movie doesn't influence the the sentiment score based on summaries (small variation. decrease by 0.0145 per unit).

---

## Conclusion

It is generally agreed upon that the representation of various ethnicities in the movie industry has not been particularly fair. Many people from marginalized groups, including people of color, LGBTQ+ individuals, and people with disabilities, have historically been underrepresented and often portrayed in stereotypical or negative ways in films. This lack of fair representation can have a significant impact on the way that these groups are perceived and treated in society. It can also limit the opportunities available to actors and filmmakers from these groups to tell their own stories and be recognized for their talents.

There have been some efforts in recent years to improve representation in the movie industry, but there is still a long way to go. Many people believe that more needs to be done to promote diversity and inclusion in all aspects of the movie industry, including in the stories that are told, the actors who are cast, and the filmmakers who are given the opportunity to make films. Overall, it is important for the movie industry to reflect the diversity of the world in which we live and to give equal opportunities to all people, regardless of their ethnicity or other identities.
