# BobApp

Clone project:

> git clone XXXXX

## Front-end 

Go inside folder the front folder:

> cd front

Install dependencies:

> npm install

Launch Front-end:

> npm run start;

### Docker

Build the container:

> docker build -t bobapp-front .  

Start the container:

> docker run -p 8080:8080 --name bobapp-front -d bobapp-front

## Back-end

Go inside folder the back folder:

> cd back

Install dependencies:

> mvn clean install

Launch Back-end:

>  mvn spring-boot:run

Launch the tests:

> mvn clean install

### Docker

Build the container:

> docker build -t bobapp-back .  

Start the container:

> docker run -p 8080:8080 --name bobapp-back -d bobapp-back

### CI/CD

Six GitHub Actions workflows run automatically on push and pull requests to main and dev/* branches:

**Tests back** : Runs Java unit tests and uploads the JaCoCo coverage report.

**Tests front** : Runs Angular unit tests and uploads the Karma/lcov coverage report.

**Sonar analysis back** : Triggered after each tests back workflow succeeds; sends code and coverage to SonarCloud.

**Sonar analysis front** : Triggered after each tests front workflow succeeds; sends code and coverage to SonarCloud.

**Docker deploy back** : Triggered on main after Sonar analysis back succeed; builds and pushes the back Docker image to Docker Hub.

**Docker deploy front** : Triggered on main after Sonar analysis front succeed; builds and pushes the front Docker image to Docker Hub.

Required secrets: DOCKERHUB_USERNAME, DOCKERHUB_TOKEN, SONAR_TOKEN.
