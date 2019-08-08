Access this repository: http://bit.ly/aspnetcoredocker

## Setting up TeamCity Server and Agent and running it

- Getting TeamCity Server and Agent onto local Docker Container
1) In CMD, cd to ..\api\infra\teamcity
2) Run the docker-compose.yml file (which automates commands to get it running) with the following command: docker-compose up -d

- Connecting to Container Hosting TeamCity Server and Agent
    - On a web browser, go to "localhost:8111"

- Setting Up TeamCity
    - Click "Proceed"
    - For "Select the database type" select "Internal (HSQLDB)"
    - Create Username and Password
    - After you login, go to "Unauthorized" tab and click "Unauthorize", then click "Authorize"
