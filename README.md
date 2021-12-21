# How to run SonarQube on docker

## Description
A really cool way to do static analysis of your source code with SonarQube

[![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Sonar](https://img.shields.io/badge/SonarLint-CB2029?style=for-the-badge&logo=sonarlint&logoColor=white)](hhttps://www.sonarqube.org/)

## Running
```bash
docker-compose up
```

## Create Sonar Properties
Create a sonar-project.properties into your project. See the configurations here: https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/

# Running SonarScanner from the Docker image
```bash
docker run \
    --rm \
    -e SONAR_HOST_URL="http://${SONARQUBE_URL}" \
    -e SONAR_LOGIN="myAuthenticationToken" \
    -v "${YOUR_REPO}:/usr/src" \
    sonarsource/sonar-scanner-cli
```


