# BackEnd.NoSQL.InTheCloud
Module 5
---------------------------------------------------------

**Project description:** Non relational databases (or NoSQL), like they are sometimes called, have been gaining popularity in recent years. They differ from relational databases in the way that the relations between the data is not the main concern of the developer when creating the database. This causes data to be repeated and sometimes it can be hard to connect different datasets. On the other hand changing the data schema is much easier than in relational databases and there fore NoSQL has been gaining popularity in agile software development where things can change quickly and developers need to respond quickly to the changes.

To sum it up the for NoSQL:

**PROS:**

- Easy to change the schema "on the fly"
- More availability in the cloud (database as a service)
- Data is often stored as JSON

**CONS:**

- Data relation can become complicated
- The data might change so there is no promise that it will always look the way it does
- Lack of support in older software (legacy systems)
--------------------------------------------------------------

>I wrote some notes to understand the project little better.

MERN stack Tutorial from Ellert Smári: (https://ellertsmarik.medium.com/the-mern-stack-for-beginners-e607eb8b7100)

Source for notes: (https://www.mongodb.com/nosql-explained)

***What I need to go deeper into is: Playing around with the stack, add some things to the code like other routes, responding with JSON data.***
-----------------------------------------------------------
***How to make a RESTful API:***

**API = Application Programming Interface**
- For two computers to talk to each other
- Request ->> API <<- Response
-  Writing code to request data from a server instead of “clicking buttons”
- Most API’s in the world are RESTful

**RESTful API**
- Means they follow certain rules or constrains knows as Representational state transfer (coined in Roy Fielding’s 2000 PhD dissertation)
- RESTful API orginize data entities or resources into many unique URLs (technically URIs) 
- A client can get a data about a resource by making a request to that end point over HTTP. The start line contains the URI that you wish to excess
    - GET means you want to READ the data
    - POST means you want to CREATE a new resource 
    - PATCH is for UPDATEs
    - DELETE is for REMOVING data
    - And more .. -> HEAD, PUT, CONNECT, OPTIONS, TACE.
    
Below the start line we have:
- The HEADERS contains meta data about the request. (POST/dinosaur HTTP/1.1)
- ACCEPT header can tell the server you want the data in a specific format. (ACCEPT: application/json)
- AUTHORIZATION header can be used to tell the server that you are allowed to make that request ( <token> )
					
					POST/dinosaur HTTP/1.1
					ACCEPT: application/json (accept JSON)
					Authorisation: <token>
					Body: 					
                              {
					   “face”: “….”
					}

- Then after these headers we have the BODY, which contains a custom payload of data the server will receive the request massage and then execute some code usually to read from a database that can then be formatted into a response massage the top of the message contains a status code to tell the client what happened to their request.
        - Codes at the 200 level means that things went well, 
        - at the 400 level it means something was wrong with your request
        - At the 500 level it means that the server failed.
        
 					2** GOOD
					4** YOU MESSED UP
					5** SERVER BROKEN
      
 - After the status code we then have the response headers which contain information about the server that’s followed by the response body which contains the data payload and is usually formatted in JSON when talking about APIs

- Important part of this architecture is that it’s stateless.
        - Which means that the two parties don’t need to store any information about each other and every request response cycle is independent from all other communication and this leads to well-behaved rep applications that tare predictable and reliable.

- The most poplular framework for building RESTful APIs in node is express.js, it’s been around forever and it’s very minimal and easy to learn if you know a little bit of javascript.

**What is a NoSQL database?**
NoSQL database (aka “not only SQL”) are non-tabular database and store data differently then relational tables.  NoSQL database come in variety of types based on their data model. The main types are document, key-value, wide-column, and graph. They provide flexible chemise and scale easily with large amounts of data and high user loads.

When people use the term “NoSQL database” they typically use it to refer to any non-relational database. Some say the term “NoSQL” stands for “non SQL” while others say it stands for “not only SQL”. Either way, most agree that NoSQL databases are databases that store data in a format other then relational tables.

**Types of NoSQL databases:**
Over time, four major types of NoSQL databases emerged: document databases, key-value databases, wide-column stores, and graph databases.

 - **Document databases:** store data in documents similar to JSON (Javascript Object Notation) objects. Each document contains pairs of fields and values. The values can typically be a variety of types including things like strings, numbers, booleans, arrays, or objects.
 - **Key-value databases:** are simpler type of database where each item contains key and values.
 - **Wide-column stores:** store data in tables, rows and dynamic columns.
 - **Graph databases:** store data in nodes and edges. Node typically store information about people, places, and things, while edges store information about the relationships between the nodes.
	
  Link to learn more about different types of NoSQL Databases -> (https://www.mongodb.com/scale/types-of-nosql-databases)
  
**Why NoSQL?**
NoSQL databases are used in nearly every industry. Use cases range from the highly critical (e.g., storing financial data and healthcare records) to the more fun and frivolous 		(e.g., storing loT readings from a smart kitty litter box)

A variety of NoSQL databases exist. The most popular NoSQL database is MongoDB.

**Difference between a NoSQL and SQL database.**

Are also referred to as relational or non-relational. 
SQL stands for structured query language, It is a relational database. (Think Exel document)
NoSQL is non-relational databases. 


MongoDB is a document database. Instead of using tables rows and columns document databases store data in documents, specifically JSON, JavaScript object notation structured documents.  
		
            {
		“Key”: “value”
		}
    
When we have multiple values we can just use an array to define them [ ]. Data Accessed together stays together.


**Diffrent terminology differences in SQL and NoSQL**

          SQL:               NoSQL:
          - Cluster          - Cluster
          - Database         - Database
          - Table            - Collection
          - Row              - Document
          - Column           - Field


**MongoDB ecosystem:**

- Self-Hosted: this option will allow you to host your own MongoDB server on your hardware. This requires that you manage your server, updates and any other maintenance. You can download and use MongoDB open source community server on your hardware for free.
- Atlas: So if you don’t want to go the old school route of managing all of this on your own, you need MongoDB Atlas.  Atlas utilises a software as a service approach and is a global cloud database as a service for modern applications. With it you can deploy a fully managed MongoDB server across aws, Google Cloud and Azure with best in class automation and proven practices that guarantee availability, scalability and compliance with all of the most demanding data security and privacy standards.
- Compass: Is the GUI for MongoDB, it is available on linux, Mac or windows. It allows you to visually explore your data, run Ad Hoc Queries in seconds, interact with your data with full crud functionality, view and optimize your query performance and make smaller decisions about indexing, document validation and much more.
- Realm: with MongoDB Realm you can build better apps faster with edge to cloud sync and fully managed back-end services including trigger functions and graphql MongoDB Realm sync handles conflict resolution and networking code for you so you can build better mobile apps faster.
- Atlas Search: Makes it easy to build fast relevant full-text search capabilities on top of your data in the cloud available exclusively with MongoDB Atlas.  With search you’ll get: 
    * Leucine-powered search engine
    * Typo Tolerance
    * Auto-complete
    * Filter & Facets
    * Custom scoring
    * And much more….
- Charts: is a modern data visualisation tool that is integrated with the MongoDB cloud data platform. Charts is the quickest easiest and most powerful way to visualize MongoDB data or real-time insights, business intelligence and embedded analytics.
- Online Archive: You can tier your data across fully managed databases and cloud object storage and query it through a single endpoint automatically archive historical data and save on operational and transactional data storage costs without compromising on query performance.
- Data Lake: you can query and analyse data across aws s3 and mongoDB atlas in place in it’s native format, csv feels and other formats using the mogodb query language.

YouTube source: (https://www.youtube.com/watch?v=RGfFpQF0NpE)

**How to query a NoSQL database:**

Just like you had multiple ways to create a database, you have multiple options for querying a database: in the Atlas Data Explorer, in the MongoDB Shell, in MongoDB Compass, or using your favourite programming language.

In this section, you’ll query the database using the Atlas Data Explorer. This is a good way to get started querying, as it requires zero setup.

1. Navigate to the Data Explorer (the Collections tab), if you are not already there. See the official MongoDB documentation for information on how to navigate to the Data Explorer.

(The left panel of the Data Explorer displays a list of databases and collections in the current cluster. The right panel of the Data Explorer displays a list of documents in the current collection.)

![ktiqg2rcidp2r9mg2-image3](https://user-images.githubusercontent.com/89387153/148976021-ffa8b447-b619-4bde-8da0-f6a7237a0df9.png)
(The Data Explorer displays a list of documents in the listingsAndReviews collection.)

2. Expand the **sample_mflix** database in the left panel. A list of the database’s collections is displayed.
3. Select the **movies** collection. The Find View is displayed in the right panel. The first twenty documents of the results are displayed.
4. You are now ready to query the **movies** collection. Let’s query for the movie Pride and Prejudice. In the query bar, input {title: “Pride and Prejudice”} in the query bar and click **Apply**.

Two documents with the title “Pride and Prejudice” are returned.

![ktiqmvdaumzjbiw9c-image2](https://user-images.githubusercontent.com/89387153/148976044-b450f743-b51e-4d77-a5b3-1288388ef2a7.png)
(The results for querying for movies with the title “Pride and Prejudice”.)

Congrats! You’ve successfully queried a NoSQL database!






