#  Creating_a_data_warehouse_for_the_immigration_data

#### Project Summary
In this project I have the data in 2 different sources `sas` and `csv` formats.
Creating a data warehouse using `postgreSQL` it's capable of doing the job and there is more details about this in the data model
section.
performing cleaning process on the data befor inserting it on the data warehouse.
this data warehouse will be the final product of the project and the main purpos of it will be to answer the analytical queries 
like one to answer a question like if immigrants flock to states with generally more immigrants
i included a query to answer this in the end of the project to make sure that the data warehouse served its purpos
The project follows the following steps:
* Step 1: Scope the Project and Gather Data
* Step 2: Explore the Data
* Step 3: Defininge Data Model
* Step 4: Runing the ETL
* Step 5: Project Write Up


#### Scope 
the data comes in 2 different sources `sas` and `csv` formats.
we will know more about the data in the exploring section.
the goal of the project is to insert the data in a database resides in postgreSQL.

#### Describe and Gather Data 
we have 3 data sets
- I94 Immigration Data: This data comes from the US National Tourism and Trade Office.
- U.S. City Demographic Data: This data comes from OpenSoft.
- Airport Code Table: This is a simple table of airport codes and corresponding cities.

### Defining the Data Model
#### 3.1 Conceptual Data Model
the purpos of our porject is to build an analytical house and the best model for that is the `dimensional model`
our data model consists of 4 tables and for more details about the tables itselfs check the data dictionary

#### 3.2 Mapping Out Data Pipelines
- creating the database and the tables. 
- load the data into dataframes. 
- clean the dataframes.
- insert the data into the database


- in this project i used `pandas` to handle the small datasets and `spark` for the big ones and there is a reason to choose the 2 techs, in gerneral i use pandas dataframe to insert the data into postgresql and with the small datasets using pandas is a good choice and no need for spark cause the process is fast, but in the immigration dataset with this larg number of rows it's hard to process the data with pandas and if we run spark in distributed system it will be 100x faster.
- using `postgreSQL` for the database case it can handle about 9.7 millions rows and our data is much smaller, in general we need a releational database fo our dimintional model and according to the size of our data it's not nessessary to go to a cloud data warehouse, to avoid the unnessesary cost we could use `postgreSQL` and also `postgreSQL` has a much better query optimizer, vastly better join handling, and much more flexibility in querying in general than MySQL, which is a big advantage in an analytics environment such as a data warehouse.
- if The data was increased by 100x then we should us a map reduce tech to process the data in multiple nodes and I go for `redshift`
- if The data populates a dashboard that must be updated on a daily basis by 7am every day we should use airflow to schedule the task as we need
- if The database needed to be accessed by 100+ people movig to `redshift` can handle this problem.
