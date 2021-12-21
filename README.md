# How to run SonarQube on docker

## Description
A really cool way to do static analysis of your source code with SonarQube

[![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Sonar](https://img.shields.io/badge/SonarLint-CB2029?style=for-the-badge&logo=sonarlint&logoColor=white)](https://marketplace.visualstudio.com/items?itemName=SonarSource.sonarlint-vscode)

## Running
```bash
docker-compose up
```

## Create Sonar Properties
Create a sonar-project.properties into your project. See the configurations here: https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/

## Running SonarScanner from the Docker image
```bash
docker run \
    --rm \
    -e SONAR_HOST_URL="http://${SONARQUBE_URL}" \
    -e SONAR_LOGIN="myAuthenticationToken" \
    -v "${YOUR_REPO}:/usr/src" \
    sonarsource/sonar-scanner-cli
```

## SonarLint
Use SonarLint to check the consistency of your code even before deploying with sonarqube validation. This helps you verify the source before sonar analysis.

This guarantees the quality of the font based on the rules defined in sonarqube.

To interact your SonarQube project with the rules you have defined just use SonarLint here: https://marketplace.visualstudio.com/items?itemName=SonarSource.sonarlint-vscode

