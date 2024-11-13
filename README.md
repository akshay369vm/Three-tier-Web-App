# Three-Tier-Web-App

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-production-user-asset-6210df.s3.amazonaws.com/658727/272340510-34957be5-7318-4473-8141-2751ca571c4f.png">
    <source media="(prefers-color-scheme: light)" srcset="https://github-production-user-asset-6210df.s3.amazonaws.com/658727/272340472-ad8d7a46-ef85-47ea-9129-d815206ed2f6.png">
    <img alt="Garden" src="https://github-production-user-asset-6210df.s3.amazonaws.com/658727/272340472-ad8d7a46-ef85-47ea-9129-d815206ed2f6.png">
  </picture>
</p>


The project is a voting application with the following components:

- `web` — A frontend Vue application
  --
  - Use `node version 10` to build and test the app.
  - Run `npm install` to download all the node modules.
  - Run `npm run serve` to start the application.
  - Run `npm run test:unit` to run the unit test cases.
  - Run `npm run test:integ` to run the integration test.
- `api` — A Python API server
  --
  - Use `python:3.10` to run the api service.
  - Add the packages using the command
    `apk add --no-cache entr postgresql-dev musl-dev gcc`
  - Install the requirement using pip package manager.
  - Make port 80 available for links and/or publish
  - Define our command to be run when launching the container
     `gunicorn app:app -b 0.0.0.0:8080 --log-file - --access-logfile - --workers 4 --keep-alive 0`
  - Add the below environment variables for kubernetes deployment
    - `PGDATABASE: postgres`
    - `PGUSER: postgres`
    - `PGPASSWORD: postgres`
  - Run python integration test using `python3 test.py`
- `db` — A Postgres database
  --
  - Create the database using `postgres:12.4-alpine`.
  - Create the table using the command
    `CREATE TABLE IF NOT EXISTS votes (id VARCHAR(255) NOT NULL UNIQUE, vote VARCHAR(255) NOT NULL, created_at timestamp default NULL)`
  - Add the below environment variables for kubernetes deployment
    - `PGDATABASE: postgres`
    - `PGUSER: postgres`
    - `PGPASSWORD: postgres`
    
