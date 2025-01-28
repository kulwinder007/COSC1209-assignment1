# COSC1209-assignment1
This assignment will cover the creation and deployment of docker containers using dockerfiles and docker compose

COSC 1209 Assignment 1:
Containers
This assignment will cover the creation and deployment of docker containers using dockerfiles and
docker compose. A simple node.js application will be provided to you that you will convert to a
containerized application.
Part 1 (10 marks)
Create a dockerfile with the following specifications, include a screenshot in your submission showing
your file. All commands should be part of your dockerfile.
1. Use the node:19.7.0-alpine base image. (1 mark)
2. Set the environment variable NODE_ENV with a value of production.
3. Create a new directory in root called labone (1 mark)
a. Change the ownership to the node user and node group.
b. Set this new folder as the working directory.
4. Set the user to node. (1 mark)
5. Copy all source files and change the file ownership to the node user and node group. (1 mark)
6. Run the npm install command to install your node.js packages (1 mark)
7. Expose port 3000. (1 mark)
8. Set the default execution command to node src/index.js (1 marks)
Run the docker container using docker compose up --build -d Include a screenshot of your container
running on localhost:3000, add your student ID and your name as items. (3 marks)
You can stop your docker container with the docker compose down command.
Part 2 (15 marks)
Now that you have established a basic containerized application, the next step will be creating a
database that will allow your data to persist when the container restarts.
In the docker compose.yaml file create a new service called db that uses the postgres image. Add the
following configuration to this service, include a screenshot in your submission showing your file.
1. Set the user to postgres (1 mark).
2. Create a volume called db-data and set the path to var/lib/postgresql/data (1 mark)
3. Set the POSTGRES_DB environment variable to labonedb and set the POSTGRES_PASSWORD
variable to your first name followed by your student number. (1 mark)
4. Expose port 5432 (1 mark)
5. Set a health check with an interval of 10 seconds a timeout of five seconds and five retries. For
the test itself use [ "CMD", "pg_isready" ] (2 marks)
Update the server service with the following configuration:
6. Set environment variables for the POSTGRES_HOST, POSTGRES_USER, POSTGRES_PASSWORD,
and POSTGRES_DB. (1 mark)
7. Add a dependency that is conditional on the db server being healthy. (3 marks)
Add a new volume to the compose.yaml file called db-data. (1 mark)
Start your application using docker compose up --build -d. Provide a screenshot showing a list of all
running docker containers. (4 marks)
