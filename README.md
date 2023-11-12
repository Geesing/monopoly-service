# CS 262 Monopoly Webservice

This is the data service application for the 
[CS 262 Lab 8 Monopoly Project](https://github.com/Geesing/cs262/tree/main/lab07),
 which is deployed here:
          
- <https://jgc-monopoly-service.azurewebsites.net/>

It has the following read data route URLs:
- `/` a hello message
- `/players` a list of players
- `/players/:id` a single player with the given ID

It is based on the [Lab 9 tutorial](https://cs.calvin.edu/courses/cs/262/kvlinden/09is/lab.html)
from CS 262 at Calvin University, and adopts its sample [Monopoly](https://github.com/calvin-cs262-organization/monopoly-service)
[service file](https://github.com/calvin-cs262-organization/monopoly-service/blob/master/monopolyService.js).

The database is relational with the schema specified in an `sql/` sub-directory
and is hosted on [ElephantSQL](https://www.elephantsql.com/). The database server,
user and password are stored as Azure application settings so that they aren&rsquo;t 
exposed in this (public) folder.

We implement this sample service as a separate repo to simplify Azure integration;
it&rsquo;s easier to auto-deploy a separate repo to Azure.

Answers to the lab questions:
* What are the (active) URLs for your data service?
  * https://jgc-monopoly-service.azurewebsites.net/
  * https://jgc-monopoly-service.azurewebsites.net/players
  * https://jgc-monopoly-service.azurewebsites.net/players/1
  * https://jgc-monopoly-service.azurewebsites.net/players/2
  * https://jgc-monopoly-service.azurewebsites.net/players/3
* Which of these endpoints implement actions that are idempotent? nullipotent?
  * The "players" endpoints are both idempotent and nullipotent, as is the empty 
  '/' endpoint, for "get." Put and delete are also idempotent.
* Is the service RESTful? If not, why not? If so, what key features make it RESTful.
  * The service is RESTful because it:
    * uses HTTP,
    * does not store client states,
    * has directory-style URIs specified by '/',
    * and conveys information in JSON format.
* Is there any evidence in your implementation of an impedance mismatch?
  * There isn't significant evidence of impedance mismatch, as every Player record
  can be accessed as a JSON object whose attributes correspond to those of the
  tuples that would originally define the Player relation.