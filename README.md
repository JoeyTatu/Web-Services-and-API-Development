--------------------------- Assignment 1 ---------------------------

Assignment - Creating Web Services
This is an individual assignment, you write your code, others write theirs. Plagiarism will
be referred the disciplinary committee, you have been warned.
Part I
Roman Numeral Converter (50%)
Overview
For this part you must create a Java program to convert a roman numeral to a decimal and
vice-versa.
Example:
Input 1079
Output MLXXIX
Conversion Example
To convert 2012 into roman numerals.
Step 1 Identify the highest number which ts into 2012, X is the remainder after subtracting
the value from 2012 i.e.X=2012-1000
Step 2 You then repeat the procedure with X. Keeping track of the of the numeral corre-
sponding to the biggest number that ts.
Repeat until the number is zero.

Table 1: Roman Numeral Values
1 I
4 IV
5 V
9 IX
10 X
40 XL
50 L
90 XC
100 C
400 CD
500 D
1000 M
Create Web Service
Now you must take the functionality completed in Part I and create a web service which
provides this functionality. In the case of the Roman numeral converter no UI is required,
however you should develop client code for that web service which invokes the GET request
based on user input. Final 20% reserved for bi-directional transformation (from numerals,
and to numerals supported by the API)
Part II
API Proxy (50%)
• Develop an API proxy for acquiring weather data, you will be acting as a proxy server
as dened to be \a server that acts as an intermediary for requests from clients seeking
resources from other servers".
• The user will make a request to your application specifying a city (a GET). Your ap-
pointed method on the server will make a client connection to http://openweathermap.
org/forecast to acquire the data and return it to the client, as such your application
acts as an intermediary. You will need to sign up to acquire an API key.
• The specic URL you will access to get the information should be http://api.openweathermap.
org/data/2.5/forecast?q=[INSERT CITY]&mode=json&appid=[INSERT API ID]
• For this task you can use Jersey HTTP Clients on your server side and client side.

--------------------------- Assignment 2 ---------------------------

Programming Test Re-run 2018
Rules
 READ IT ALL FIRST (you might find it easier to do some questions in parallel)
 You can use the Internet. You need to refer to any code taken from the web (not
necessary for code I have given). Not doing so is plagiarism and will be treated severely.
 No communication between students is allowed.
 You can ask questions, I decide if they are fair in an exam setting.
The What
You are required to create a web service, which provides URL end points for CRUD opera-
tions on Student resources. This is to be done using Jersey.
The scope of this assessment does NOT include databases or persistence, as such you will
NOT actually delete, or save. You will just return appropriate messages as response to
requests. The web service will return ONLY JSON. The web service accepts, where appro-
priate, JSON input. You are required to use GSON explicitly through the code, you will not
use the framework to convert the POJOs to JSON.
The Specifics
1. Create a service to return a list of all the Students (25%)
Create an ArrayList storing five Student instances. When the request for a list of
users is invoked, return this list to the caller in JSON format. The list returned will
be filtered from the full list by an offset i.e. the user supplies a “3” then the returned
list is offset from main list. This should be contained in an annotated method. The
Student class must be defined by yourself; a student should have a name, an age, and
a list of subjects which they are taking. If no offset is provided the full list should be
returned.
2. Create a service to search for Students (20%)
Use the same list as before, if the user(s) specified by their name (this is a query) are
present, return those users in JSON format, otherwise return a sensible HTTP error
code and JSON output. This should be contained in an annotated method. The user
should be retrieved from the ArrayList. The user should be able to search by first
name, surname, and full name.

3. Create a service to update a Student (15%) On the server there should be
a method which updates a Student object from the query parameter input. if the
student was present in the list, then the new object will replace the existing one, if the
student did not exist then the update should fail. Return a sensible response, with the
URL of the resource.
4. Create a service to delete a Student (20%) Examine the input parameter and
return a message indicating that the resource was removed. You will return an affir-
mative message stating that the resource is deleted only if the user is in our ArrayList.
This should all be contained in a properly annotated method.
5. cURL Client (20%)
Provide cURL commands to invoke each of the above defined HTTP requests. These
should be included as comments above each method. I will use these to test your code.

--------------------------- Assignment 3 ---------------------------

BSc (Honours) in Computing - Web Services & API
Development - Project (50% of Module)
This is a group project, if you are not in a group contact the lecturer.
Problem Domain
Online Banking is a mainstream service oered by most banks today. A typical consumer
online banking application requires the following:
A Customer Customers are individuals with a name, correspondence address, email and
security credentials. A customer can hold one or more accounts.
An Account An account has a sort code (identifying the branch), an account number and
a current balance, The account has a list of transactions.
A Transaction Each transaction is either a debit or credit on a particular date, with a
description and post-transaction balance.
Customers will be able to do the following:
Create Customers should be able to create an account with the bank, and a customer
who has an account should be able to add additional accounts. For example a typical
customer may have a current account and a savings account.
Lodgement For the lodgement, a bank customer can specify the amount to lodge with the
credit card that will be debited.
Transfer For the transfer, the bank customer can specify the amount to transfer and an
account to transfer to.
Withdrawal For withdrawal, the bank customer can specify the amount to withdraw and
the card that will be credited.
Balance The customer can request a balance on any account at any time.

Project Requirements
You are required to design, document, and develop, an API for the problem domain above.
The document will have the following sections:
Introduction (5%)
The introduction will expand the problem statement to describe how the API ts together.
For instance:
 Textual description of the problem and the proposed solution. (1 mark)
 An Entity-Relationship diagram describing the problem area, re
ecting your database
structure. (4 Marks)
Introduction is to be approximately 1.5 pages.
The RESTful API (30%)
The API describes all the entry points for the above problem domain. Each entry point (at
least 15 entry points - 2 Marks for each) should be documented under the following headings:
API Name e.g. Users Resource
Description e.g. This allows the retrieval of all user resources
URI e.g. /users
HTTP verb e.g. GET
Parameters e.g. user id (Integer, Required), name (String, Optional), for a POST this
would be a JSON object
Resource contents e.g an example of the returned resource
Pre-Conditions e.g. no record for the user with the specied user id must exist.
Post-Conditions e.g. a new record for the user with the specied user id exists.
The design of the API will be assessed here in terms of its adherence to REST principles,
readability, and the quality of the documentation. The documentation should allow anyone
with knowledge of Web APIs to use your API with no issue. You will receive 0% for this
section if you do not include this documentation despite having implemented it.
Prototype (65%)
The API prototype, must be implemented according to the following requirements:
 An HTML+JavaScript or Mobile or Desktop client calling ALL portions of the API.
E.g., the client should check the account balance allowing a transfer or withdrawal.
(10 Marks)

 A server developed in Java which implements ALL portions of the API using in-memory
objects. Constraints should be implemented, balances should be updated and trans-
actions should be remembered as the API is called. (20 Marks)
 OR A server developed in Java which implements ALL portions of the API using Java
Persistence API (JPA) objects . Constraints should be implemented, balances should
be updated and transactions should be remembered as the API is called. This should
be achieved with a database layer (either memory or disk). (35 Marks)
 A server implementing ALL of the entry points returning resource representations in
XML and JSON. (10 Marks)
 The API must be well secured with access points which are only available to specic
users (by access level, role, and their identity), and protection from web attack vectors
such as SQL injection (10 marks)
You must provide a video (or an accessible link to one) and screen shots to demonstrate
the operation of the Web Service. This should step through the functionality of the project.
There are no specic marks for this but if you don't submit it we will not be in a position
to grade the project.
The prototype source code should also be included with the submission in a ZIP le.