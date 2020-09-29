# PretermMetaproteomeGraphDB

Dockerized graph database as referenced in:

J. Alfredo Blakeley-Ruiz, Stephen K. Grady, Carissa Bleker, Michael A. Langston, and Robert L. Hettich (2020) *Highly connected metabolic networks and discriminatory reactions for necrotizing enterocolitis extracted from metaproteomics of preterm human infant gut microbiomes.* (forthcoming)

Feel free to create an issue with questions. 

## Data
Minimal data is kept in this repo. Files are avalible in the [Massive repository](https://massive.ucsd.edu/), identifier MSV000086096. 

## Set up

### Part 1: Neo4j Database

To create a copy of the graphDB on you own computer you will need [docker](https://docs.docker.com/) and [docker-compose](https://docs.docker.com/compose/). 

1. Clone this repo to your computer. 
    
       git clone https://github.com/UTKLangstonLab/PretermMetaproteomeGraphDB.git 


3. Build the neo4j container with the graph.  (It may take a few minutes to download the graph dump. )
    
       cd PretermMetaproteomeGraphDB
       docker build --tag proteomegraph .

3.  Run the image: 

       docker run -it  -p 7474:7474 -p 1337:1337 -p 7687:7687 proteomegraph
       
   And visit [http://localhost:7474/](http://localhost:7474/). 

### Part 2: Link the neo4j database to a Jupyter notebook

Start up the neo4j database and linked jupyter notebook with docker-compose. To run the first time, navigate to the folder (containing docker-compose.yml) and type:

       docker-compose up

   Thereafter you can use 

       docker-compose start

   To stop the containers, use:

       docker-compose stop

   Or to stop and remove them:
   
       docker-compose down
   
   Open your browser at the http://localhost:8888/?token=... link printed to the terminal. If the logs are not printed, run

       docker-compose logs | grep 'http://localhost:.*/?token' | tail -1 
 
   to find the correct link. 

#### To remove
If you need to remove the graph image. 

1. Remove the container: 

       docker-compose down

   Or get the container ID from the first column in:
      
       docker ps -a | grep proteomegraph
       
   And delete it using:

       docker rm <container ID>  

2. Delete the image:
    
       docker rmi proteomegraph

3. Delete the folder with the graph data (if it exists). 

       sudo rm -rf ~/neo4j/data/proteome/
