# Analysing the wokeness of the film industry
___Study of the representation of ethnic diversity in the film industry___

## Abstract: 

<!-- A 150 word description of the project idea and goals. What’s the motivation behind your project? What story would you like to tell, and why? -->

The [*Oxford Learner's Dictionaries*](https://www.oxfordlearnersdictionaries.com/definition/english/woke_2) define **woke** as: aware of social and political issues, especially racism. Our society is slowly evolving towards a feeling of inclusion and equality for different social groups. This is reflected by an effort to give equal opportunities and representation to minorities  in the media. In this project we will put the focus on ethnic diversity in the film industry worldwide. For this goal, we will use the movie metadata from the November 4, 2012 dump of Freebase to compare the representation of different ethnicities in different countries of production, and study their evolution over time. Furthermore, we will try to explore the influence that this phenomenon has had on the success of movies in their respective countries, measured by their box office revenue. 

## Research Questions

<!--A list of research questions you would like to address during the project.-->

- How is ethnic diversity represented in each country's film industry? 
- How has this representation evolved over time?
- Is ethnic diversity related to (financial) success? 
- Is ethnic diversity different for actors and actresses? 
- <a name="thequestion">*Are certain ethnicities more prone to be cast for specific character types?* [See below](#addata)</a>


    
## <a name="addata">Proposed additional datasets</a>
The [data provided to us](https://www.cs.cmu.edu/~ark/personas/) contains a file named `tvtropes.clusters.tx` which contains 501 datapoints with information about different characters and their respective character types. However, this dataset is too small for us to perform any kind of relevant data analysis. With this in mind, we tried to use the [code](https://github.com/dbamman/ACL2013_Personas) provided in support of the work described in [Bamman, O'Connor and Smith, "Learning Latent Personas of Film Characters" (ACL 2013)](https://aclanthology.org/P13-1035.pdf). Nevertheless, at the time of writing, we have not yet obtained an operable dataset from this source. Therefore, we reserve the option to withdraw our [last research question](#thequestion) in case we are unable to obtain an appropriate dataset.
    
## Methods
    
#### **Part 0: Data cleaning (milestone2)**
The provided data is composed of five files: `character.metadata.tsv`, `movie.metadata.tsv`, `name.clusters.txt`, `plot_summaries.txt` and `tvtropes.clusters.txt`. From these, `character.metadata.tsv` (containing approximately 450 000 datapoints) has most of the data relevant for our research questions, since it partially contains the ethnicity information of the actors playing each character. We are only going to keep 9 features, as we decided that we would not use other features for our analysis. We will also drop all datapoints without a defined ethnicity. Furthermore, we only considered data before 2013, since our data was extracted from Freebase's November 4, 2012 dump. From this, we built two main datasets:
    
* **Dataset 1**: General dataset with features about each character (name, ethnicity, age, gender and movie date release). 

* **Dataset 2**: Character metadata merged with movie metadata on the wikipedia ID  (added features to the previous dataset with movie name, revenue, runtime, countries…) 

* **Dataset 3**: Non processed summaries of movie (containing wikipedia ID and summaries) 



#### **Part 1: First analysis and data visualization (milestone2)**
For this part, we produced a preliminary work on the datasets described above. We created a [jupyter notebook](https://github.com/epfl-ada/ada-2022-project-borroworrob/blob/main/main_milestone2.ipynb) containing various plots for the visualization of the data, such as:
    
- A histogram with the number of occurrences for each ethnicity 
- A timeline with the number of different ethnicities over time
- A distribution barplot of ethnicities in different countries
- A histogram counting the number of popular actors for each ethnicity 
- Boxplots of the revenue by country
- Scatter plot for 10 countries, average box office revenue versus number of movies
- Barplot of the average box office revenu for 10 countries
    

#### **Part 2: How is ethnic diversity represented in each country's film industry?**
After the primary analysis, we will start by computing ethnic diversity scores using entropy (USA). Then, we can start answering our first research question by producing an analysis on the countries or region that have generated the largest number of movies. For this purpose, we inted to use different models and statistical tests to extract information from our data.

#### **Part 3: How has this representation evolved over time?**
The next step is to explore the evolution over time of the results found in the previous step. We used the data between 1940 and 2012 to investigate statistically significant changes for this period of time using different quantitative analysis methods and visualisation. 
We also created an interactive map using plotly to compare the representation of different ethnicities in five countries over the year. It allows users to explore the data and see how the percentages of different ethnicities have changed over time.

#### **Part 4: Is ethnic diversity related to (financial) success?**
For our third question, we want to see if there is a causality link between ethnicity representation and the financial success of a movie. In order to do so, we are going to carry out an observational study of the successfull movies. 

#### **Part 5: Is diversity different for actors and actresses?
To determine a causal link between gender and ethnic diversity, we compare two datasets one with a majority of actresses and another with a majority of actors. Then we conduct an observational study and compute the linear regression. 

#### **Part 6: Are certain ethnicities more prone to be cast for specific character types?**
As mentioned in the [proposed additional data](#addata), if we are able to obtain a large dataset providing character type information for each character, we would like to investigate whether some character types are more readily assigned to particular ethnicities. In order to do so, we would start by mapping the character types to the ethnicities and quantifying them. Then, we would like to explore how other features like age, height or gender influence the results, and maybe do a PCA for the different features.
This section was withdrawn as we did not obtain a usable dataset.

#### **Part 7: Github site building and Datastory redaction.**

#### **Bonus:sentimental analysis over summary **
We did a sentimental analysis to pick up a correlation between ethnicity representation and sentiment on the summary.

#### **Bonus:movie genre and ethnic representation**
We also included a few plot for each gender film as well as their ethnic proportion. 

    
## Proposed timeline
    
- 18/11/2022: Submission of Project Milestone 2; Start working on Homework 2
- 25/11/2022: Working on Homework 2
- 02/12/2022: Submission of Homework 2; Start working on Project Milestone 3 
- 09/12/2022: Finish problem formulation and mathematics, start Github site 
- 16/12/2022: Finish code, works on the github site and start Datastory 
- 23/12/2022: Finish data story, Submission of Project Milestone 3


## Team organization

Dalil : Preliminary data analysis; Mathematical framework; Code work including figures
    
David : Problem formulation; Writing the report of the data story; Creating the website (interactive plots)
    
Johann: Classification of ethnicities in groups; Constructing the diversity score; Code work including figures
    
Melina: Group Leadership; Spokesperson; Problem formulation; Notebook work. 

