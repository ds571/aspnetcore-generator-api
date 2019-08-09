Access this repository: http://bit.ly/aspnetcoredocker

## Setting up TeamCity Server and Agent and running it

- Getting TeamCity Server and Agent onto local Docker Container
    1) In CMD, cd to ..\api\infra\teamcity
    2) Run the docker-compose.yml file (which automates commands to get it running) with the following command: docker-compose up -d

- Creating a Private Registry
    1) In CMD, cd to ..\api\infra\regisry
    2) Run this command: docker-compose up -d
    3) Test by going to web browser and navigating to "localhost:55000/v2/_catalog". You should see a JSON response
    4) In Powershell running as Admin, type: "notepad C:\Windows\System32\drivers\etc\hosts" and add "127.0.0.1 my-registry" on the last
       line and save. Do not include the quotation marks.
    5) In Docker, go to SETTINGS->DAEMON and add "my-registry:55000" to "Insecure registries" and click "Apply"
    6) Restart Docker
    
- Connecting to Container Hosting TeamCity Server and Agent
    - On a web browser, go to "localhost:8111"

- Setting Up TeamCity
    - Click "Proceed"
    - For "Select the database type" select "Internal (HSQLDB)"
    - Create Username and Password
    - After you login, go to "Unauthorized" tab and click "Unauthorize", then click "Authorize"
  
- Hooking Your Project to TeamCity
    - In 'Projects', click 'Create project'
    - Provide GitHub repository URL
    - provide Username and Password
    - Click 'Proceed'

## Testing Connection to Deployed Container
- Connecting to deployed container:
    1) in CMD, type: docker run --rm -it \<registryName>:\<portNumber>/\<projectName>:tag
        - Example: docker run --rm -it my-registry:55000/gen:ci-12
