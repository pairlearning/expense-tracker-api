# expense-tracker-api

REST API for tracking expenses.

A RESTful API created using Spring Boot. We have used PostgreSQL as the relational database and JdbcTemplate to interact with that.
Apart from this, we have used JSON Web Token (JWT) to add authentication. Using JWT, we can protect certain endpoints and ensure that user must be logged-in to access those.

Here are all the videos where we have created this API from scratch - [Youtube Playlist](https://www.youtube.com/playlist?list=PLWieu6NbbqTwwYwylgXmmKVX1ZWsUVx8m)

## Setup and Installation

1. **Clone the repo from GitHub**
   ```sh
   git clone https://github.com/pairlearning/expense-tracker-api.git
   cd expense-tracker-api
   ```
2. **Spin-up PostgreSQL database instance**

   You can use either of the below 2 options:
   - one way is to download from [here](https://www.postgresql.org/download) and install locally on the machine
   - another option is by running a postgres docker container:
     ```sh
     docker container run --name postgresdb -e POSTGRES_PASSWORD=admin -d -p 5432:5432 postgres
     ```
3. **Create database objects**

   In the root application directory (expense-tracker-api), SQL script file (expensetracker_db.sql) is present for creating all database objects
   - if using docker (else skip this step), first copy this file to the running container using below command and then exec into the running container:
     ```
     docker container cp expensetracker_db.sql postgresdb:/
     docker container exec -it postgresdb bash
     ```
   - run the script using psql client:
     ```
     psql -U postgres --file expensetracker_db.sql
     ```
4. **(Optional) Update database configurations in application.properties**
   
   If your database is hosted at some cloud platform or if you have modified the SQL script file with some different username and password, update the src/main/resources/application.properties file accordingly:
   ```properties
   spring.datasource.url=jdbc:postgresql://localhost:5432/expensetrackerdb
   spring.datasource.username=expensetracker
   spring.datasource.password=password
   ```
5. **Run the spring boot application**
   ```sh
   ./mvnw spring-boot:run
   ```
   this runs at port 8080 and hence all enpoints can be accessed starting from http://localhost:8080
