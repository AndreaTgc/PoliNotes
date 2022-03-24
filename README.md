# Mission Expenses Management

This project allows the management of missions and of the expenses corresponding to them. The registered users (for example usr: user2 pwd: user2pass) can:

* Create Missions
* Add expenses to Missions
* Close missions

### Prerequisites

You need to have a MySQL database, Eclipse and Tomcat configured.

## Getting Started

To have this project up and running in your machine you need to complete the following steps:

1.  Import the database structure and test data from spese.sql to MySQL (MySQL Workbench -> File -> Run SQL script -> Choose spese.sql and execute)
2.  Import project into Eclipse (File -> Import -> Existing project into workspace -> Choose project in your PC)
3.  Change username and password to work with your configuration (WebContent/WEB-INF/web.xml, change dbUser and dbPassword)
4.  Run the project (Run -> Run as... -> Run on Server, choose server configuration and Finish)

## Additional Information

In this project we have introduced some classes that migh not be known for most students in the course

* [Java Enum](https://docs.oracle.com/javase/tutorial/java/javaOO/enum.html) - An enum type is a special data type that enables for a variable to be a set of predefined constants. We used it to define the finite states of a mission (open, reported, closed)


* [Try with resources Statement](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html) - The try-with-resources statement ensures that each resource is closed at the end of the statement. We have used it, in the DAO objects for the PrepareStatement creation and query execution, so we do not need to manually handle the clousure of the resources in the finally block as we do in other examples provided for the course.

* [Transactions](https://docs.oracle.com/javase/tutorial/jdbc/basics/transactions.html) - We use transactions to ensure the DB remains in a consistent state when an operation consist of more than one query (ExpensesReportDAO-->addExpenseReport())


## Authors

* **Piero Fraternali - Federico Milani - Rocio Nahime Torres** 
