# nginx-php-postgres-alpine
Docker compose to run nginx, php, postgres and alpine stack for developement purpose.

A very light weight docker compose file with minimal requirement for running php app, nginx, postgres on alpine base for development purpose and not production. And please note that it is not intended for complex program but just a simple starter to boot up your php project on docker containers, however you can try (by adding or changing the configurations). You can use this compose to work on any number of projects at the same time considering you will have different project name and ports.

You can add or change the contents in files as per your requirements :)

## Simple steps:

1. First clone the repo:

  `git clone https://github.com/roxcity/nginx-php-postgres-alpine.git`

2. Go to nginx-php-postgres-alpine or this repo folder.

3. Rename or copy the env.sample file to .env.

4. Add environment variables in .env file:

  **Example:**
  ```
    INDEX_FOLDER_PATH=public
    PROJECT_NAME=myproject
    PROJECT_PATH=/home/../myapp
    WEB_PORT=80
    DB_PORT=5432
    POSTGRES_USER=
    POSTGRES_PASSWORD=
    PGDATA=/dbdata
    POSTGRES_DB=new_database
    DB_VOLUME=db_volume
  ```
  >If you want to know about the POSTGRES environment variables then docs is available here: 

  >https://github.com/docker-library/docs/tree/master/postgres#environment-variables

  >If you leave POSTGRES_USER and POSTGRES_PASSWORD values blank then default user of username "postgres" will created with no password. It will be easy for development purpose to leave those two blank. :)

5. Then run

   >You need to create a volume for persistant data for database. If you have created a named volume then you can skip below command. So, only for the first time, you need to run this command:

  `docker volume create --name <DB_VOLUME(from .env file)>`

   >After you have created a volume, run below command:

  `docker-compose up -d`

  >-d runs your container in a detached mode.

6. Then open your 

  `http://localhost:WEB_PORT`

Hurray! You will see your index page considering all your library are installed and everything went okay. :D

- To stop your containers, run below command from the same folder:

  `docker-compose stop`

- To stop and remove your containers & networks, run below command from the same folder:

  `docker-compose down`

- To start your stopped containers, run below command from the same folder:

  `docker-compose start`

**Note:** Your project files must be in the project path declared in .env file or you can add you files there later (after completing the steps). In an example above my index.php file is inside public which is inside myapp folder. If your index.php file is in another directory, you need to give full path from the project root directory (in above case the root directory is myapp).
