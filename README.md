# Community Discovery Among Actors in the Movie Industry: A Statistical and Temporal Analysis

___Study on the underlying people's network dynamics in the cinema industry___


The notebook P3 contains the main bulk of the project , the notebook scraping was used to query from wikidata some additional features , the notebook exploration was used to generate the graphs that can be found in the website.
The csv files used in the notebook can be found in the folder CSV_files

## Abstract

Considerable studies have been conducted on actors in the movie industry, but they mainly focused on individual performers and their properties. This project takes a different approach by analyzing how various actors connect with one another and establish communities. By creating an actor co-occurrence network, we can then employ community detection algorithms to cluster them by groups of actors recurrently playing in the same movies. We'll try to understand what characterizes the different subgroups, and whether actors regroup in homogenous communities or not. We'll focus on how actors relate to each other and the statistical properties of the community (based on the actors' attributes, e.g occupation, gender, age, etc. and the properties of movies where they cooperated, e.g genre, rating, etc.). We'll also investigate the temporal evolution of these communities to see how they change over time.


## Research Questions

1. Is it sound to assume that the rising stars of the movie industry are the ones who are most likely to be part of the largest communities? If so, how does this assumption hold up over time?
To answer this question the idea was to define a “rising star” as an actor who shows a sudden surge in a given centrality metrics. <br><br>

Centrality measures are used to identify the most important nodes in a graph based on the connections they have to other nodes. In this case, the nodes would be actors and the edges would be movies they have acted in together.<br><br>

One centrality measure that could be used to identify rising stars is degree centrality, which is a measure of the number of connections a node has to other nodes in the graph. Actors who suddenly appear in a large number of movies with other actors could be considered rising stars based on this measure.
Another centrality measures that could be used include closeness centrality, which measures the average distance from a node to all other nodes in the graph, and eigenvector centrality, which measures the influence of a node based on the influence of its neighbors.<br><br>
So is possible to define a "rising star" as an actor who shows a sudden surge overtime on a given metric. In this case, it would be needed to track the value of the metric over time for each actor and look for sudden spikes or increases in the value of the metric. However, It was rather difficult to identify a clear definition of a "sudden surge" that is suitable for all actors and metrics. Different actors may have different baseline level of importance within a community, making it challenging to define a universal threshold for what constitutes a "sudden surge". Ultimately we decided to drop this question and focus on more meaningful pursuits.

2. Do actors' country of citizenship along with the dominant genre of movies they cooperate in fully explain the communities that are formed? If not, what other factors are at play?

3. How do the communities evolve over time? Does gender parity improves over the lifespan of communities  ? 

4. On which factors is a community homogeneous (citizenship, language spoken) and on which is it not (actor's genre, age)? 
The goal of this question is to try to determine what links actors of the same communities , do actors who work together share the same features ? 

## Proposed additional datasets

We will use a collection of scraping and query scripts to collect data from wikidata, potentially enriching it with data from IMDB. 

The data collected from wikidata includes:
- Actor's occupations: actor, director, producer, etc.
- Actor's country of citizenship


## Methods

**Step 1: Data scraping, pre-processing and dataset cleaning** <br>
We are going to use 2 of the provided files: the *movie_metadata* dataset and the *character_metadata* dataset. We decide to include all the available years in our study (namely from 1888 to 2016, since the dataset includes previsionned movies). The main features we want for our study are :
- For the actors : gender, date of birth, nationality, occupations
- For the movies : date of release, genres, languages


The first step is to clean the data by removing rows not including the needed features, and try to scrape missing values. We also convert certain columns to interpretable and uniform formats (dates are converted in years, etc). Some actor names are not written in english, but this should not impact the study as we do not plan on studying names within a community. 

**Step 2: Network creation and communities calculations** <br>
For the network, we only keep pairs of actors that played in more than two movies together. Logically, the movies studied will only include those that have at least 2 actors. To reduce the size of the dataset, we only keep the movies with strictly more than 2 actors.
Each node of the network is an actor, and each edge between two actors describes their number of common movies. Thus, a single movie will generate multiple edges (in fact $\sum_{1}^{N-1}$ edges, where N is the number of actors in the movie). Then the communities are computed via the Louvain algorithm.
=======
The first step is to clean the data by removing rows not including the needed features. We also convert certain columns to interpretable and uniform formats (dates are converted in years, etc). Some actor names are not written in english, but this should not impact the study as we do not plan on studying names within a community. 

**Step 2: Network creation and communities calculations** <br>
For the network, we only keep pairs of actors that played in more than two movies together. Logically, the movies studied will only include those that have at least 2 actors. To reduce the size of the dataset, we only keep the movies with strictly more than 2 actors.
Each node of the network is an actor, and each edge between two actors describes their number of common movies. Thus, a single movie will generate multiple edges (in fact $\sum_{1}^{N-1}$ edges, where N is the number of actors in the movie). Then the communities are computed via the Louvain algorithm. We will then use the communities populations to query actors country of citizenship and occupations from Wikidata . We only query these features for the actors of the top 20 communities for time constraints. The scraping and querying is done in the "scraping.ipynb" notebook.


**Step 3: Characterize the actors within each communities** <br>
For each communities, observe features such as citizenship, genre, occupation and birthdate. 

**Step 4: Characterize the movies within each communities** <br>
For each community, observe features such as date of release, languages, genre. 
From the 2 previous steps, try to find overarching clustering feature(s) for each community. Does each community represent a specific country of geographical area, of a specific type of genre production ? Are the movie produced spread accross time, or does a community reflet only one or two decade of the movie industry ? Are actors of different ages ? 

**Step 5: Slice the analysis over time** <br>
Perform a time analysis where we slice our network to only observe nodes and edges prior to the chosen year. For each community, how did it evolve over time? 
For a certain time slice , we observe only the actors who played roles until that time and observe how the feature distribution in communities evolve . We expected for example to see more women playing in movies as years go by.

**Step 6: Make a beautiful story out of our findings**



## More details about the network methodology 

We will use the following methods:
- graph theory: to create the actor co-occurence network (nodes: actors, edges: number of movies they cooperated in)
(maths: https://en.wikipedia.org/wiki/graph_theory, **to be completed**)
- louvain algorithm: to detect communities in the network
(maths: https://en.wikipedia.org/wiki/Louvain_Modularity, **to be completed**)

### Graph theory: 

- A graph is a mathematical structure that consists of a finite set of vertices (or nodes) and a finite set of edges (or links) that connect pairs of vertices. We will use graphs in in order to model the actor co-occurence network.
- Mathematically, a graph is defined as a pair **G** = (**V**, **E**) where **V** is a set of vertices and E is a set of edges. Each edge is a pair of vertices (**u**, **v**) where **u** and **v** are distinct vertices. In the context of our project, the nodes will be the actors and the edges will represent if the actors have cooperated in a movie. The weight of the edge will be the number of movies they have cooperated in.
- In graph theory a degree of a node is the number of edges incident to it. In our case, the degree of a node will be the total number of movies the actor has cooperated in(movies can be counted multiple times if the actor has cooperated in them with multiple actors).
- The adjacency matrix of a graph is a square matrix whose entries are defined by the adjacency relation. In our case, the adjacency matrix will be a matrix of size **n** x **n** where **n** is the number of actors. The entry in the $i^{th}$ row and $j^{th}$ column will be the number of movies the $i^{th}$ actor has cooperated in with the $j^{th}$ actor. The diagonal of the matrix will be the degree of each actor.
### Louvain algorithm: 

- The complexity of the community detection problem stems from the vague definition of a community. In order to overcome this, we will use the louvain algorithm which is a fast and accurate community detection algorithm. It is based on the modularity maximization principle which states that the best partition of a network is the one that maximizes the modularity of the network. The modularity of a network is a measure of the density of edges within communities compared to the density of edges between communities.

- Mathematically, the modularity of a partition of a graph **G** = (**V**, **E**) is defined as:
    - $Q = \frac{1}{2m} \sum_{ij} \left[ A_{ij} - \frac{k_i k_j}{2m} \right] \delta(c_i, c_j)$ where 
        - $A_{ij}$ is the adjacency matrix of the graph
        - $k_i$ is the degree of the $i^{th}$ node
        - $m$ is the total number of edges in the graph
        - $\delta(c_i, c_j)$ is 1 if the $i^{th}$ and $j^{th}$ nodes belong to the same community and 0 otherwise
        - $c_i$ and $c_j$ are the communities to which the $i^{th}$ and $j^{th}$ nodes belong to respectively
    - Based on the above equation, the modularity of a community **c** can be calculated as:
        - $Q_c = \frac{\sum_{in}}{2m} - (\frac{(\sum_{tot})}{2m})^2$ where
            - $\sum_{in}$  is the sum of edge weights between nodes within the community 
            - $\sum_{tot}$ is the sum of all edge weights for nodes within the community


        

- The Louvain algorithm is a greedy algorithm that iteratively improves the modularity of the network by moving nodes between communities. The algorithm is based on the following steps:

1. Assign each node to its own community.
2. While modularity can be increased:
    1. For each node, calculate the increase in modularity if the node was moved to each of its neighboring communities.
    2. Move the node to the community that maximizes the increase in modularity.
3. Return the communities.

- It is worth mentioning that the Louvain algorithm is a heuristic algorithm and does not guarantee to find the optimal partition of the network. The randomisation of the algorithm can lead to different results each time it is run. In order to overcome this, for simplicity, we ran the algorithm multiple times and taking the partition that maximizes the average modularity of the respective communities or potentially comparing multiple community discovery algorithms according to the same principle.





## Team organization

- Ahmed : scrapping, data processing, time slicing, map visualization
- Aziz : scrapping,  network time analysis, communities characterization , notebook organization
- Loïc: organize meetings, network visualization, inter-communities relationships, website
- Solène : network visualization, data story, network movies analysis, website