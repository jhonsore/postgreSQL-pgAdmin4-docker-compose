# Accessing PgAdmin in browser:
http://localhost:16543

# Access credentials
user: dockerpg@mail.com
password: #PgDocker123

# Adding a new Server
1 - Add new server
2 - In name the name you desire for
3 - Host name/address put container's name, in our case is: postgres-compose
4 - In Port use defaul pg port: 5432
5 - In Username we fill with the default PG user: postgres
6 - In Password put our .yml pass: #PgDocker123

# Connect to Postgres in Docker Container

Code to connect
$ docker exec -it [container_name] psql -U [postgres_user]

- Where container_name is our container name: postgresql-pgadmin4-docker-compose_postgres-compose_1
- postgres_user: postgres

So, we have this:
$ docker exec -it postgresql-pgadmin4-docker-compose_postgres-compose_1 psql -U postgres

Now, let's create a new database:
$ create database teste;

To view all databases run:
$ \l

Connecting to prevvious created database
$ \c teste
You are now connected to database "teste" as user "postgres".
teste=#


Let's create a new table users

CREATE TABLE users (id serial NOT NULL, name VARCHAR(250) NOT NULL, age INTEGER, PRIMARY KEY (id));

Now drop a column
ALTER TABLE users DROP COLUMN age;

Let's add a new column
ALTER TABLE users ADD COLUMN address VARCHAR(250) NOT NULL;

It's time to insert some data
INSERT INTO users (name, address) VALUES ('Umbrella Corporation', '545 S Birdneck RD STE 202B Virginia Beach, VA 23451');
