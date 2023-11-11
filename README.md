# API Deployment Example

## Setup

1. Make sure [Docker](https://www.docker.com/) is installed and running
2. Make sure [sqlx cli](https://crates.io/crates/sqlx-cli) is installed
3. settup postgresql locally with docker: ``docker run -p 5432:5432 --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres````
4. Create a `.env` file. This file will store environment variables. Specifically, `DATABASE_URL` and `POSTGRES_PASSWORD`. It should look like this:
    ```s
    DATABASE_URL=postgres://postgres:mysecretpassword@localhost:5432/postgres
    ```
    `NOTE:` When deploying the API, make sure to change the default PostgreSQL password.
5. To Test the api locally with Cargo: 

   ```shell
   $ cargo run
   ```
   Add a user:
    
   Create a post request to (in postman or an equivalent tool): localhost:3000/user, 
   
   body: 
   ```javascript
   { "name": "Daniel Ahmed",
     "email": "daniel.ahmed@gmail.com" }
   ```
6. Update `docker-compose.yml` and change `nuaip` to your own Docker Hub username. 

## Run Locally with Docker
1. Run an instance of PostgreSQL. This can be done via Docker:
    ```bash
    docker pull postgres
    docker run --name example-db -e POSTGRES_PASSWORD=postgrespw -p 5432:5432 -d postgres
    ```
2. Run SQL migrations:
    ```bash
    sqlx migrate run
    ```
3. Start server:
    ```bash
    cargo run
    ```
4. Test routes. I like to use [Postman](https://www.postman.com/).

## Run Locally using Docker
1. Run API via Docker Compose:
    ```bash
    docker-compose up
    ```
2. Test routes. I like to use [Postman](https://www.postman.com/).