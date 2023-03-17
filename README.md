
## 🍺 The Beer project  🍺 

As it was shown in classes, graph databases are a natural way of navegating distinct types of data. For this first project we will be taking a graph database to analyse beer and breweries!   

_For reference the dataset used for this project has been extracted from [kaggle](https://www.kaggle.com/ehallmar/beers-breweries-and-beer-reviews), released by Evan Hallmark. Even though the author does not present metada on the origin of the data it is probably a collection of open data from places like [beeradvocate](https://www.beeradvocate.com/)_.

### Problem description

Explore the database via python neo4j connector and/or the graphical tool in the NEO4J webpage. Answer the questions. Submit the results by following the instructions


### Questions

1. How many different countries exist in the database?
1. Most reviews:  
    1. Which `Beer` has the most reviews?  
    1. Which `Brewery` has the most reviews for its beers? [Hint: 5-node path]
    1. Which `Country` has the most reviews for its beers? [Hint: 5-node path]
1. Find the user/users that have the most shared reviews (reviews of the same beers) with the user CTJman?
1. Which Portuguese brewery has the most beers?
1. From those beers (the ones returned from the previous question), which has the most reviews?
1. On average how many different beer styles does each brewery produce?
1. Which brewery produces the strongest beers according to ABV? [Hint: database has NaN values]
1. If I typically enjoy a beer due to its aroma and appearance, which beer style should I try? (Justify your answer well!) [Hint: database has NaN values]
1. Using Graph Algorithms answer **one** of the following questions: [Hint: make sure to clear the graph before using it again]
    1. Which two countries are most similiar when it comes to their **top 10** most produced Beer styles?
    2. Which beer is the most influential when considering beers are conected by users who review them? [Please use limit of 1000 on beer-review-user path]]
    3. Users are connected together by their reviews to beers, taking into consideration the "overall" score they review as a weight, how many communities are formed from these relationships? How many users has the biggest community? [Please use limit of 1000 on beer-review-user path]]
1. Using Graph Algorithms answer **one** of the following questions:
    1. Which beer has the most similar reviews as the beer `Super Bock Stout`? [Hint:inspect two subsets: with and without the beer in question]
    2. Which user is the most influential when it comes to reviews made?
1. If you had to pick 3 beers to recommend using only this database, which would you pick and why? (Justify your answer well!) [Hint: database has NaN values]


Questions 8 to 10 are somewhat open, which means we'll also be evaluating the reasoning behind your answer. So there aren't necessarily bad results there are only wrong criteria, explanations or execution. 
 
### Groups  

Groups should have 2 people.
You should register your group on **moodle**.

### Submission      

The code used to produce the results and respective explations should be uploaded to moodle. They should have a clear reference to the group, either on the file name or on the document itself. Preferably one Jupyter notebook per group.

Delivery date: Until the **midnight of March 13**

### Evaluation   

This will be 20% of the final grade.   
Each solution will be evaluated on 2 components: correctness of results and simplicity of the solution.  
All code will go through plagiarism automated checks. Groups with the same code will undergo investigation.




## Loading the Database

#### Be sure that you **don't have** the neo4j docker container running

The default container does not have any data whatsoever, we will have to load a database into our docker image:
- Download and unzip the `Neo4JHWData` file provided in Moodle.
- Copy the path of the `Neo4JHWData` folder of the unziped file, e.g. `C:/Users/nunoa/Desktop/Aulas/Big Data Management and Modelling/2023/HW1/Neo4JHWData/data`.
- Download and unzip the `Neo4JPlugins` file provided in Moodle.
- Copy the path of the `Neo4JPlugins` folder of the unziped file, e.g. `C:/Users/nunoa/Desktop/Aulas/Big Data Management and Modelling/2023/Neo4Jplugins`.
- Change the code bellow accordingly. As you might have noticed, you do not have a user called `nunoa`, please use the appropriate path that you got from the previous step. Be sure that you have a neo4j docker container running: \

`docker run --name Neo4JHW -p 7474:7474 -p 7687:7687 -d -v "C:/Users/nunoa/Desktop/Aulas/Big Data Management and Modelling/2023/Neo4Jplugins":/plugins -v "C:/Users/nunoa/Desktop/Aulas/Big Data Management and Modelling/2023/HW1/Neo4JHWData/data":/data --env NEO4J_AUTH=neo4j/test --env NEO4J_dbms_connector_https_advertised__address="localhost:7473" --env NEO4J_dbms_connector_http_advertised__address="localhost:7474" --env NEO4J_dbms_connector_bolt_advertised__address="localhost:7687" --env NEO4J_dbms_security_procedures_unrestricted=gds.* --env NEO4J_dbms_security_procedures_allowlist=gds.* neo4j`

- Since Neo4j is trying to recognize a new database folder, this might take a bit (let's say 3 minutes), so don't worry.
