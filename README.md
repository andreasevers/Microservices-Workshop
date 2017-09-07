# Chapter 1: Refactoring to microservices
To understand what microservices are, we will start from a more comfortable project and tranform it to a distributed system. 
The process of transforming is a form of application modernization. Developers have been doing it for decades and as a result,
there are some ideas that we can reuse when refactoring a monolith into microservices.

## Strategy 1: Domain modeling
When Identifying the scope of our microservices, we look at the functionality a service needs to provide. 
Domain modeling is a core principle of designing loosely coupled microservices.
The goal is to ensure that each of your microservice is isolated from runtime side effects and insulated from changes in the implementation of another microservice in the system.
To help you defining the bounded context of your microservice, we extract what we expect from the functionality. 
Here are three questions that can help you with this exercise:

* Does one service need more instances(copy of a microservice) to receive more traffic than another?
* Does the user need to rely on a service to be up all the time than another service?
* Does one service changes data more often than another? 

### Exercise
Research and define the bounded context inside this project and write down why you would split it into different services.
When defined, check with your coach before you continue.
Now that we defined our bounded context, we can create for each bounded context a Spring Boot project.

* Go to [Spring Initializr](https://start.spring.io/)
* You can reference to the dependencies of this project for adding it to the new Spring Boot project.
* Generate the project and unzip
* Place the folder in your local git folder and open with Intellij

## Strategy 2: Each service has its own database
To have your own database for each service enables developers to use the type of database that is best suited for the service's needs. 
But it comes with more complexity by managing each database.
 
### Exercise
* Copy the code of the domain from the monolith in the proper service.
* Refactor the JPA entities so they are not coupled anymore.
* Replace the properties file with a yml file and configure the in memory database (H2)
* Configure the name of the application (We will be needing it later on)
* Configure a different port on each service
* Create the import.sql in each service and input the data you got from the monolith

## End Result
Run your services and go to your localhost:<port server>/<entities>
You should see a list of data in each service. 

### Next step
 ```sh
   git checkout chpt2-ServiceDiscovery
   ```













