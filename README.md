## docker-compose-jenkins-sonarqube
> This is environment for CI and QA with docker.


### Assumptions

 - You have Docker and Docker-Compose installed (Docker for Mac, Docker for Windows, get.docker.com and manual Compose installed for Linux).
 - You want to use Docker for local development (i.e. never need to install php or npm on host) and have dev and prod Docker images be as close as possible.
 - You don't want to lose fidelity in your dev workflow. You want a easy environment setup, using local editors, debug/inspect, local code repo, while web server runs in a container.
 - You use `docker-compose` for local development only (docker-compose was never intended to be a production deployment tool anyway).
 - The `docker-compose.yml` is not meant for `docker stack deploy` in Docker Swarm, it's meant for happy local development.


### Getting Started

 - Running `docker-compose up` is all you need. It will:
 - Starts Jenkins at port 8080 and SonarQube at port 9000. SonarQube will saves the data in a PostgreSQL container, exclusively created for this purpose.
 - Requires install Maven, Java and SonarQube Scanner in Jenkins. For enables SonarQube Scanner see https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner+for+Jenkins .
 - For a maven project at Jenkins, in Build options set the following maven goals clean test install $SONAR_MAVEN_GOAL -Dsonar.host.url=http://sonarqube:9000. It will execute the tests and will do a code analysys with SonarQube. After see in SonarQube the result of analisys.
 

