# Community Discovery Among Actors in the Movie Industry: A Statistical and Temporal Analysis

___Study on the underlying people's network dynamics in the cinema industry___

## Abstract

Considerable studies have been conducted on actors in the movie industry, but they mainly focused on individual performers and their properties. This project takes a different approach by analyzing how various actors connect with one another and establish communities. By creating an actor co-occurrence network, we can then employ community detection algorithms to cluster them by groups of actors recurrently playing in the same movies. We'll try to understand what characterizes the different subgroups, and whether actors regroup in homogenous communities or not. We'll focus on how actors relate to each other and the statistical properties of the community (based on the actors' attributes, e.g occupation, gender, age, etc. and the properties of movies where they cooperated, e.g genre, rating, etc.). We'll also investigate the temporal evolution of these communities to see how they change over time.


## Research Questions

1. Is it sound to assume that the rising stars of the movie industry are the ones who are most likely to be part of the largest communities? If so, how does this assumption hold up over time?

2. Do actors' country of citizenship along with the dominant genre of movies they cooperate in fully explain the communities that are formed? If not, what other factors are at play?

3. How do the communities evolve over time? Could the most noticeable changes be correlated to major global events?

4. On which factors is a community homogeneous (citizenship, language spoken) and on which is it not (actor's genre, age)? 

## Proposed additional datasets

We will use a collection of scraping and query scripts to collect data from wikidata, potentially enriching it with data from IMDB. 

The data collected from wikidata includes:
- Actor's occupations: actor, director, producer, etc.
- Actor's country of citizenship
- Actor's discription (can be used to complete some missing values for gender and age)

## Data handling pipeline 

**(To be completed)**

## Methods

**Step 1: Data scraping, pre-processing and dataset cleaning**

We are going to use 2 of the provided files: the *movie_metadata* dataset and the *character_metadata* dataset. We decide to include all the available years in our study (namely from 1888 to 2016, since the dataset includes previsionned movies). The main features we want for our study are :
- For the actors :

The first step is to clean the data by removing rows not including the needed features, and try to scrape missing values. We also convert certain columns to interpretable and uniform formats (dates are converted in years, etc). Some actor names are not written in english, but this should not impact the study as we do not plan on studying names within a community. 

**Step 2: Network creation and communities calculations**

For the network, we only keep pairs of actors that played in more than two movies together. Logically, the movies studied will only include those that have at least 2 actors. To reduce the size of the dataset, we only keep the movies with strictly more than 2 actors.
Each node of the network is an actor, and each edge between two actors describes their number of common movies. Thus, a single movie will generate multiple edges (in fact sum(1 at N-1) edges, where N is the number of actors in the movie). Then the communities are computed via the Louvain algorithm.

**Step 3: Characterize the actors within each communities**

For each communities, observe features such as citizenship, genre, occupation and birthdate. 

**Step 4: Characterize the movies within each communities**

For each community, observe features such as date of release, languages, genre. 

From the 2 previous steps, try to find overarching clustering feature(s) for each community. Does each community represent a specific country of geographical area, of a specific type of genre production ? Are the movie produced spread accross time, or does a community reflet only one or two decade of the movie industry ? Are actors of different ages ? 

**Step 5: Slice the analysis over time**
Perform a time analysis where we slice our network to only observe nodes and edges prior to the chosen year. For each community, how did it evolve over time? 

**Step 6: Make a beautiful story out of our findings**



We will use the following methods:
- graph theory: to create the actor co-occurence network (nodes: actors, edges: number of movies they cooperated in)
(maths: https://en.wikipedia.org/wiki/graph_theory, **to be completed**)
- louvain algorithm: to detect communities in the network
(maths: https://en.wikipedia.org/wiki/Louvain_Modularity, **to be completed**)

## Proposed timeline











