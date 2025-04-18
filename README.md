# Hello Java Maven - Jenkins CI/CD Demo

A simple demonstration of Jenkins CI/CD capabilities with a Java Maven project.

## Project Overview

This repository contains a basic Java HelloWorld application that demonstrates continuous integration using Jenkins. The project is built with Maven and outputs a simple "Hello, Jenkins + Maven!" message.

## Project Structure

```
hello-java-maven/
├── pom.xml                      # Maven configuration file
└── src/
    └── main/
        └── java/
            └── HelloWorld.java  # Main Java class
```

## Prerequisites

- Windows operating system
- Docker Desktop for Windows
- Git
- Java JDK 8 or 11
- Maven (for local testing)

## Local Setup

1. Clone this repository:
   ```
   git clone https://github.com/SlayerK15/hello-java-maven.git
   cd hello-java-maven
   ```

2. Build the project locally (optional):
   ```
   mvn clean package
   ```

3. Run the application (optional):
   ```
   java -cp target/hello-1.0.jar HelloWorld
   ```

## Jenkins Setup (Docker)

This project uses Jenkins running in a Docker container instead of a standalone installation.

### Starting Jenkins

1. Start Docker Desktop for Windows

2. Run Jenkins using Docker:
   ```
   docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts
   ```

3. Access Jenkins at http://localhost:8080

4. Retrieve the initial admin password from the Docker logs:
   ```
   docker logs <container-id>
   ```
   Look for the line that contains the initial admin password.

5. Follow the installation wizard to install suggested plugins and create an admin user

### Configuring Maven in Jenkins

1. Go to **Manage Jenkins** > **Global Tool Configuration**
2. Add Maven installation (named "Maven 3.9.9" or similar)
3. Save the configuration

### Creating a Jenkins Job

1. From Jenkins dashboard, click **New Item**
2. Enter "hello-java-maven" as name and select **Freestyle project**
3. Under **Source Code Management**, select **Git** and enter your repository URL
4. Under **Build**, add a step **Invoke top-level Maven targets**
5. Set **Goals** to `clean package`
6. Save and run the job

## Development Notes

- This project was initially created locally and then pushed to GitHub
- The Jenkins instance is running as a Docker container, not as a standalone application
- Maven is used for dependency management and building the project

## Build Artifacts

After a successful build, the following artifacts are generated:

- `target/hello-1.0.jar`: The compiled Java application

## Troubleshooting

### Docker Issues
- Ensure Docker Desktop is running before attempting to start Jenkins
- If port 8080 is already in use, change the port mapping in the Docker run command

### Jenkins Issues
- If Jenkins cannot connect to Git, ensure credentials are properly configured
- For Maven build failures, check the console output for detailed error messages

## License

This project is open source and available under the MIT License.