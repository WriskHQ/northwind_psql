# Wrisk test

This repository contains the wrisk take home test. Below you will find how to get 
started and then the question of the test itself.

![Er Diagram](ER.png)

## Getting started:

### Manually

Use the provided sql file `nortwhind.sql` in order to populate your database.

### With Docker and docker compose

#### Pre-requirement: install docker and docker-compose

 https://www.docker.com/get-started

 https://docs.docker.com/compose/install/


#### 1. Run docker-compose

```bash
> docker-compose up

...
... Lots of messages...
...
Creating network "northwind_psql_default" with the default driver
Creating northwind_psql_db_1 ... done
db_1  | 2019-11-28 21:07:14.357 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
db_1  | 2019-11-28 21:07:14.357 UTC [1] LOG:  listening on IPv6 address "::", port 5432
db_1  | 2019-11-28 21:07:14.364 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
db_1  | 2019-11-28 21:07:14.474 UTC [1] LOG:  database system is ready to accept connections
```

#### 2. Run psql client in the docker-compose container

Open another terminal window, and type:

````bash
> docker-compose exec db psql -U northwind_user -d northwind

psql (10.5 (Debian 10.5-1.pgdg90+1))
Type "help" for help.

postgres=# select * from us_states;
 state_id |      state_name      | state_abbr | state_region
----------+----------------------+------------+--------------
        1 | Alabama              | AL         | south
        2 | Alaska               | AK         | north
        ...
````

You can connect to the database from your local machine on port `32770` and the jdbc connection 
string would be `jdbc:postgresql://localhost:32770/northwind`.

#### 3. Stop docker-compose

Stop the server that was launched by `docker compose up` via `Ctrl-C`, then remove the containers via:

```bash
docker-compose down
```

Your modifications will be persisted in the `dabata/` local folder, and can be retrieved
once you restart `docker compose up`.

## The test

Please provide the code, queries and output to the following.

### Introduction

* When was the first order placed?
* Which customers have placed over 10 orders?

### Reporting

* Produce a report that, for each customer, calculates the total discounted price of all their 
orders along with the total percentage discount they received
* Produce a report that shows the number of orders along with the total value of orders for the customer
with id 'SAVEA'. This report should include every month between 1996-01-01 and 1998-12-01.
If they have not placed an order in any of the months then the number of orders and total value of orders should be 0.
* Using a window function, produce a report that shows the id of each order placed, 
the customer id for that order along with the last order id that the customer placed

### Analysis

* Is there any relationship between the region served by
employees and the categories of products which they sell (by volume)?
* What is the median average delay between order date and shipped date by shipping company?
* Try to determine the factors that best explain the sales performance of employees as assessed by sales income

