## Programing Languages
Is set of instruction/commands which have their own syntax that when given to computer gives desired output.

## Some known programing languages
* Javascript
* Python 
* Java
* Kotlin
* C
* C++
* C#
* PHP
* Ruby
* Dart
* Go 
* COBOL

* JavaScript can be used in front end as well as back end.
    * JavaScript front end framework: React JS,Vue JS, Angular JS etc.
    * JavaScript back end framework: Next JS,Express etc.

## IP Address(is like building)

* IP(Internet Protocal) address - unique address that each device has that identifies that is used to identify that device on internet or local network.
* Any we application cannot work without IP address.

* IPv4 and IPv6 created by IANA(Internet Assigned Number Authority)standards organization that is incharge of  global IP address allocation.

* IPv4(32 bit) - limitations of the IP.
Therefore IPv6 was introduced.

* IP can be public(which everyone can access from which application is be powered) and private(used within organization).

## IPv4 Classes

* Class A : 0-127(reserved for local system
  * (0.0.0.0 - 127.255.255.255)
  * Any IP that starts with 127 means that it assigned to local system.
  * 10 - 10.255 local network IP 
* Class B : 128-191 - used for internet
* Class C : 192-223 - (192.168 local network IP(used within a network))
* Class D : 224-239 (not used/reserved)
* Class E : 240-255 (not used)


## Port (is like house)

 * door/point through which application communicate.
 * Range 0 - 65535
 * 0 - 1023( no other application can use this port, port used only by system).
 * 1024 - 49150 (3000 - 9999 mostly used for web application).
 * 49151 - 65535 - are open port(system uses this ports to connect to other application).
 
### Web Port :

Any web application that we run on server uses this ports 80 : for HTTP  and 443 : for HTTPS(secure all production application runs on this port)

Browser internally converts Domain name(name for an IP address) to IP address.

## Postman
for backend development , api development , test api

## Code editor
 * VSCode
 * sublime
 * Notepad ++

## Web Server
where web application get hosted
* local development : xampp etc
* production : Nginx etc.

## HTTP Verbs

* GET : to get data
* POST : to send data 
* PUT : to update data
* DELETE : to delete 
* OPTION and HEAD : for quering  

## HTTP Headers

* Any request that comes from server has header, are like defination which browser is sending or any application is sending to server and based on values in header server may decide to do something.

## HTTP Status Code

* 100 - 199 : Information Responses
   * 100 - continue
* 200-299 : Success resonse
  * 200 - ok
  * 202 - accepted
* 300 -399 - Used for redirecting/migration.
   * 302 - not found
* 400 -499 : client side error(user error)
   * 403 - forbidden
   * 404 - not found 
   * 408 - request timeout
* 500 series - Server error (send by server)
   * 500 - server internal error
   * 503 - if server is down, sever unavailable.


## Software License
most company use open sorce license which gives freedom to company therefore there are open sorce application.
* BSD
* Apache 2.0 
* MIT 
In all of above licensing the you can modify it and you don't have to share the development.
* GPL (used by linux, have to share the code if you modify it i.e make it available to everyone)



## Database
* Relational Database : Have tables which holds data. 
   * MySQL
   * postgreSQL
   * MariaBD
* Non Relational Database : Stores data in document or as graph.
   * MongoDB
   * Redis
   * NeoJS

## Cloud Providers

Helps to maintain application.Provides cloud services like IAAS, PAAS, SAAS.

* Digital Ocean
* Vultr
* AWS (Enterprise)
* Google Cloud (Enterprise)
* Azure (Enterprise)



## Code Repository

Act as tool for collabration 
* Github
* GitLab - open sorce
* Bitbucket

## Project Management Tool
* JIRA- used by big company (Task,Stories)

* Small company uses following :
  * Google Sheet
  * DOC
  * Trello
  * Asana

## Dev Workflow
* Git Dev Workflow
   * feature branch
   * develop branch
   * stage branch
   * master branch(Deploy to production)


## Infrastructure
  Flow that can be followed.

    1. Dev
    only DevOps have access to follow
    2. UAT(user acceptance test)/Staging
    3. Production System
