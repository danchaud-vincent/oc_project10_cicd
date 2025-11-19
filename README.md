# BobApp

## :notebook: Project Description

BobApp is a fun little application that tells a random joke every time you click the button. It’s designed to provide a simple and entertaining experience for users while demonstrating modern development and CI/CD practices. 

### 1. Projet goals 

This project was designed to:
- Set up GitHub Actions pipelines for both frontend and backend.
- Automatically build and test the code on each commit.
- Generate test coverage reports to monitor code quality.
- Analyze the code with SonarCloud to detect bugs, vulnerabilities, and maintainability issues.
- Build and publish Docker images for the frontend and backend to Docker Hub.

This project demonstrates a complete continuous integration and delivery (CI/CD) workflow for a simple but fully functional application.

### 2. Prerequisites: 

The backend is built with **Spring Boot**(version 2.6.1) and the frontend is developed using **Angular**(version 14.2.0).

- [Angular CLI](https://github.com/angular/angular-cli) version 14
- [Java](https://www.oracle.com/java/technologies/javase/jdk11-archive-downloads.html) version 11
- [Maven](https://maven.apache.org/)
- [Node.js](https://nodejs.org/en)
- [Docker](https://www.docker.com/)

## SonarCloud Analysis

### Frontend

| Metric | Status |
|--------|--------|
| Quality Gate | [![Frontend Quality Gate](https://sonarcloud.io/api/project_badges/measure?project=danchaud-vincent_bobapp-frontend&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=danchaud-vincent_bobapp-frontend&branch=main) |
| Coverage | [![Frontend Coverage](https://sonarcloud.io/api/project_badges/measure?project=danchaud-vincent_bobapp-frontend&metric=coverage)](https://sonarcloud.io/component_measures?id=danchaud-vincent_bobapp-frontend&metric=coverage&view=list) |
| Bugs | [![Frontend Bugs](https://sonarcloud.io/api/project_badges/measure?project=danchaud-vincent_bobapp-frontend&metric=bugs)](https://sonarcloud.io/component_measures?metric=new_bugs&view=list&id=danchaud-vincent_bobapp-frontend) |
| Vulnerabilities | [![Frontend Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=danchaud-vincent_bobapp-frontend&metric=vulnerabilities)](https://sonarcloud.io/component_measures?metric=new_vulnerabilities&view=list&id=danchaud-vincent_bobapp-frontend) |
| Code Smells | [![Frontend Code Smells](https://sonarcloud.io/api/project_badges/measure?project=danchaud-vincent_bobapp-frontend&metric=code_smells)](https://sonarcloud.io/component_measures?metric=code_smells&view=list&id=danchaud-vincent_bobapp-frontend) |

### Backend

| Metric | Status |
|--------|--------|
| Quality Gate | [![Backend Quality Gate](https://sonarcloud.io/api/project_badges/measure?project=danchaud-vincent_bobapp-backend&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=danchaud-vincent_bobapp-backend&branch=main) |
| Coverage | [![Backend Coverage](https://sonarcloud.io/api/project_badges/measure?project=danchaud-vincent_bobapp-backend&metric=coverage)](https://sonarcloud.io/component_measures?id=danchaud-vincent_bobapp-backend&metric=coverage&view=list) |
| Bugs | [![Backend Bugs](https://sonarcloud.io/api/project_badges/measure?project=danchaud-vincent_bobapp-backend&metric=bugs)](https://sonarcloud.io/component_measures?metric=Reliability&view=list&id=danchaud-vincent_bobapp-backend) |
| Vulnerabilities | [![Backend Vulnerabilities](https://sonarcloud.io/api/project_badges/measure?project=danchaud-vincent_bobapp-backend&metric=vulnerabilities)](https://sonarcloud.io/component_measures?metric=Reliability&view=list&id=danchaud-vincent_bobapp-backend) |
| Code Smells | [![Backend Code Smells](https://sonarcloud.io/api/project_badges/measure?project=danchaud-vincent_bobapp-backend&metric=code_smells)](https://sonarcloud.io/component_measures?metric=code_smells&selected=danchaud-vincent_bobapp-backend%3Asrc%2Fmain%2Fjava%2Fcom%2Fopenclassrooms%2Fbobapp%2Fmodel%2FJoke.java&view=list&id=danchaud-vincent_bobapp-backend) |

## :screwdriver: Setup locally :

### 1. Clone the repository :

```bash
git clone https://github.com/danchaud-vincent/oc_project10_cicd
```

### 2. Frontend :

#### a. Before running the frontend

To use the app, make sure that the backend server is started before starting the frontend.

#### b. Go inside the front folder (from the project root)

```bash
cd front
```

#### c. Install dependencies

```bash
npm install
```

#### d. To start a local development server, run:

```bash
npm run start
```

or

```bash
ng serve --open
```

Once the server is running, open your browser and navigate to `http://localhost:4200/`. The application will automatically reload whenever you modify any of the source files.

#### e. To build the front:

To build the project run:

```bash
ng build
```

This will compile your project and store the build artifacts in the `dist/` directory. By default, the production build optimizes your application for performance and speed.

#### f. Run the tests:

```bash
npm run test
```

or with code coverage:

```bash
npm run test -- --code-coverage
```

> You can find the coverage reports in `front/coverage/bobapp` (index.html file).

### 3. Back-end

#### a. Go inside the back folder (from the project root)

```bash
cd back
```

#### b. Install dependencies:

```bash
mvn clean install
```

#### c. Launch Back-end:

```bash
mvn spring-boot:run
```

#### d. Run the tests:

```bash
mvn clean test
```

or :

```bash
maven clean verify
```

> You can find the jacoco coverage reports in `back/target/site`.

## :whale2: Docker: Build and run with docker

### Build and run the application with docker-compose

```bash
docker-compose up --build
```

or

```bash
docker compose up --build -d
```

### Build and run with docker network

#### a. Build Frontend container

```bash
docker build -t bobapp-front .
```

#### b. Build Backend container

```bash
docker build -t bobapp-back .
```

#### c. create a network

```bash
docker network create bobapp-network
```

#### d. Run the backend and frontend in the network

Start the backend container:

```bash
docker run -d -p 8080:8080 --name backend --network bobapp-network bobapp-back
```

Start the frontend container:

```bash
docker run -d -p 80:80 --name frontend --network bobapp-network bobapp-front
```

## :black_nib: Author :

**Danchaud Vincent**

