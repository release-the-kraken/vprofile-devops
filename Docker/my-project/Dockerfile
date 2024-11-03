# Use a multi-stage build to keep the final image small
# Stage 1: Build the application
FROM maven:3.8.5-openjdk-17-slim AS BUILD_IMAGE

# Set the working directory inside the container
WORKDIR /app

# Define the Git repository and branch directly in the Dockerfile
# Change these to your repository and branch
ARG GIT_REPO=https://github.com/release-the-kraken/kanye-test.git
ARG GIT_BRANCH=main

# Install git, clone the repository, and build the project
RUN apt-get update && apt-get install -y git && \
    git clone -b ${GIT_BRANCH} ${GIT_REPO} . && \
    mvn clean package -DskipTests

# Stage 2: Run the application
FROM openjdk:17-jdk-slim

# Set the working directory
WORKDIR /app

# Copy the jar file from the builder stage
COPY --from=BUILD_IMAGE /app/target/*.jar app.jar

# Expose the application port
EXPOSE 8080

# Set the entry point
ENTRYPOINT ["java", "-jar", "app.jar"]