P2: Project proposal and initial analyses

When you are done with Homework H1, you will continue to work on the next project milestone. In Milestone P2, together with your team members, you will agree on, and refine, your project proposal. Your first task is to select a project. Even though we provide the datasets for you to use, at this juncture, it is your responsibility to check that what you propose is feasible given the data (including any additional data you might bring in yourself), and to perform initial analyses.

The goal of this milestone is to intimately acquaint yourself with the data, preprocess it, and complete all the necessary descriptive statistics tasks. We expect you to have a pipeline in place, fully documented in a notebook, and show us that you have clear project goals.

When describing the relevant aspects of the data, and any other datasets you may intend to use, you should in particular show (non-exhaustive list):

    That you can handle the data in its size.
    That you understand what’s in the data (formats, distributions, missing values, correlations, etc.).
    That you considered ways to enrich, filter, transform the data according to your needs.
    That you have a reasonable plan and ideas for methods you’re going to use, giving their essential mathematical details in the notebook.
    That your plan for analysis and communication is reasonable and sound, potentially discussing alternatives to your choices that you considered but dropped.

We will evaluate this milestone according to how well these steps have been done and documented, the quality of the code and its documentation, the feasibility and critical awareness of the project. We will also evaluate this milestone according to how clear, reasonable, and well thought-through the project idea is. Please use the second milestone to really check with us that everything is in order with your project (idea, feasibility, etc.) before you advance too much with the final Milestone P3! There will be project office hours dedicated to helping you.

You will work in a public GitHub repository dedicated to your project, which can be created by following this link. The repository will automatically be named ada-2022-project-<your_team_name>. By the Milestone P2 deadline, each team should have a single public GitHub repo under the epfl-ada GitHub organization, containing the project proposal and initial analysis code.

P2 deliverable (done as a team): GitHub repository with the following:

    Readme.md file containing the detailed project proposal (up to 1000 words). Your README.md should contain:
        Title
        Abstract: A 150 word description of the project idea and goals. What’s the motivation behind your project? What story would you like to tell, and why?
        Research Questions: A list of research questions you would like to address during the project.
        Proposed additional datasets (if any): List the additional dataset(s) you want to use (if any), and some ideas on how you expect to get, manage, process, and enrich it/them. Show us that you’ve read the docs and some examples, and that you have a clear idea on what to expect. Discuss data size and format if relevant. It is your responsibility to check that what you propose is feasible.
        Methods
        Proposed timeline
        Organization within the team: A list of internal milestones up until project Milestone P3.
        Questions for TAs (optional): Add here any questions you have for us related to the proposed project.
    Notebook containing initial analyses and data handling pipelines. We will grade the correctness, quality of code, and quality of textual descriptions.

# Community Discovery among actors in the movie industry: A statistical and Temporal Analysis

## Abstract

Considerable study has been conducted on the subject of actors in the movie industry, but the bulk of it has focused on individual performers and their properties. We intend to accomplish something different through this project. We want to look at how various actors connect with one another and establish communities. In order to achieve this we will first create an actor co-occurence network which will allow us to trace the growth of actors and emphasize the global behavior of the movie industry. We then employ community detection algorithms to separate its moving parts. We'll investigate the temporal evolution of these communities to see how they change over time in terms of composition, how they relate to each other, as well as their evolution with respect to their statistical properties (based on the actors attributes e.g occupation, gender, age, etc. and the properties of movies where they cooperated e.g genre, rating etc.).

## Research Questions

1. Is it sound to assume that the rising stars of the movie industry are the ones who are most likely to be part of the largest communities? If so, how does this assumption hold up over time?

2. Do actors' country of citizenship along with the dominant genre of movies they cooperate in fully explain the communities that are formed? If not, what other factors are at play?

3. How do the communities evolve over time? Could the most noticeable changes be correlated to major global events?

## Proposed additional datasets

We will use a collection of scraping and query scripts to collect data from wikidata, potentially enriching it with data from IMDB. 

The data collected from wikidata includes:
- Actor's occupation: actor, director, producer, etc.
- Actor's country of citizenship
- Actor's discription (can be used to complete some missing values for gender and age)

## Data handling pipeline 

**(To be completed)**

## Methods

We will use the following methods:
- graph theory: to create the actor co-occurence network (nodes: actors, edges: number of movies they cooperated in)
(maths: https://en.wikipedia.org/wiki/graph_theory, **to be completed**)
- louvain algorithm: to detect communities in the network
(maths: https://en.wikipedia.org/wiki/Louvain_Modularity, **to be completed**)

## Proposed timeline

**(To be completed)**









